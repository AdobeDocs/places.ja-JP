---
title: Places APIリファレンス
description: PlacesのAPIリファレンスに関する情報です。
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 32%

---


# Places APIリファレンス {#places-api-reference}

Places拡張機能のAPIリファレンスに関する情報を次に示します。

## 地域イベントの処理

デバイスがアプリの事前定義済みの場所サービスの領域の境界の1つを越えると、領域とイベントタイプがSDKに渡され、処理されます。

### ProcessGeofence(Android)

指定されたの領域 `Geofence` イベントを処理し `transitionType`ます。

からを渡 `transitionType` し `GeofencingEvent.getGeofenceTransition()`ます。 現在、 `Geofence.GEOFENCE_TRANSITION_ENTER` およびがサポートさ `Geofence.GEOFENCE_TRANSITION_EXIT` れています。

**構文**

このメソッドの構文を次に示します。

```java
public static void processGeofence(final Geofence geofence, final int transitionType);
```

**例**

Android Geofenceイベントの受信用に登録さ `IntentService` れているユーザーで、このメソッドを呼び出します。

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

### ProcessRegionEvent(iOS)

このメソッドは、 `CLLocationManager` delegateで呼び出す必要があります。このメソッドは、ユーザーが特定の領域に入ったか出たかを知らせます。

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

### ProcessGeofencingEvent(Android)

すべて `Geofences` を同時に処理 `GeofencingEvent` します。

**構文**

```java
public static void processGeofenceEvent(final GeofencingEvent geofencingEvent);
```

**例**

Android Geofenceイベントの受信用に登録さ `IntentService` れているユーザーでこのメソッドを呼び出す

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

コールバックで、隣接するPOIの順序付けられたリストを返します。 このメソッドのオーバーロードされたバージョンは、結果のネットワーク呼び出しで何か問題が発生した場合にエラーコードを返します。

### GetNichlorePointsOfInterest (Android)

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

### GetNichlorePointsOfInterest (iOS)

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

デバイスが現在存在することがわかっているPOIのリストを要求し、コールバックで返します。

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

Places拡張機能によって、既知のデバイスの場所を要求します。

>[!TIP]
>
>Places拡張機能では、への呼び出しによって提供された場所についてのみ認識され `GetNearbyPointsOfInterest`ます。


### GetLastKnownLocation(Android)

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

### GetLastKnownLocation(iOS)

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

## クライアント側のデータの消去


### クリア(Android)

共有状態、ローカルストレージ、およびメモリ内のPlaces拡張のクライアント側データを消去します。

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

### クリア(iOS)

共有状態、ローカルストレージ、およびメモリ内のPlaces拡張のクライアント側データを消去します。

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

## 場所の認証状態の設定

### setAuthorizationStatus(Android)

*Places v1.4.0以降で利用可能*

Places拡張で認証状態を設定します。

表示されるステータスは、[場所]共有状態に保存され、参照用にのみ表示されます。
このメソッドを呼び出しても、このデバイスの実際の場所の認証状態には影響しません。

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

### setAuthorizationStatus(iOS)

*ACPPlaces v1.3.0以降で利用可能*

Places拡張で認証状態を設定します。

表示されるステータスは、[場所]共有状態に保存され、参照用にのみ表示されます。
このメソッドを呼び出しても、このデバイスの実際の場所の認証状態には影響しません。

デバイスの認証状態が変更されると、 `locationManager:didChangeAuthorizationStatus:` メソッドが呼び出 `CLLocationManagerDelegate` されます。 このメソッド内から、新しい `CLAuthorizationStatus` 値をACPPlaces `setAuthorizationStatus:` APIに渡す必要があります。

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
