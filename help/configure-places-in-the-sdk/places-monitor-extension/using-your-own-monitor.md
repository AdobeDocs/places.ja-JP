---
title: 独自のモニタを使用する
seo-title: 独自のモニタを使用する
description: 'また、Places拡張APIを使用して、監視サービスを使用し、Placesと統合することもできます。 '
seo-description: 'また、Places拡張APIを使用して、監視サービスを使用し、Placesと統合することもできます。 '
translation-type: tm+mt
source-git-commit: ef3d77eba407013e1f701ed001ef9ab7b3818e07

---


# 独自のモニタを使用する {#using-your-monitor}

また、Places拡張APIを使用して、監視サービスを使用し、Placesと統合することもできます。

## ジオフェンスの登録

監視サービスを使用する場合は、次の手順を実行して、現在の場所周辺のPOIのジオフェンスを登録します。

### iOS

iOSで、次の手順を実行します。

1. iOSのコアロケーションサービスから取得した場所の更新をPlaces拡張に渡します。

2. Places拡張APIを `getNearbyPointsOfInterest` 使用して、現在の場所周辺の *n*`ACPPlacesPoi` 個のオブジェクトの配列を取得します。

   ```objective-c
   - (void) locationManager: (CLLocationManager*) manager didUpdateLocations: (NSArray<CLLocation*>*) locations {
   
          [ACPPlaces getNearbyPointsOfInterest:currentLocation limit:10 callback: ^ (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi) {
              [self startMonitoringGeoFences:nearbyPoi];
      }];
   
   }
   ```

3. 取得したオブジェクトから情報を抽 `ACPPlacesPOI` 出し、それらのPOIの監視を開始します。

   ```objective-c
   - (void) startMonitoringGeoFences: (NSArray*) newGeoFences {
       // verify if the device supports monitoring geofences
       // check for location permission
   
       for (ACPPlacesPoi * currentRegion in newGeoFences) {
           // make the circular region
           CLLocationCoordinate2D center = CLLocationCoordinate2DMake(currentRegion.latitude, currentRegion.longitude);
           CLCircularRegion* currentCLRegion = [[CLCircularRegion alloc] initWithCenter:center                                                                                                                              radius:currentRegion.radius                                                                                                                    identifier:currentRegion.identifier];
           currentCLRegion.notifyOnExit = YES;
           currentCLRegion.notifyOnEntry = YES;
   
           // start monitoring the new region
           [_locationManager startMonitoringForRegion:currentCLRegion];
   
       }
   }
   ```

### Android

1. Google playサービスまたはAndroidロケーションサービスから取得した場所の更新をPlaces Extensionに渡します。

2. Places Extension APIを使 `getNearbyPointsOfInterest` 用して、現在の場所周辺のオブジェクト `PlacesPoi` のリストを取得します。

   ```java
       LocationCallback callback = new LocationCallback() {
               @Override
               public void onLocationResult(LocationResult locationResult) {
                   super.onLocationResult(locationResult);
   
                   Places.getNearbyPointsOfInterest(currentLocation, 10, new            AdobeCallback<List<PlacesPOI>>() {
               @Override
               public void call(List<PlacesPOI> pois)
                   starMonitoringGeofence(pois);
               }
           });
   
               }
           };
   ```

3. 取得したオブジェクトからデータを抽 `PlacesPOI` 出し、POIの監視を開始します。

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
