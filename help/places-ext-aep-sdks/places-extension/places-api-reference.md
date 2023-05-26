---
title: Places API リファレンス
description: Places の API リファレンスに関する情報です。
exl-id: ce1a113c-dee0-49df-8d2f-789ccc1c8322
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 32%

---

# Places API リファレンス {#places-api-reference}

Places 拡張機能の API リファレンスに関する情報を次に示します。

## 地域イベントの処理

デバイスがアプリの事前定義済みの Places Service 地域の境界を越えると、地域とイベントタイプが SDK に渡されて処理されます。

### ProcessGeofence (Android)

プロセス a `Geofence` 指定されたの地域イベント `transitionType`.

パス `transitionType` から `GeofencingEvent.getGeofenceTransition()`. 現在 `Geofence.GEOFENCE_TRANSITION_ENTER` および `Geofence.GEOFENCE_TRANSITION_EXIT` はサポートされています。

**構文**

このメソッドの構文を次に示します。

```java
public static void processGeofence(final Geofence geofence, final int transitionType);
```

**例**

このメソッドを `IntentService` Android ジオフェンスイベントの受信用に登録されている

このメソッドのコードサンプルを次に示します。

```java
public class GeofenceTransitionsIntentService extends IntentService {

    public GeofenceTransitionsIntentService() {
        super("GeofenceTransitionsIntentService");
    }

    protected void onHandleIntent(Intent intent) {
        GeofencingEvent geofencingEvent = GeofencingEvent.fromIntent(intent);

        List<Geofence> geofences = geofencingEvent.getTriggeringGeofences();

        if (geofences.size() > 0) {
          // Call the Places API to process information
          Places.processGeofence(geofences.get(0), geofencingEvent.getGeofenceTransition());
        }
    }
}
```

### ProcessRegionEvent (iOS)

このメソッドは、 `CLLocationManager` delegate：ユーザーが特定の地域に入ったか出たかを示します。

**構文**

このメソッドの構文を次に示します。

```objectivec
+ (void) processRegionEvent: (nonnull CLRegion*) region forRegionEventType: (ACPRegionEventType) eventType;
```

**例**

このメソッドのコードサンプルを次に示します。


```objectivec
- (void) locationManager:(CLLocationManager *)manager didEnterRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeEntry];
}

- (void) locationManager:(CLLocationManager *)manager didExitRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeExit];
}
```

### ProcessGeofencingEvent (Android)

すべてを処理 `Geofences` 内 `GeofencingEvent` 同時に

**構文**

```java
public static void processGeofenceEvent(final GeofencingEvent geofencingEvent);
```

**例**

このメソッドを `IntentService` Android ジオフェンスイベントの受信に登録されている

```java
public class GeofenceTransitionsIntentService extends IntentService {

    public GeofenceTransitionsIntentService() {
        super("GeofenceTransitionsIntentService");
    }

    protected void onHandleIntent(Intent intent) {
        GeofencingEvent geofencingEvent = GeofencingEvent.fromIntent(intent);
        // Call the Places API to process information
        Places.processGeofenceEvent(geofencingEvent);
    }
}
```

## 近くの目標地点の取得

コールバックで近くの POI の順序付きリストを返します。 オーバーロードされたバージョンのこのメソッドでは、結果のネットワーク呼び出しで問題が発生した場合、エラーコードが返されます。

### GetNicherPointsOfInterest (Android)

このメソッドの構文を次に示します。

**構文**

```java
public static void getNearbyPointsOfInterest(final Location location, final int limit,
                                             final AdobeCallback<List<PlacesPOI>> callback);

public static void getNearbyPointsOfInterest(final Location location, final int limit,
                                             final AdobeCallback<List<PlacesPOI>> callback,
                                             final AdobeCallback<PlacesRequestError> errorCallback);
```

**例**

このメソッドのコードサンプルを次に示します。

```java
// getNearbyPointsOfInterest without an error callback
Places.getNearbyPointsOfInterest(currentLocation, 10, new AdobeCallback<List<PlacesPOI>>() {
    @Override
    public void call(List<PlacesPOI> pois) {
        // do required processing with the returned nearbyPoi array
        startMonitoringPois(pois);
    }
});

// getNearbyPointsOfInterest with an error callback
Places.getNearbyPointsOfInterest(currentLocation, 10,
    new AdobeCallback<List<PlacesPOI>>() {
        @Override
        public void call(List<PlacesPOI> pois) {
            // do required processing with the returned nearbyPoi array
            startMonitoringPois(pois);
        }
    }, new AdobeCallback<PlacesRequestError>() {
        @Override
        public void call(PlacesRequestError placesRequestError) {
            // look for the placesRequestError and handle the error accordingly
            handleError(placesRequestError);
        }
    }
);
```

### GetNixeredPointsOfInterest (iOS)

**構文**

```objectivec
+ (void) getNearbyPointsOfInterest: (nonnull CLLocation*) currentLocation
                             limit: (NSUInteger) limit
                          callback: (nullable void (^) (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi)) callback;

+ (void) getNearbyPointsOfInterest: (nonnull CLLocation*) currentLocation
                             limit: (NSUInteger) limit
                          callback: (nullable void (^) (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi)) callback
                     errorCallback: (nullable void (^) (ACPPlacesRequestError result)) errorCallback;
```

**例**

