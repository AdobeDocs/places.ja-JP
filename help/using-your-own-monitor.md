---
title: 独自のモニタの使用
description: また、Places Service 拡張機能 API を使用すると、監視サービスを使用したり、Places Service と統合したりすることもできます。
exl-id: 8ca4d19b-0f23-4291-b335-af47f03179fa
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 1%

---

# 独自のモニタの使用 {#using-your-monitor}

また、Places 拡張機能 API を使用すると、監視サービスを使用し、Places Service と統合することもできます。

## ジオフェンスの登録

監視サービスを使用する場合は、次の手順を実行して、現在の場所に関する POI のジオフェンスを登録します。

### iOS

iOSで、以下の手順を実行します。

1. iOSのコア場所サービスから取得した場所の更新を Places 拡張機能に渡します。

1. `getNearbyPointsOfInterest` Places 拡張機能 API を使用して、現在の場所の周囲にある `ACPPlacesPoi` オブジェクトの配列を取得します。

   ```objective-c
   - (void) locationManager: (CLLocationManager*) manager didUpdateLocations: (NSArray<CLLocation*>*) locations {
       [ACPPlaces getNearbyPointsOfInterest:currentLocation limit:10 callback: ^ (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi) {
           [self startMonitoringGeoFences:nearbyPoi];
       }];
   }
   ```

1. 取得した `ACPPlacesPOI` オブジェクトから情報を抽出し、それらの POI の監視を開始します。

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

1. Google Play サービスまたはAndroidの場所サービスから取得した場所の更新を Places Extension に渡します。

1. `getNearbyPointsOfInterest` Places Extension API を使用して、現在の場所の周りの `PlacesPoi` オブジェクトのリストを取得します。

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

1. 取得した `PlacesPOI` オブジェクトからデータを抽出し、それらの POI の監視を開始します。

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


`getNearbyPointsOfInterest` API を呼び出すと、現在の場所の周囲の場所を取得するネットワーク呼び出しが発生します。

>[!IMPORTANT]
>
>API の呼び出しは慎重に行うか、ユーザーの場所が大きく変更された場合にのみ行うようにしてください。

## ジオフェンスイベントの投稿

### iOS

iOSで、`CLLocationManager` デリゲートの `processGeofenceEvent` Places API を呼び出します。 この API は、ユーザーが特定のリージョンにエントリまたは離脱したかどうかを通知します。

```objective-c
- (void) locationManager:(CLLocationManager *)manager didEnterRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeEntry];
}

- (void) locationManager:(CLLocationManager *)manager didExitRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeExit];
}
```

### Android

Androidでは、`processGeofence` メソッドを、ジオフェンス放送受信機の適切なトランジションイベントと共に呼び出します。 受信したジオフェンスのリストをキュレートして、エントリや離脱の重複を防ぐことができます。

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
