---
title: Places APIリファレンス
seo-title: Places APIリファレンス
description: 場所のAPIリファレンスに関する情報です。
seo-description: 場所のAPIリファレンスに関する情報です。
translation-type: tm+mt
source-git-commit: fd1b37a0f50d93de1efff4cb38fc23253f02d517

---


# Places APIリファレンス {#places-api-reference}

場所のAPIリファレンスに関する情報を次に示します。

## 地域イベントの処理

デバイスがアプリの事前定義された場所領域の境界を越えると、領域とイベントタイプがSDKに渡され、処理されます。

### ProcessGeofence(Android)

指定したの領 `Geofence` 域イベントを処理しま `transitionType`す。

fromを渡 `transitionType` します `GeofencingEvent.getGeofenceTransition()`。 現在、およ `Geofence.GEOFENCE_TRANSITION_ENTER` びはサ `Geofence.GEOFENCE_TRANSITION_EXIT` ポートされています。

**構文**

このメソッドの構文を次に示します。

```java
public static void processGeofence(final Geofence geofence, final int transitionType);
```

**例**

Androidジオフェンスイベントを受け取るた `IntentService` めに登録されているユーザーで、このメソッドを呼び出します。

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

このメソッドは、ユーザーが特定の地域に入ったか出 `CLLocationManager` たかを知らせるdelegateで呼び出す必要があります。

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

すべてを `Geofences` 同時に `GeofencingEvent` 処理します。

**構文**

```java
public static void processGeofenceEvent(final GeofencingEvent geofencingEvent);
```

**例**

Androidジオフェンスイベントを受け取るた `IntentService` めに登録されているユーザーでこのメソッドを呼び出します

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

コールバック内の近くのPOIの順序付きリストを返します。

### GetNicherePointsOfInterest (Android)

このメソッドの構文を次に示します。

**構文**

```java
public static void getNearbyPointsOfInterest(final Location location,
    final int limit, final AdobeCallback<List<PlacesPOI>> callback);
```

**例**

このメソッドのコードサンプルを次に示します。

```java
Places.getNearbyPlaces(currentLocation, 10, new AdobeCallback<List<PlacesPOI>>() {
    @Override
    public void call(List<PlacesPOI> pois) {
        // do required processing with the returned nearbyPoi array
        startMonitoringPois(pois);
    }
});
```

### GetNicheredPointsOfInterest (iOS)

**構文**

```objectivec
+ (void) getNearbyPointsOfInterest: (nonnull CLLocation*) currentLocation
                             limit: (NSUInteger) limit
                          callback: (nullable void (^) (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi)) callback;
```

**例**

```objectivec
[ACPPlaces getNearbyPointsOfInterest:location
                               limit:10     
                            callback:^(NSArray<ACPPlacesPoi*>* nearbyPoi) {
    // do required processing with the returned nearbyPoi array
    [self startMonitoringPois:nearbyPOI];
}];
```

## 現在のデバイス目標地点の取得

デバイスが現在インしていることがわかっているPOIのリストを要求し、コールバックで返します。

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


## デバイスの場所を取得します

以前に知られていたデバイスの場所をPlaces拡張で要求します。

>[!TIP]
>
>Places拡張では、への呼び出しによって提供された場所についてのみ認識されま `GetNearbyPointsOfInterest`す。


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

## クライアント側データの消去


### 消去(Android)

「共有状態」、「ローカルストレージ」、「メモリ内」の各場所のクライアント側データをクリアします。

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

### clear(iOS)

「共有状態」、「ローカルストレージ」、「メモリ内」の各場所のクライアント側データをクリアします。

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
