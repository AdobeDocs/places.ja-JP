---
title: 独自のモニタを使用する
description: また、Places Service 拡張 API を使用して、監視サービスを使用し、Places Service と統合することもできます。
exl-id: 8ca4d19b-0f23-4291-b335-af47f03179fa
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 1%

---

# 独自のモニタを使用する {#using-your-monitor}

また、Places 拡張機能 API を使用して、監視サービスを使用し、Places Service と統合することもできます。

## ジオフェンスの登録

監視サービスを使用する場合は、次の手順を実行して、現在の場所に関する POI のジオフェンスを登録します。

### iOS

iOSで、次の手順を実行します。

1. iOSの Core ロケーションサービスから取得したロケーションの更新を Places 拡張機能に渡します。

1. 以下を使用： `getNearbyPointsOfInterest` Places 拡張機能 API を使用しての配列を取得する `ACPPlacesPoi` 現在の位置の周囲のオブジェクト。

   ```objective-c
   - (void) locationManager: (CLLocationManager*) manager didUpdateLocations: (NSArray<CLLocation*>*) locations {
       [ACPPlaces getNearbyPointsOfInterest:currentLocation limit:10 callback: ^ (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi) {
           [self startMonitoringGeoFences:nearbyPoi];
       }];
   }
   ```

1. 取得したから情報を抽出します。 `ACPPlacesPOI` オブジェクトを参照し、これらの POI の監視を開始します。

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

1. Google Playサービスまたは Android ロケーションサービスから取得したロケーションの更新を Places 拡張機能に渡します。

1. 以下を使用： `getNearbyPointsOfInterest` Places 拡張機能 API を使用してのリストを取得 `PlacesPoi` 現在の位置の周囲のオブジェクト。

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

1. 取得したからデータを抽出します `PlacesPOI` オブジェクトを参照し、これらの POI の監視を開始します。

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


の呼び出し `getNearbyPointsOfInterest` API を実行すると、現在の場所の周囲の場所を取得するネットワーク呼び出しが実行されます。

>[!IMPORTANT]
>
>API は、慎重に、またはユーザーの大きな場所の変更がある場合にのみ呼び出す必要があります。

## ジオフェンスイベントの投稿

### iOS

iOSで、 `processGeofenceEvent` Places API を `CLLocationManager` デリゲート。 この API は、ユーザーが特定の地域に入ったか出たかを通知します。

```objective-c
- (void) locationManager:(CLLocationManager *)manager didEnterRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeEntry];
}

- (void) locationManager:(CLLocationManager *)manager didExitRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeExit];
}
```

### Android

Android で、 `processGeofence` メソッドと、ジオフェンスブロードキャストレシーバーの適切なトランジションイベントを組み合わせて使用します。 入口や出口の重複を防ぐために、受け取ったジオフェンスのリストをキュレーションする必要がある場合があります。

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
