---
title: 独自のモニタを使用する
description: また、Places Service Extension APIを使用して、監視サービスを使用し、Places Serviceと統合することもできます。
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b

---


# 独自のモニタを使用する {#using-your-monitor}

また、監視サービスを使用し、Places拡張APIを使用してPlaces Serviceと統合することもできます。

## ジオフェンスの登録

監視サービスを使用する場合は、次の手順を実行して、現在の場所周辺のPOIのジオフェンスを登録します。

### iOS

iOSで、次の手順を実行します。

1. iOSのコアロケーションサービスから取得した場所の更新をPlaces拡張に渡します。

1. Places拡張APIを `getNearbyPointsOfInterest` 使用して、現在の場所の周囲にあるオブジ `ACPPlacesPoi` ェクトの配列を取得します。

   ```objective-c
   - (void) locationManager: (CLLocationManager*) manager didUpdateLocations: (NSArray<CLLocation*>*) locations {
       [ACPPlaces getNearbyPointsOfInterest:currentLocation limit:10 callback: ^ (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi) {
           [self startMonitoringGeoFences:nearbyPoi];
       }];
   }
   ```

1. 取得したオブジェクトから情報を抽 `ACPPlacesPOI` 出し、それらのPOIの監視を開始します。

   ```objective-c
   - (void) startMonitoringGeoFences: (NSArray*) newGeoFences {
       // verify if the device supports monitoring geofences
       // check for location permission
   
       for (ACPPlacesPoi * currentRegion in newGeoFences) {
           // make the circular region
           CLLocationCoordinate2D center = CLLocationCoordinate2DMake(currentRegion.latitude, currentRegion.longitude);
           CLCircularRegion* currentCLRegion = [[CLCircularRegion alloc] initWithCenter:center
                                                                                 radius:currentRegion.radius
                                                                             identifier:currentRegion.identifier];
           currentCLRegion.notifyOnExit = YES;
           currentCLRegion.notifyOnEntry = YES;
   
           // start monitoring the new region
           [_locationManager startMonitoringForRegion:currentCLRegion];
       }
   }
   ```

### Android

1. Google playサービスまたはAndroidロケーションサービスから取得した場所の更新をPlaces Extensionに渡します。

1. Places Extension APIを使 `getNearbyPointsOfInterest` 用して、現在の場所周辺のオブジ `PlacesPoi` ェクトのリストを取得します。

   ```java
   LocationCallback callback = new LocationCallback() {
       @Override
       public void onLocationResult(LocationResult locationResult) {
           super.onLocationResult(locationResult);
   
           Places.getNearbyPointsOfInterest(currentLocation, 10, new AdobeCallback<List<PlacesPOI>>() {
               @Override
               public void call(List<PlacesPOI> pois) {
                   starMonitoringGeofence(pois);
               }
           });
       }
   };
   ```

1. 取得したオブジェクトからデータを抽 `PlacesPOI` 出し、POIの監視を開始します。

   ```java
   private void startMonitoringFences(final List<PlacesPOI> nearByPOIs) {
       // check for location permission
       for (PlacesPOI poi : nearByPOIs) {
           final Geofence fence = new Geofence.Builder()
               .setRequestId(poi.getIdentifier())
               .setCircularRegion(poi.getLatitude(), poi.getLongitude(), poi.getRadius())
               .setExpirationDuration(Geofence.NEVER_EXPIRE)
               .setTransitionTypes(Geofence.GEOFENCE_TRANSITION_ENTER |
                                   Geofence.GEOFENCE_TRANSITION_EXIT)
               .build();
           geofences.add(fence);
       }
   
       GeofencingRequest.Builder builder = new GeofencingRequest.Builder();
       builder.setInitialTrigger(GeofencingRequest.INITIAL_TRIGGER_ENTER);
       builder.addGeofences(geofences);
       builder.build();
       geofencingClient.addGeofences(builder.build(), geoFencePendingIntent)
   }
   ```


この `getNearbyPointsOfInterest` APIを呼び出すと、現在の場所の周りの場所を取得するネットワーク呼び出しが発生します。

>[!IMPORTANT]
>
>APIは、個別に呼び出すか、ユーザーの場所が大幅に変更された場合にのみ呼び出す必要があります。

## ジオフェンスイベントの投稿

### iOS

iOSでは、Places APIをデリゲ `processGeofenceEvent` ートで呼び出し `CLLocationManager` ます。 このAPIは、ユーザーが特定の地域に入ったか出たかを通知します。

```objective-c
- (void) locationManager:(CLLocationManager *)manager didEnterRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeEntry];
}

- (void) locationManager:(CLLocationManager *)manager didExitRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeExit];
}
```

### Android

Androidで、Geofenceブロードキャスト受信 `processGeofence` 機の適切なトランジションイベントと共にメソッドを呼び出します。 入口/出口の重複を防ぐために、受け取ったジオフェンスのリストをキュレーションする必要がある場合があります。

```java
void onGeofenceReceived(final Intent intent) {
    // do appropriate validation steps for the intent
    ...

    // get GeofencingEvent from intent
    GeofencingEvent geoEvent = GeofencingEvent.fromIntent(intent);

    // get the transition type (entry or exit)
    int transitionType = geoEvent.getGeofenceTransition();

    // validate your geoEvent and get the necessary Geofences from the list
    List<Geofence> myGeofences = geoEvent.getTriggeringGeofences();

    // process region events for your geofences
    for (Geofence geofence : myGeofences) {
        Places.processGeofence(geofence, transitionType);
    }
}
```
