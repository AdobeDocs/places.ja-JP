---
title: Places 拡張機能
description: Places拡張機能を使用すると、ユーザの場所に基づいて操作を行うことができます。
translation-type: tm+mt
source-git-commit: a7dddb78e1e00a0bde01ea668334932759a9dae8
workflow-type: tm+mt
source-wordcount: '694'
ht-degree: 5%

---


# Places 拡張機能 {#places-extension}

Places拡張機能を使用すると、ユーザの場所に基づいて操作を行うことができます。 この拡張機能は、PlacesクエリサービスAPIへのインターフェイスです。 GPS座標とジオフェンス領域のイベントを含むイベントをリッスンすると、この拡張は、ルールエンジンで処理される新しいイベントをディスパッチします。 また、Places拡張は、APIから取得したアプリデータに最も近いPOIのリストを取得し、配信します。 APIから返される領域はキャッシュと永続性に保存されるので、オフライン処理に制限があります。

## Places拡張機能をAdobe Experience Platform Launchにインストールする

1. In Experience Platform Launch, click the **[!UICONTROL Extensions]** tab.
1. タブで、 **[!UICONTROL Catalog]** 拡張機能を探してをクリックし **[!UICONTROL Places]****[!UICONTROL Install]**&#x200B;ます。
1. このプロパティで使用する場所ライブラリを選択します。 これらは、アプリケーションでアクセスできるライブラリです。
1. 「**[!UICONTROL Save]**」をクリックします。

   をクリックする **[!UICONTROL Save]**&#x200B;と、Experience PlatformSDKは、選択したライブラリ内のPOIをPlaces Servicesで検索します。 POIデータは、アプリケーションの構築時にライブラリのダウンロードには含まれませんが、POIの場所ベースのサブセットは、実行時にエンドユーザーのデバイスにダウンロードされ、ユーザーのGPS座標に基づきます。

