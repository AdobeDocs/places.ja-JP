---
title: Places Monitor APIリファレンス
description: プレースモニターのAPIのリスト。
translation-type: tm+mt
source-git-commit: 5a21e734c0ef56c815389a9f08b445bedaae557a
workflow-type: tm+mt
source-wordcount: '1090'
ht-degree: 2%

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

Experience PlatformSDKの残りの部分を初期化する `onCreate` メソッドで、このメソッドを呼び出します。

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

## 拡張機能のバージョン

Places Monitor拡張機能の現在のバージョンを返す

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

## 開始デバイスの監視

デバイスの場所の追跡を開始し、周辺の場所を監視します。

### 開始(Android)

デバイスの場所を使用する権限がユーザーによって付与されていない場合、 `start` APIへの最初の呼び出しによって、ユーザーに権限を求めるメッセージが表示されます。

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
>* Places Serviceの認証がアプリケーションに提供されていない場合、最初の `start` APIの呼び出しでは、アプリケーションに対して設定されたPlaces Serviceを使用するように承認が要求されます。
>* デバイスの機能に応じて、認証が提供されている場合は、プレースモニターは現在設定されている場所に基づいてユーザーの場所を追跡し `ACPPlacesMonitorMode`ます。 デフォルトでは、モニタはを使用 `ACPPlacesMonitorModeSignificantChanges`します。


>[!CAUTION]
>
>SDKの初期化が終了する前に開始の監視の呼び出しが行われた場合は、無視される場合があります。

に提供されたコールバックからを呼び出すことで、SDKの初期化 `start` が完了したことを確認でき `ACPCore::start:`ます。

このAPIの構文とコード例を次に示します。

#### 構文

```objectivec
+ (void) start;
```

#### 例

SDKの初期化時にプレースモニターを開始する：

```objective-c
[ACPCore start:^{
    [ACPPlacesMonitor start];
}];
```

アプリの実行後にプレースモニターを起動する：

```objective-c
[ACPPlacesMonitor start];
```

## デバイス監視の停止

デバイスの位置の追跡を停止します。

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

このAPIは、デバイスの場所を即時に更新する場合に使用します。 このAPIを呼び出すと、デバイスは指定した正確さのレベルで位置を判断しようとします。 このプロセスは、拡張機能によって監視される近くのPOIも更新します。

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

このAPIを使用して、ユーザーが入力を求められ、Places Serviceでの使用を承認された場所の権限のタイプを設定できます。

### SetLocationPermission(Android)

このAPIは、ユーザーに選択を求める場所の権限リクエストのタイプを設定します。

>[!TIP]
>
>このAPIは、Android 10以降のデバイスでのみ有効です。
>
>ユーザーに表示される適切な認証プロンプトを設定するには、このAPIを `PlacesMonitor.start()`このメソッドを呼び出すと、アクティブに監視しながら、場所の権限レベルが要求された権限の値にアップグレードされます。 要求された認証レベルが既にアプリケーションユーザーによって提供または拒否されている場合、またはアクセス許可をから `ALWAYS_ALLOW` にダウングレードしようとした場合、このメソッドは無効 `WHILE_USING_APP`です。

場所の権限は、次のいずれかの値に設定できます。

* `PlacesMonitorLocationPermission.WHILE_USING_APP`

   この値を指定すると、アプリケーションの使用中にのみデバイスの場所にアクセスするようユーザーに促します。 アクティビティが前景で実行されているなど、ユーザーがデバイス画面でアプリを表示している場合、アプリは使用中と見なされます。

   >[!TIP]
   >
   >アプリのマニフェストファイルにACCESS_FINE_LOCATIONユーザー権限が設定されていることを確認します。

* `PlacesMonitorLocationPermission.ALWAYS_ALLOW`

   この値は、アプリケーションがバックグラウンドになっている場合でも、デバイスの場所にアクセスするようユーザーに促します。

   >[!TIP]
   >
   >アプリのマニフェストファイルにACCESS_BACKGROUND_LOCATIONとACCESS_FINE_LOCATIONのユーザー権限が設定されていることを確認します。

   `PlacesMonitorLocationPermission.ALWAYS_ALLOW` は、デフォルトの場所権限の値です。

>[!IMPORTANT]
>
>アプリユーザーに `WHILE_USING_APP` 権限が付与された場合、ジオフェンスはオペレーティングシステムに登録されません。 その結果、プレースモニター拡張機能によって、バックグラウンドで発生している地域で入口/出口イベントがトリガーされることはありません。

このAPIの構文とコード例を次に示します。

#### 構文

```java
public static void setLocationPermission(final PlacesMonitorLocationPermission placesMonitorLocationPermission)
```

#### 例

権限をリクエストするには、次の手順に従い `WHILE_USING_APP` ます。

