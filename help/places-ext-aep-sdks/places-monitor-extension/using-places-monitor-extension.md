---
title: プレースモニター拡張機能の使用
seo-title: プレースモニター拡張機能の使用
description: プレースモニター拡張機能のインストール、設定、使用方法に関する情報です。
seo-description: プレースモニター拡張機能のインストール、設定、使用方法に関する情報です。
translation-type: tm+mt
source-git-commit: 419df41a0abeac1ac2a77f32bfa818b4edf3baeb

---


# プレースモニター拡張機能の使用 {#using-places-monitor-extension}

プレースモニター拡張機能を使用するには、次のタスクを実行します。

## Experience Platform LaunchにPlaces Monitor Extensionをインストールする

1. In Experience Platform Launch, click the **[!UICONTROL Extensions]** tab.
1. タブで、拡 **[!UICONTROL Catalog]** 張機能を探し、「イ **[!UICONTROL Places Monitor]** ンストール」をクリック **します**。
1. 「**[!UICONTROL Save]**」をクリックします。
1. 公開プロセスに従ってSDK設定を更新します。

### プレースモニター拡張機能の設定 {#configure-places-monitor-extension}

プレースモニター拡張機能の設定タスクはありません。

![場所モニターの設定](/help/assets/configure_places_monitor.png)

## プレースモニター拡張機能のアプリへの追加 {#add-monitor-extension-to-app}

AndroidまたはiOSアプリにプレースモニター拡張機能を追加する必要があります。

### Android

Androidで、次の手順を実行します。

#### Java

1. アプリのグレードファイルを使用して、プレースモニター拡張機能とプレース拡張機能をプロジェクトに追加します。

1. また、最新のGoogle Locationサービスをグレードファイルに含めます。

   ```java
   implementation 'com.adobe.marketing.mobile:places:1.+'
   implementation 'com.adobe.marketing.mobile:places-monitor:1.+'
   implementation 'com.adobe.marketing.mobile:sdk-core:1.+'
   implementation 'com.google.android.gms:play-services-location:16.0.0'
   ```

1. アプリケーションのメインアクティビティにプレースモニター拡張機能を読み込みます。

   ```java
   import com.adobe.marketing.mobile.PlacesMonitor;
   ```

### iOS

iOSで、次の手順を実行します。

1. を追加して、Cocoapodsを使用してプロジェクトにライブラリ `Podfile` を追加しま `pod 'ACPPlacesMonitor'`す。
1. 場所および場所モニターライブラリの読み込み：

#### Objective-C

```objectivec
#import "ACPCore.h"
#import "ACPPlaces.h"
#import "ACPPlacesMonitor.h"
```

#### Swift

```swift
import ACPCore
import ACPPlaces
import ACPPlacesMonitor
```


## プレースモニターの登録と起動 {#register-start-places-monitor}

AndroidまたはiOSでプレースモニターを登録して起動する必要があります。

## Android

Androidで、次の手順を実行します。

### Java

アプリのメソッドで、プレース `OnCreate` モニターの拡張機能を登録します。

```java
public class MobileApp extends Application {
    @Override
    public void onCreate() {
        super.onCreate();
        MobileCore.setApplication(this);
        MobileCore.ConfigureWithAppId("yourAppId");
        try {
            PlacesMonitor.registerExtension(); //Register PlacesMonitor with Mobile Core
            Places.registerExtension(); //Register Places with Mobile Core
            MobileCore.start(null);
        } catch (Exception e) {
            //Log the exception
         }
    }
}
```

>[!IMPORTANT]
>
>場所の監視は、場所の拡張機能に依存します。 Places 監視拡張機能を手動でインストールする場合は、プロジェクトに `places.aar` ライブラリも追加してください。

## iOS

iOSアプリで、Mobile coreに`application:didFinishLaunchingWithOptions`「登録 `PlacesMonitor` 」と「場所」を選択します。

### Objective-C

```objectivec
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary*)launchOptions {
    [ACPCore configureWithAppId:@"yourAppId"];
    [ACPPlaces registerExtension];
    [ACPPlacesMonitor registerExtension];
    [ACPCore start:^{            
        // do other initialization required for the SDK
        [ACPPlacesMonitor start];
    }];

    return YES;
}
```

#### Swift

```swift
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
    ACPCore.configure(withAppId: "yourAppId")
    ACPPlaces.registerExtension()       
    ACPPlacesMonitor.registerExtension()
    ACPCore.start({
        // do other initialization required for the SDK
        ACPPlacesMonitor.start()
    })

    // Override point for customization after application launch.        
    return true
}
```

>[!IMPORTANT]
>
>場所の監視は、場所の拡張機能に依存します。 When manually installing the Places Monitor extension, ensure that you also add the `libACPPlaces_iOS.a` library to your project.


## マニフェストへの権限の追加

### Android

**Java**

Androidのすべてのバージョンで、アプリに場所の権限が必要であることを宣言するには、アプリのマニフェストに要素を最上位 `<uses-permission>` の要素の子として追加し `<manifest>` ます。 APIレベル29以降をターゲットとするAndroidアプリケーションの場合、アプリケーションがバックグラウンドで場所にアクセスできるようにするには、ACCESS_BACKGROUND_LOCATION権限を含めます。

```java
<manifest xmlns:android="http://schemas.android.com/apk/res/android" package="com.adobe.placesapp">
  <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
    // Only for Android apps targeting API level 29 and above
  <uses-permission android:name="android.permission.ACCESS_BACKGROUND_LOCATION" />
  <application>        
    ...    
  </application>
</manifest>
```


## バックグラウンドで場所の更新を有効にする {#enable-location-updates-background}

iOSは、停止中のアプリケーションや実行されなくなったアプリケーションへの位置イベントの配信をサポートします。 プレースモニター拡張機能のバックグラウンドで場所の更新を受け取るには、でアプリの場所の更新機能を設定しま `Xcode.background-location-updates`す。

![プレースモニターの使用](/help/assets/using-the-places-monitor_1.png)

## plistキーの設定

アプリのファイルには、次のキーを含める必要があ `Info.plist` ります。

* `NSLocationWhenInUseUsageDescription`  — アプリがフォアグラウンドでの実行中にユーザーの場所情報へのアクセスを要求する理由を説明するテキストが必要です。
* `NSLocationAlwaysAndWhenInUseUsageDescription`  — アプリがユーザーの場所情報へのアクセスを常に要求する理由を説明するテキストが必要です。

>[!TIP]
>
>アプリがiOS 10以前をサポートしている場合は、 `NSLocationAlwaysUsageDescription` キーも必須です。

![](/help/assets/using-the-places-monitor_2.png)
