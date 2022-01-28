---
title: Places 拡張機能
description: Places 拡張機能を使用すると、ユーザーの場所に基づいて行動できます。
exl-id: 09c02753-09b3-4e07-82b2-b6c72c4e0e42
source-git-commit: 795808b38851d5afcedc03f58e9a1d6342830934
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 5%

---

# Places 拡張機能 {#places-extension}

Places 拡張機能を使用すると、ユーザーの場所に基づいて行動できます。 この拡張機能は、Places クエリサービス API へのインターフェイスです。 GPS 座標とジオフェンス地域のイベントを含むイベントをリッスンすると、この拡張機能は、ルールエンジンで処理される新しいイベントをディスパッチします。 また、Places 拡張機能は、API から取得したアプリデータに最も近い POI のリストを取得し、配信します。 API から返される領域はキャッシュと永続性に保存され、オフラインでの処理が制限されます。

## Adobe Experience Platform Launchでの Places 拡張機能のインストール

1. Experience Platform Launchで、 **[!UICONTROL 拡張機能]** タブをクリックします。
1. の **[!UICONTROL カタログ]** タブで、 **[!UICONTROL 場所]** 拡張機能を選択し、「 **[!UICONTROL インストール]**.
1. このプロパティで使用する Places ライブラリを選択します。 これらは、アプリでアクセス可能なライブラリです。
1. 「**[!UICONTROL 保存]**」をクリックします。

   クリック時 **[!UICONTROL 保存]**&#x200B;を指定した場合、Experience PlatformSDK は、選択したライブラリ内の POI について Places サービスを検索します。 アプリの構築時に、POI データはライブラリのダウンロードに含まれませんが、POI の場所に基づくサブセットが実行時にエンドユーザーのデバイスにダウンロードされ、ユーザーの GPS 座標に基づきます。

1. 公開プロセスを完了して、SDK 設定を更新します。

   Experience Platform Launchでの公開について詳しくは、 [公開](https://docs.adobe.com/content/help/ja-JP/launch/using/reference/publish/overview.html).

### Places 拡張機能の設定 {#configure-places-extension}

![](/help/assets/places-extension.png)

## Places 拡張機能をアプリに追加する {#add-places-to-app}

Places 拡張機能は、Android およびiOSアプリに追加できます。 Places をiOSまたは Android アプリケーションに追加する手順は、以下のとおりです。 Places 拡張機能は、以下のプラットフォームでも使用できます。 これらのプラットフォームの 1 つを使用して開発する場合、アプリケーションに Places を追加するには、付属のリンクを参照してください。

**[Cordova Places プラグイン](https://github.com/adobe/cordova-acpplaces/blob/master/README.md)**

**[React Native Places プラグイン](https://github.com/adobe/react-native-acpplaces/blob/master/README.md)**

**[Flatter Places プラグイン](https://github.com/adobe/flutter-acpplaces_monitor)**

**[Xamarin Places プラグイン](https://github.com/adobe/xamarin-acpcore)**


### Android

Java を使用して Places 拡張機能をアプリに追加するには、次の手順を実行します。

1. アプリの gradle ファイルを使用して、Places 拡張機能をプロジェクトに追加します。

   ```java
   implementation 'com.adobe.marketing.mobile:places:1.+'
   implementation 'com.adobe.marketing.mobile:sdk-core:1.+'
   ```

1. Places 拡張機能をアプリケーションのメインアクティビティに読み込みます。

   ```java
   import com.adobe.marketing.mobile.Places;
   ```


### iOS

Objective-C または Swift を使用して Places 拡張機能をアプリに追加するには：

1. 場所を追加し、 [Mobile Core](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core) ライブラリをプロジェクトに追加します。 次のポッドを `Podfile`:

   ```objective-c
   pod 'ACPPlaces', '~> 1.0'
   pod 'ACPCore', '~> 2.0'    # minimum Core version for Places is 2.0.3
   ```

   また、Cocoapods を使用していない場合は、アドビの [リリースページ](https://github.com/Adobe-Marketing-Cloud/acp-sdks/releases/) を GitHub に設定します。

1. Cocoapods を更新します。

   ```objective-c
   pod update
   ```

1. Xcode を開き、AppDelegate クラスで、Core ヘッダーと Places ヘッダーを読み込みます。

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

### Places 拡張機能の Mobile Core への登録 {#register-places-mobile-core}

Android およびiOSで、Places 拡張機能を Mobile Core に登録する必要があります。

#### Android

アプリの `OnCreate` メソッドを使用して、Places 拡張機能を登録します。

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

アプリの `application:didFinishLaunchingWithOptions:` メソッドを使用して、 Places 拡張機能を他の SDK 登録呼び出しに登録します。

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

### Places メンバーシップの有効期間の変更 {#places-ttl}

特に、デバイスがバックグラウンドの場所の更新を受け取っていない場合は、場所データがすぐに古くなる可能性があります。

デバイス上の Places メンバーシップデータの有効期間を制御するには、 `places.membershipttl` 設定を行います。 渡された値は、Places 状態がデバイスで有効である状態を保持する秒数を表します。

#### Android

のコールバック内 `MobileCore.start()` を呼び出す前に、必要な変更を加えて設定を更新します。 `lifecycleStart`:

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

のコールバックの最初の行 `ACPCore`&#39;s `start:` メソッド、呼び出し `updateConfiguration:`

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

実行時にプログラムによって SDK 設定を更新するには、次の情報を使用して、Places 拡張機能の設定値を変更します。 詳しくは、 [設定 API リファレンス](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/configuration/configuration-api-reference).

| キー | 必須 | 説明 |
| :--- | :--- | :--- |
| `places.libraries` | ○ | モバイルアプリ用の Places 拡張機能ライブラリ。 ライブラリ ID と、モバイルアプリがサポートするライブラリの名前を指定します。 |
| `places.endpoint` | ○ | デフォルトの Places クエリサービスエンドポイント。ライブラリと POI に関する情報の取得に使用されます。 |
| `places.membershipttl` | × | デフォルト値の 3600（1 時間あたりの秒数）。 デバイスの Places メンバーシップ情報が有効である期間（秒）を示します。 |