```java
// set the location permission
PlacesMonitor.setLocationPermission(PlacesMonitorLocationPermission.WHILE_USING_APP);
// start monitoring
PlacesMonitor.start()
```

権限にアップグレードするには、次の手順に従い `ALWAYS_ALLOW` ます。

```java
// upgrade the permission level
PlacesMonitor.setLocationPermission(PlacesMonitorLocationPermission.ALWAYS_ALLOW);
```

### SetRequestAuthorizationLevel(iOS)

このAPIは、ユーザーに対してプロンプトが表示される場所の認証要求のタイプを設定します。

ユーザーに表示される適切な認証プロンプトを設定するには、を呼び出す `SetRequestAuthorizationLevel` 前にを呼び出し `[ACPPlacesMonitor start]`ます。 ユーザーに表示する適切な認証プロンプトを設定するには、このAPIを `[ACPPlacesMonitor start]`アクティブな監視中にこのメソッドを呼び出すと、場所の認証レベルが要求された認証値にアップグレードされます。 要求された認証レベルが、アプリケーションユーザーによって既に提供または拒否されている場合、またはから `ACPPlacesRequestAuthorizationLevelAlways``ACPPlacesRequestAuthorizationLevelWhenInUse` 認証へのアクセス許可がダウングレードされている場合は、このメソッドは無効です。

認証レベルは、次のいずれかの値に設定できます。

* `ACPPlacesRequestAuthorizationLevelWhenInUse`

   アプリの使用中にPlaces Serviceを使用するユーザーの権限を要求します。 ユーザープロンプトには、アプリのInfo.plistファイルの `NSLocationWhenInUseUsageDescription` キーのテキストが含まれ、このメソッドを呼び出す場合はそのキーの存在が必要です。 詳しくは、requestWhenInUseAuthorizationに関する [Appleのドキュメントを参照してください](https://developer.apple.com/documentation/corelocation/cllocationmanager/1620562-requestwheninuseauthorization)。

* `ACPPlacesRequestMonitorAuthorizationLevelAlways`

   アプリがバックグラウンドにある場合でも、この列挙を使用してPlaces Serviceを要求します。 アプリのInfo.plistに `NSLocationAlwaysUsageDescription` および `NSLocationWhenInUseUsageDescription` キーが必要です。 これらのキーは、ユーザープロンプトで表示されるテキストを定義します。 詳しくは、requestAlwaysAuthorizationに関する [Appleのドキュメントを参照してください](https://developer.apple.com/documentation/corelocation/cllocationmanager/1620551-requestalwaysauthorization)。

`ACPPlacesRequestAuthorizationLevelAlways` は、デフォルトのリクエスト認証値です。

>[!IMPORTANT]
>
>権限の使用を承認したアプリケーションは、バックグラウンドで発生している地域の入口/出口イベントをトリガーしません。 `ACPPlacesRequestAuthorizationLevelWhenInUse`

このAPIの構文とコード例を次に示します。

#### 構文

```objective-c
+ (void) setRequestAuthorizationLevel: (ACPPlacesRequestAuthorizationLevel) requestAuthorizationLevel;
```

#### 例

権限をリクエストするには、次の手順に従い `ACPPlacesRequestAuthorizationLevelWhenInUse` ます。

```objective-c
// set the request authorization level
[ACPPlacesMonitor setRequestAuthorizationLevel: ACPPlacesRequestAuthorizationLevelWhenInUse];
// start monitoring
[ACPPlacesMonitor start];
```

認証にアップグレードするには、次の手順に従い `ACPPlacesRequestAuthorizationLevelAlways` ます。

```objective-c
// set the request authorization level
[ACPPlacesMonitor setRequestAuthorizationLevel: ACPPlacesRequestAuthorizationLevelAlways];
```

## 監視モード（iOSのみ）

監視は、次のいずれかの値に設定できます。

* `ACPPlacesMonitorModeContinuous`

   監視拡張機能は、場所をより頻繁に受信し、処理します。 この監視方法は、大量の電力を消費しますが、高い精度を提供します。 詳しくは、継続的な監視に関する [Appleのドキュメントを参照してください](https://developer.apple.com/documentation/corelocation/cllocationmanager/1423750-startupdatinglocation)。

* `ACPPlacesMonitorModeSignificantChanges`

   監視拡張機能は、デバイスが以前に処理された場所からかなり離れた場所に移動した後にのみ、場所の更新を受信して処理します。 この監視方法は、継続的な監視方法よりも消費電力が少なくなります。 詳しくは、重要な監視に関する [Appleのドキュメントを参照してください](https://developer.apple.com/documentation/corelocation/cllocationmanager/1423531-startmonitoringsignificantlocati)

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
