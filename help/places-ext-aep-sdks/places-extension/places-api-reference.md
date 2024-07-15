---
title: Places API リファレンス
description: Places の API リファレンスに関する情報です。
feature: Mobile SDK
exl-id: ce1a113c-dee0-49df-8d2f-789ccc1c8322
source-git-commit: f521d5e3b0b69977877d88382ce41fcb7d1c54b9
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 32%

---

# Places API リファレンス {#places-api-reference}

Places 拡張機能の API リファレンスに関する情報を次に示します。

## 地域イベントの処理

デバイスがアプリの事前定義済みの Places Service 地域境界の 1 つを越えると、地域とイベントタイプが SDK に渡され、処理が行われます。

### ProcessGeofence （Android）

指定された `transitionType` の `Geofence` 地域イベントを処理します。

`GeofencingEvent.getGeofenceTransition()` から `transitionType` を渡します。 現在、`Geofence.GEOFENCE_TRANSITION_ENTER` と `Geofence.GEOFENCE_TRANSITION_EXIT` がサポートされています。

**構文**

このメソッドの構文を次に示します。

```java
public static void processGeofence(final Geofence geofence, final int transitionType);
```

**例**

Android ジオフェンスイベントを受け取るために登録されている `IntentService` で、このメソッドを呼び出します。

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

### ProcessRegionEvent （iOS）

このメソッドは、ユーザーが特定の領域に入ったか出たかを示す `CLLocationManager` デリゲートで呼び出す必要があります。

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

### ProcessGeofencingEvent （Android）

`GeofencingEvent` 内のすべての `Geofences` を同時に処理します。

**構文**

```java
public static void processGeofenceEvent(final GeofencingEvent geofencingEvent);
```

**例**

Android ジオフェンスイベントを受け取るために登録されている `IntentService` で、このメソッドを呼び出します

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

## 近くの目標地点を取得

コールバックで近隣の POI の順序付きリストを返します。 このメソッドのオーバーロードされたバージョンは、結果のネットワーク呼び出しで問題が発生した場合にエラーコードを返します。

### GetNearcomerPointsOfInterest （Android）

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

### GetNearcomerPointsOfInterest （iOS）

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

デバイスが現在存在することが知られている POI のリストをリクエストし、コールバックで返します。

### GetCurrentPointsOfInterest （Android）

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

### GetCurrentPointsOfInterest （iOS）

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


## デバイスの場所の取得

デバイスの場所（旧称：場所）をリクエストします。

>[!TIP]
>
>Places 拡張機能は、`GetNearbyPointsOfInterest` への呼び出しを介して提供された場所についてのみ認識します。


### GetLastKnownLocation （Android）

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

### GetLastKnownLocation （iOS）

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

## クライアントサイドのデータのクリア


### 消去（Android）

共有状態、ローカルストレージ、メモリ内の場所の拡張機能のクライアントサイドのデータをクリアします。

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

### 消去（iOS）

共有状態、ローカルストレージ、メモリ内の場所の拡張機能のクライアントサイドのデータをクリアします。

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

## 場所の認証ステータスを設定

### setAuthorizationStatus （Android）

*Places v1.4.0 以降で使用可能*

場所の拡張機能で認証ステータスを設定します。

提供されたステータスは、場所の共有状態に保存され、参照用です。
このメソッドを呼び出しても、このデバイスの実際の位置認証ステータスには影響しません。

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

### setAuthorizationStatus （iOS）

*ACPPlaces v1.3.0 以降で使用可能*

場所の拡張機能で認証ステータスを設定します。

提供されたステータスは、場所の共有状態に保存され、参照用です。
このメソッドを呼び出しても、このデバイスの実際の位置認証ステータスには影響しません。

デバイス認証ステータスが変更されると、`CLLocationManagerDelegate` の `locationManager:didChangeAuthorizationStatus:` メソッドが呼び出されます。 このメソッド内から、新しい `CLAuthorizationStatus` 値を ACPPlaces `setAuthorizationStatus:` API に渡す必要があります。

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