1. 公開プロセスを完了して、SDK設定を更新します。

   Experience Platform Launchでの公開について詳しくは、 [公開を参照してください](https://docs.adobe.com/content/help/ja-JP/launch/using/reference/publish/overview.html)。

### Configure the Places extension {#configure-places-extension}

![](//help/assets/places-extension.png)

## アプリケ追加ーションの場所拡張 {#add-places-to-app}

Places拡張機能は、AndroidおよびiOSアプリに追加できます。 iOSまたはAndroidアプリケーションに場所を追加する手順は、次のとおりです。 プレース拡張は、次のプラットフォームでも利用できます。 以下のプラットフォームのいずれかを使用して開発する場合、アプリケーションに場所を追加する方法については、付属のリンクを参照してください。

**[Cordova Placesプラグイン](https://github.com/adobe/cordova-acpplaces/blob/master/README.md)**

**[ネイティブPlacesプラグインを反応](https://github.com/adobe/react-native-acpplaces/blob/master/README.md)**

**[Flatter Placesプラグイン](https://github.com/adobe/flutter-acpplaces_monitor)**

**[Xamarin Placesプラグイン](https://github.com/adobe/xamarin-acpcore)**


### Android

Javaを使用してPlaces拡張をアプリに追加するには：

1. アプリ追加のグレードルファイルを使用して、プロジェクトに拡張子を配置します。

   ```java
   implementation 'com.adobe.marketing.mobile:places:1.+'
   implementation 'com.adobe.marketing.mobile:sdk-core:1.+'
   ```

1. Places拡張機能をアプリケーションのメインアクティビティに読み込みます。

   ```java
   import com.adobe.marketing.mobile.Places;
   ```


### iOS

Objective-CまたはSwiftを使用してPlaces拡張をアプリに追加するには：

1. プ追加ロジェクトに配置および [モバイルコア](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core) ライブラリを追加します。 次のポッドを `Podfile`

   ```objective-c
   pod 'ACPPlaces', '~> 1.0'
   pod 'ACPCore', '~> 2.0'    # minimum Core version for Places is 2.0.3
   ```

   また、Cocoapodsを使用していない場合は、GithubのリリースページからMobile CoreとPlacesライブラリを手動で含めることも [できます](https://github.com/Adobe-Marketing-Cloud/acp-sdks/releases/) 。

1. Cocoapodsの更新：

   ```objective-c
   pod update
   ```

1. Xcodeを開き、AppDelegateクラスで、CoreヘッダーとPlacesヘッダーを読み込みます。

   **Objective-C**

   ```objective-c
   #import "ACPCore.h"
   #import "ACPPlaces.h"
   ```

   **Swift**

   ```swift
   import ACPCore
   import ACPPlaces
   ```

### Places拡張のMobile Coreへの登録 {#register-places-mobile-core}

Places拡張機能をAndroidおよびiOSのMobile Coreに登録する必要があります。

#### Android

アプリの `OnCreate` メソッドで、Places拡張を登録します。

```java
public class PlacesTestApp extends Application {

    @Override
    public void onCreate() {
        super.onCreate();
        MobileCore.setApplication(this);

        try {
            Places.registerExtension();
            MobileCore.start(null);
        } catch (Exception e) {
            Log.e("PlacesTestApp", e.getMessage());
        }
    }
}
```

#### iOS

アプリの `application:didFinishLaunchingWithOptions:` メソッドで、Places拡張を他のSDK登録呼び出しに登録します。

**Objective-C**

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    // make other sdk registration calls
    [ACPPlaces registerExtension];    
    return YES;
}
```

**Swift**

```swift
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
    // make other sdk registration calls
    ACPPlaces.registerExtension();
    return true;
}
```

### Placesメンバーシップの有効期間の変更 {#places-ttl}

特にデバイスがバックグラウンドで場所の更新を受け取っていない場合、場所データはすぐに古くなる可能性があります。

構成設定を設定して、デバイス上のPlacesメンバーシップデータの有効期間を制御し `places.membershipttl` ます。 渡される値は、Places状態がデバイスに対して有効なままである秒数を表します。

#### Android

コールバック内で、を呼び出す前に、必要な変更を加えて設定を `MobileCore.start()` 更新し `lifecycleStart`ます。

```java
public class PlacesTestApp extends Application {

    @Override
    public void onCreate() {
        super.onCreate();
        MobileCore.setApplication(this);

        try {
            Places.registerExtension();
            MobileCore.start(new AdobeCallback() {
                @Override
                public void call(Object o) {
                    // switch to your App ID from Launch
                    MobileCore.configureWithAppID("my-app-id");

                    final Map<String, Object> config = new HashMap<>();
                    config.put("places.membershipttl", 30);
                    MobileCore.updateConfiguration(config);

                    MobileCore.lifecycleStart(null);
                }
            });
        } catch (Exception e) {
            Log.e("PlacesTestApp", e.getMessage());
        }
    }
}
```

#### iOS

の `ACPCore``start:` メソッドのコールバックの最初の行で、 `updateConfiguration:`

**Objective-C**

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    // make other sdk registration calls

    const UIApplicationState appState = application.applicationState;
    [ACPCore start:^{
        [ACPCore updateConfiguration:@{@"places.membershipttl":@(30)}];

        if (appState != UIApplicationStateBackground) {
            [ACPCore lifecycleStart:nil];            
        }
    }];

    return YES;
}
```

**Swift**

```swift
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
    // make other sdk registration calls

    let appState = application.applicationState;            
    ACPCore.start {
        ACPCore.updateConfiguration(["places.membershipttl" : 30])

        if appState != .background {
            ACPCore.lifecycleStart(nil)
        }    
    }

    return true;
}
```

## 設定キー

実行時にSDK設定をプログラムで更新するには、次の情報を使用してPlaces拡張の設定値を変更します。 詳しくは、 [設定APIリファレンスを参照してください](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/configuration/configuration-api-reference)。

| キー | 必須 | 説明 |
| :--- | :--- | :--- |
| `places.libraries` | ○ | モバイルアプリ用のPlaces拡張ライブラリ。 ライブラリIDと、モバイルアプリケーションがサポートするライブラリの名前を指定します。 |
| `places.endpoint` | ○ | デフォルトの配置クエリサービスエンドポイントです。このエンドポイントは、ライブラリとPOIに関する情報の取得に使用されます。 |
| `places.membershipttl` | × | デフォルト値は3600（1時間あたりの秒数）です。 デバイスのメンバーシップ情報を保持する時間（秒）を示します。 |
