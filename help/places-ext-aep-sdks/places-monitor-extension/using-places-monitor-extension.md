---
title: 「Places Monitor」拡張機能の使用
description: プレースモニター拡張機能のインストール、設定、使用方法に関する情報です。
translation-type: tm+mt
source-git-commit: 7fdaace59886225b7fd9b0eba8cc6c2a139fa2d7
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 6%

---


# プレースモニタ拡張機能の使用{#using-places-monitor-extension}

プレースモニタ拡張機能を使用するには、次のタスクを実行します。

## Experience Platform LaunchでのPlaces Monitor Extensionのインストール

1. Experience Platform Launchで、「**[!UICONTROL 拡張子]**」タブをクリックします。
1. 「**[!UICONTROL カタログ]**」タブで、「**[!UICONTROL モニターを配置]**」の拡張子を探し、「**インストール**」をクリックします。
1. 「**[!UICONTROL 保存]**」をクリックします。
1. 公開プロセスに従ってSDK設定を更新します。

### プレースモニタ拡張機能の構成{#configure-places-monitor-extension}

Places Monitor拡張機能の設定タスクはありません。

![「場所モニター](/help/assets/configure_places_monitor.png)」の設定

## Places Monitor拡張機能追加をアプリケーションに追加{#add-monitor-extension-to-app}

AndroidまたはiOSアプリケーションにプレースモニター拡張機能を追加する手順は、以下のとおりです。

Places Monitor拡張機能のその他のプラットフォームサポートには、次のものがあります。
**[Cordovaプレイスモニタ](https://github.com/adobe/cordova-acpplaces-monitor/blob/master/README.md)**

**[ネイティブ・プレース・モニターに反応](https://github.com/adobe/react-native-acpplaces-monitor/blob/master/README.md)**

**[はためく場所モニタ](https://github.com/adobe/flutter_acpplaces_monitor/blob/master/README.md)**


### Android

Androidで、次の手順を実行します。

#### Java

1. アプ追加リのグレードルファイルを使用して、プレースモニター拡張子と配置拡張子をプロジェクトに追加します。

1. 最新のGoogle Locationサービスもグラデールファイルに含めます。

   ```java
   implementation 'com.adobe.marketing.mobile:places:1.+'
   implementation 'com.adobe.marketing.mobile:places-monitor:1.+'
   implementation 'com.adobe.marketing.mobile:sdk-core:1.+'
   implementation 'com.google.android.gms:play-services-location:16.0.0'
   ```

1. アプリケーションのメインアクティビティーにPlaces Monitor拡張機能を読み込みます。

   ```java
   import com.adobe.marketing.mobile.PlacesMonitor;
   ```

### iOS

iOSで、次の手順を実行します。

1. &lt;追加a1/>を追加して、Cocoapods `Podfile`を介してライブラリをプロジェクトに追加します。`pod 'ACPPlacesMonitor'`
1. 場所と場所モニターライブラリを読み込む：

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


## プレースモニタの登録と開始{#register-start-places-monitor}

AndroidまたはiOSのプレースモニターを登録して開始する必要があります。

## Android

Androidで、次の手順を実行します。

### Java

アプリの`OnCreate`メソッドで、プレースモニター拡張を登録します。

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
            PlacesMonitor.start();//Start monitoring the geo-fences
        } catch (Exception e) {
            //Log the exception
        }
    }
}
```

>[!IMPORTANT]
>
>場所の監視は、Places拡張子に応じて異なります。 Places 監視拡張機能を手動でインストールする場合は、プロジェクトに `places.aar` ライブラリも追加してください。

## iOS

iOSアプリの`application:didFinishLaunchingWithOptions`で、`PlacesMonitor`と場所をMobile Coreに登録します。

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

#### スウィフト

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
>場所の監視は、Places拡張子に応じて異なります。 プレースモニター拡張機能を手動でインストールする場合は、プロジェクトにも`libACPPlaces_iOS.a`ライブラリを追加してください。


## マニフェスト追加への権限

### Android

**Java**

Androidのすべてのバージョンで、アプリに場所の権限が必要であることを宣言するには、アプリマニフェストに`<uses-permission>`要素を最上位`<manifest>`要素の子として追加します。 APIレベル29以降のターゲットを使用するAndroidアプリケーションの場合、アプリケーションをバックグラウンドで場所にアクセスできるようにするには、ACCESS_BACKGROUND_LOCATION権限を含めます。

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


## バックグラウンドで場所の更新を有効にする{#enable-location-updates-background}

iOSでは、停止されているアプリや実行されなくなったアプリへの場所イベントの配信がサポートされます。 プレースモニター拡張機能のバックグラウンドで場所の更新を受け取るには、`Xcode.background-location-updates`でアプリの場所の更新機能を設定します。

![プレースモニターの使用](/help/assets/using-the-places-monitor_1.png)

## plistキーの設定

次のキーは、アプリの`Info.plist`ファイルに含める必要があります。

* `NSLocationWhenInUseUsageDescription`  — テキストは、前景での実行中にアプリがユーザーの位置情報へのアクセスを要求する理由を説明する必要があります。
* `NSLocationAlwaysAndWhenInUseUsageDescription`  — このテキストには、アプリがユーザーの位置情報へのアクセスを常に要求している理由を説明する必要があります。

>[!TIP]
>
>アプリがiOS 10以前をサポートしている場合は、`NSLocationAlwaysUsageDescription`キーも必要です。

![](/help/assets/using-the-places-monitor_2.png)
