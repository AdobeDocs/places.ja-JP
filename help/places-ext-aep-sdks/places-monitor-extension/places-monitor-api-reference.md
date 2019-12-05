---
title: Places Monitor APIリファレンス
description: プレースモニターのAPIのリストです。
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# Places Monitor APIリファレンス {#places-api-reference}

## Register Places Monitor Extension

プレースモニター拡張機能をコアイベントハブに登録します。

### RegisterExtension(Android)

このAPIの構文とコード例を次に示します。

#### 構文

Javaの構文を次に示します。

```java
public static void registerExtension();
```

#### 例

このメソッドは、残りのExperience Platform SDK `onCreate` を初期化するメソッドで呼び出します。

```java
public class MobileApp extends Application {
  @Override
  public void onCreate(){
     super.onCreate();
     MobileCore.setApplication(this);
     try {
        PlacesMonitor.registerExtension();
     } catch (Exception e) {
       //Log the exception
       }
    }
 }
```

### RegisterExtension(iOS)

このAPIの構文とコード例を次に示します。

#### 構文

Objective-Cの構文を次に示します。

```objective-c
+ (void) registerExtension;
```

#### 例

This method should be called in the `didFinishLaunchingWithOptions` delegate method of the `AppDelegate`.

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {

    [ACPCore configureWithAppId:@"launch-appID"];    
    [ACPPlaces registerExtension];    
    [ACPPlacesMonitor registerExtension];

    [ACPCore start:^{
        // do other initialization of the SDK
    }];

    return YES;
}
```

## 拡張バージョン

プレースモニタ拡張機能の現在のバージョンを返す

### ExtensionVersion(Android)

このAPIの構文とコード例を次に示します。

#### 構文

```java
public static String extensionVersion();
```

#### 例

```java
String placesMonitorVersion = PlacesMonitor.extensionVersion();
```

### ExtensionVersion(iOS)

このAPIの構文とコード例を次に示します。

#### 構文

```objective-c
+ (nonnull NSString*) extensionVersion;
```

#### 例

```objective-c
NSString *placesMonitorVersion = [ACPPlacesMonitor extensionVersion];
```

## デバイス監視の開始

デバイスの場所の追跡を開始し、近くの場所を監視します。

### 開始(Android)

デバイスの場所を使用する権限がユーザーによって許可されていない場合、 `start` APIの最初の呼び出しで、ユーザーに権限を求めるメッセージが表示されます。

このAPIの構文とコード例を次に示します。

#### 構文

```java
public static void start();
```

#### 例

```java
PlacesMonitor.start();
```

### 開始(iOS)

>[!IMPORTANT]
>
>監視を開始するには、ロケーションサービスに必要な認証が必要です。
>
>* ロケーションサービスの認証がアプリケーションに提供されていない場合、 `start` APIへの最初の呼び出しは、アプリケーションに対して設定されたロケーションサービスを使用するための認証を要求します。
>* デバイスの機能に応じて、認証が提供されている場合、プレースモニターは現在設定されているユーザーの場所を基にして追跡しま `ACPPlacesMonitorMode`す。 デフォルトでは、モニターはを使用しま `ACPPlacesMonitorModeSignificantChanges`す。


>[!CAUTION]
>
>SDKの初期化が完了する前に監視を開始する呼び出しが行われた場合、その呼び出しは無視される可能性があります。

に提供されたコールバックから呼び出すことで、SDKの初期化 `start` が完了したことを確認できま `ACPCore::start:`す。

このAPIの構文とコード例を次に示します。

#### 構文

```objectivec
+ (void) start;
```

#### 例

SDKの初期化中にプレースモニターを起動します。

```objective-c
[ACPCore start:^{
    [ACPPlacesMonitor start];
}];
```

アプリの実行後にプレースモニターを起動します。

```objective-c
[ACPPlacesMonitor start];
```

## デバイス監視の停止

デバイスの場所の追跡を停止します。

### 停止(Android)

このAPIの構文とコード例を次に示します。

#### 構文

```java
public static void stop();
```

#### 例

```java
PlacesMonitor.stop();
```

### 停止(iOS)

このAPIの構文とコード例を次に示します。

#### 構文

```objectivec
+ (void) stop;
```

#### 例

```objective-c
[ACPPlacesMonitor stop];
```

## 更新場所

このAPIは、デバイスの場所を即座に更新する場合に使用します。 このAPIを呼び出すと、デバイスは指定した精度で場所を判断しようとします。 このプロセスにより、拡張によって監視される近くのPOIも更新されます。

### UpdateLocation(Android)

このAPIの構文とコード例を次に示します。

#### 構文

```java
public static void updateLocation();
```

#### 例

```java
PlacesMonitor.updateLocation();
```

### UpdateLocationNow(iOS)

#### 構文

```objective-c
+ (void) updateLocationNow;
```

#### 例

```objective-c
[ACPPlacesMonitor updateLocationNow];
```

## アプリの場所の権限

このAPIを使用して、ユーザーがロケーションサービスで使用するように求められ、承認されたロケーション権限のタイプを設定できます。

### SetLocationPermission(Android)

このAPIは、ユーザーに選択を求める場所の権限リクエストのタイプを設定します。

>[!TIP]
>
>このAPIは、Android 10以降のデバイスに対してのみ有効です。
>
>ユーザーに表示する適切な認証プロンプトを設定するには、このAPIを `PlacesMonitor.start()`このメソッドを呼び出すと、アクティブに監視しながら、場所の権限レベルが要求された権限の値にアップグレードされます。 要求された承認レベルが既にアプリケーションユーザーによって提供または拒否されている場合、または権限をからにダウングレードしようとした場合、こ `ALWAYS_ALLOW` のメ `WHILE_USING_APP`ソッドは無効です。

場所の権限は、次のいずれかの値に設定できます。

* `PlacesMonitorLocationPermission.WHILE_USING_APP`

   この値は、アプリケーションを使用している間にのみ、デバイスの場所にアクセスするようにユーザーに指示します。 アプリは、ユーザーがデバイス画面でアプリを見ているときに使用中と見なされます。例えば、アクティビティがフォアグラウンドで実行されている場合などです。

   >[!TIP]
   >
   >アプリのマニフェストファイルにACCESS_FINE_LOCATIONユーザー権限が設定されていることを確認します。

* `PlacesMonitorLocationPermission.ALWAYS_ALLOW`

   この値は、アプリケーションがバックグラウンドである場合でも、デバイスの場所にアクセスするようユーザーに指示します。

   >[!TIP]
   >
   >アプリのマニフェストファイルにACCESS_BACKGROUND_LOCATIONおよびACCESS_FINE_LOCATIONのユーザー権限が設定されていることを確認します。

   `PlacesMonitorLocationPermission.ALWAYS_ALLOW` は、デフォルトの場所権限の値です。

>[!IMPORTANT]
>
>アプリユーザーに権限が付与された場合、 `WHILE_USING_APP` geofencesはオペレーティングシステムに登録されません。 その結果、プレースモニター拡張機能では、バックグラウンドで発生している領域で入口/出口イベントがトリガーされません。

このAPIの構文とコード例を次に示します。

#### 構文

```java
public static void setLocationPermission(final PlacesMonitorLocationPermission placesMonitorLocationPermission)
```

#### 例

権限を要求するに `WHILE_USING_APP` は：

```java
// set the location permission
PlacesMonitor.setLocationPermission(PlacesMonitorLocationPermission.WHILE_USING_APP);
// start monitoring
PlacesMonitor.start()
```

権限にアップグレードす `ALWAYS_ALLOW` るには：

```java
// upgrade the permission level
PlacesMonitor.setLocationPermission(PlacesMonitorLocationPermission.ALWAYS_ALLOW);
```

### SetRequestAuthorizationLevel(iOS)

このAPIは、ユーザーに表示される場所の認証要求のタイプを設定します。

ユーザーに表示する適切な認証プロンプトを設定するには、を呼び出す前にを `SetRequestAuthorizationLevel` 呼び出しま `[ACPPlacesMonitor start]`す。 ユーザーに表示する適切な認証プロンプトを設定するには、このAPIを `[ACPPlacesMonitor start]`アクティブな監視中にこのメソッドを呼び出すと、場所の認証レベルが要求された認証値にアップグレードされます。 要求された承認レベルが既にアプリケーションユーザーによって提供または拒否されている場合、または承認から承認へのダウングレードがある場合、 `ACPPlacesRequestAuthorizationLevelAlways` こ `ACPPlacesRequestAuthorizationLevelWhenInUse` のメソッドは無効です。

認証レベルは、次のいずれかの値に設定できます。

* `ACPPlacesRequestAuthorizationLevelWhenInUse`

   アプリの使用中にロケーションサービスを使用するユーザーの権限を要求します。 ユーザープロンプトには、アプリのInfo.plist `NSLocationWhenInUseUsageDescription` ファイル内のキーからのテキストが含まれ、このメソッドを呼び出す際にそのキーの存在が必要です。 詳しくは、requestWhenInUseAuthorizationの [Appleのドキュメントを参照してください](https://developer.apple.com/documentation/corelocation/cllocationmanager/1620562-requestwheninuseauthorization)。

* `ACPPlacesRequestMonitorAuthorizationLevelAlways`

   アプリがバックグラウンドにある場合でも、この列挙を使用して場所サービスを要求します。 アプリのInfo.plistに `NSLocationAlwaysUsageDescription` キーと `NSLocationWhenInUseUsageDescription` キーが必要です。 これらのキーは、ユーザープロンプトの実行時に表示されるテキストを定義します。 詳しくは、requestAlwaysAuthorizationの [Appleのドキュメントを参照してください](https://developer.apple.com/documentation/corelocation/cllocationmanager/1620551-requestalwaysauthorization)。

`ACPPlacesRequestAuthorizationLevelAlways` はデフォルトのリクエスト承認値です。

>[!IMPORTANT]
>
>権限の使用を承認したアプリケーション `ACPPlacesRequestAuthorizationLevelWhenInUse` は、バックグラウンドで発生している地域では入口/出口イベントをトリガーできません。

このAPIの構文とコード例を次に示します。

#### 構文

```objective-c
+ (void) setRequestAuthorizationLevel: (ACPPlacesRequestAuthorizationLevel) requestAuthorizationLevel;
```

#### 例

権限を要求するに `ACPPlacesRequestAuthorizationLevelWhenInUse` は：

```objective-c
// set the request authorization level
[ACPPlacesMonitor setRequestAuthorizationLevel: ACPPlacesRequestAuthorizationLevelWhenInUse];
// start monitoring
[ACPPlacesMonitor start];
```

認証にアップグレードす `ACPPlacesRequestAuthorizationLevelAlways` るには：

```objective-c
// set the request authorization level
[ACPPlacesMonitor setRequestAuthorizationLevel: ACPPlacesRequestAuthorizationLevelAlways];
```

## 監視モード（iOSのみ）

監視は、次のいずれかの値に設定できます。

* `ACPPlacesMonitorModeContinuous`

   監視拡張機能は、より頻繁に場所を受信し、処理します。 この監視方法は、大量の電力を消費しますが、より高い精度を提供します。 詳しくは、継続的な監視に関する [Appleのドキュメントを参照してください](https://developer.apple.com/documentation/corelocation/cllocationmanager/1423750-startupdatinglocation)。

* `ACPPlacesMonitorModeSignificantChanges`

   監視拡張機能は、デバイスが前に処理された場所からかなり離れた場所に移動した後にのみ、場所の更新を受け取って処理します。 この監視戦略は、継続的な監視戦略に比べて消費電力が少なくなります。 詳しくは、重要な監視に関する [Appleのドキュメントを参照してください](https://developer.apple.com/documentation/corelocation/cllocationmanager/1423531-startmonitoringsignificantlocati)

### SetPlacesMonitorMode(iOS)

このAPIの構文とコード例を次に示します。

#### 構文

```objective-c
+ (void) setPlacesMonitorMode: (ACPPlacesMonitorMode) monitorMode;
```

#### 例

```objective-c
[ACPPlacesMonitor setPlacesMonitorMode:ACPPlacesMonitorModeSignificantChanges];
```