```objectivec
// getNearbyPointsOfInterest without an error callback
[ACPPlaces getNearbyPointsOfInterest:location
                               limit:10     
                            callback:^(NSArray<ACPPlacesPoi*>* nearbyPoi) {
    // do required processing with the returned nearbyPoi array
    [self startMonitoringPois:nearbyPOI];
}];

// getNearbyPointsOfInterest with an error callback
[ACPPlaces getNearbyPointsOfInterest:location limit:10
    callback:^(NSArray<ACPPlacesPoi *> * _Nullable nearbyPoi) {
        // do required processing with the returned nearbyPoi array
        [self startMonitoringPois:nearbyPOI];
    } errorCallback:^(ACPPlacesRequestError result) {
        // look for the error and handle accordingly
        [self handleError:result];
    }
];
```

## 現在のデバイスの目標地点の取得

デバイスが現在存在することがわかっている POI のリストをリクエストし、コールバックで返します。

### GetCurrentPointsOfInterest (Android)

このメソッドの構文を次に示します。

**構文**

```java
public static void getCurrentPointsOfInterest(final AdobeCallback<List<PlacesPOI>> callback);
```

**例**

このメソッドのコードサンプルを次に示します。

```java
Places.getCurrentPointsOfInterest(new AdobeCallback<List<PlacesPOI>>() {
    @Override
    public void call(List<PlacesPOI> pois) {
        // use the obtained POIs that the device is within
        processUserWithinPois(pois);        
    }
});
```

### GetCurrentPointsOfInterest (iOS)

**構文**

このメソッドの構文を次に示します。

```objectivec
+ (void) getCurrentPointsOfInterest: (nullable void (^) (NSArray<ACPPlacesPoi*>* _Nullable userWithinPoi)) callback;
```

**例**

このメソッドのコードサンプルを次に示します。

```objectivec
[ACPPlaces getCurrentPointsOfInterest:^(NSArray<ACPPlacesPoi*>* userWithinPoi) {
    // do required processing with the returned userWithinPoi array
    [self processUserWithinPois:userWithinPoi];
}];
```


## デバイスの場所を取得する

Places 拡張機能によって、既に知られているデバイスの場所を要求します。

>[!TIP]
>
>Places 拡張機能は、への呼び出しを通じて提供された場所についてのみ把握しています。 `GetNearbyPointsOfInterest`.


### GetLastKnownLocation (Android)

**構文**

このメソッドの構文を次に示します。

```java
public static void getLastKnownLocation(final AdobeCallback<Location> callback);
```

**例**

このメソッドのコードサンプルを次に示します。

```java
Places.getLastKnownLocation(new AdobeCallback<Location>() {
    @Override
    public void call(Location lastLocation) {
        // do something with the last known location
        processLastKnownLocation(lastLocation);        
    }
});
```

### GetLastKnownLocation (iOS)

**構文**

このメソッドの構文を次に示します。

```objectivec
+ (void) getLastKnownLocation: (nullable void (^) (CLLocation* _Nullable lastLocation)) callback;
```

**例**

このメソッドのコードサンプルを次に示します。

```objectivec
[ACPPlaces getLastKnownLocation:^(CLLocation* lastLocation) {
    // do something with the last known location
    [self processLastKnownLocation:lastLocation];
}];
```

## クライアント側のデータを消去


### 消去 (Android)

共有状態、ローカルストレージ、インメモリの Places 拡張機能のクライアント側データをクリアします。

**構文**

このメソッドの構文を次に示します。

```java
public static void clear();
```

**例**

このメソッドのコードサンプルを次に示します。

```java
Places.clear();
```

### クリア (iOS)

共有状態、ローカルストレージ、インメモリの Places 拡張機能のクライアント側データをクリアします。

**構文**

このメソッドの構文を次に示します。

```objectivec
+ (void) clear;
```

**例**

このメソッドのコードサンプルを次に示します。

```objectivec
[ACPPlaces clear];
```

## 場所の認証状態を設定

### setAuthorizationStatus (Android)

*Places v1.4.0 以降で使用可能*

Places 拡張機能で認証ステータスを設定します。

提供されたステータスは「Places」共有状態に保存され、参照用にのみ表示されます。
このメソッドを呼び出しても、このデバイスの実際の位置認証状態には影響しません。

**構文**

このメソッドの構文を次に示します。

```java
public static void setAuthorizationStatus(final PlacesAuthorizationStatus status);
```

**例**

このメソッドのコードサンプルを次に示します。

```java
Places.setAuthorizationStatus(PlacesAuthorizationStatus.ALWAYS);
```

### setAuthorizationStatus (iOS)

*ACPPlaces v1.3.0 以降で使用可能*

Places 拡張機能で認証ステータスを設定します。

提供されたステータスは「Places」共有状態に保存され、参照用にのみ表示されます。
このメソッドを呼び出しても、このデバイスの実際の位置認証状態には影響しません。

デバイスの認証ステータスが変更されると、 `locationManager:didChangeAuthorizationStatus:` メソッド `CLLocationManagerDelegate` が呼び出されます。 このメソッド内から、新しい `CLAuthorizationStatus` 値を ACPPlaces に設定 `setAuthorizationStatus:` API

**構文**

このメソッドの構文を次に示します。

```objectivec
+ (void) setAuthorizationStatus: (CLAuthorizationStatus) status;
```

**例**

このメソッドのコードサンプルを次に示します。

```objectivec
- (void) locationManager: (CLLocationManager*) manager didChangeAuthorizationStatus: (CLAuthorizationStatus) status {    
    [ACPPlaces setAuthorizationStatus:status];
}
```
