---
title: 自分のモニターを使用する
description: また、Places サービス拡張機能APIを使用して、監視サービスを使用したり、Places サービスと統合したりすることもできます。
exl-id: 8ca4d19b-0f23-4291-b335-af47f03179fa
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: d8704da9c84a066f72471421290d4b46c65f41e1
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 1%
---
# 自分のモニターを使用する {#using-your-monitor}

また、Places拡張機能APIを使用して、監視サービスを使用したり、Places サービスと統合したりすることもできます。

## ジオフェンスの登録

モニタリングサービスを使用する場合は、次の手順を実行して、現在の場所のPOIのジオフェンスを登録します。

### iOS

IOSで、次の手順を実行します。

1. IOSのコアロケーションサービスから取得した位置情報の更新をPlaces拡張機能に渡します。

1. `getNearbyPointsOfInterest` Places拡張機能APIを使用して、現在の場所の周囲にある`ACPPlacesPoi` オブジェクトの配列を取得します。

   ```objective-c
   - (void) locationManager: (CLLocationManager*) manager didUpdateLocations: (NSArray<CLLocation*>*) locations {
       [ACPPlaces getNearbyPointsOfInterest:currentLocation limit:10 callback: ^ (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi) {
           [self startMonitoringGeoFences:nearbyPoi];
       }];
   }
   ```

1. 取得した`ACPPlacesPOI` オブジェクトから情報を抽出し、それらのPOIの監視を開始します。

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

1. Google Play サービスまたはAndroid location サービスから取得した位置情報の更新をPlaces拡張機能に渡します。

1. `getNearbyPointsOfInterest` Places Extension APIを使用して、現在の場所の周囲にある`PlacesPoi` オブジェクトのリストを取得します。

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

1. 取得した`PlacesPOI` オブジェクトからデータを抽出し、それらのPOIの監視を開始します。

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


`getNearbyPointsOfInterest` APIを呼び出すと、現在の場所の周りの場所を取得するネットワーク呼び出しが発生します。

>[!IMPORTANT]
>
>APIの呼び出しは控えめにするか、ユーザーの場所が大幅に変更された場合にのみ行う必要があります。

## Geofence イベントの投稿

### iOS

IOSで、`CLLocationManager` デリゲートで`processGeofenceEvent` Places APIを呼び出します。 このAPIは、ユーザーが特定の地域にエントリしたか離脱したかを通知します。

```objective-c
- (void) locationManager:(CLLocationManager *)manager didEnterRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeEntry];
}

- (void) locationManager:(CLLocationManager *)manager didExitRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeExit];
}
```

### Android

Androidで、Geofence ブロードキャスト受信機で適切なトランジションイベントとともに`processGeofence` メソッドを呼び出します。 受信したジオフェンスのリストをキュレートして、エントリ/離脱が重複しないようにすることができます。

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
