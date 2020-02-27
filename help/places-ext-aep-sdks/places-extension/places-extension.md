---
title: Places 拡張機能
description: 「場所」拡張では、ユーザーの場所に基づいて行動できます。
translation-type: tm+mt
source-git-commit: 36ea8616aa05f5b825a2a4c791a00c5b3f332e9f

---


# Places 拡張機能 {#places-extension}

「場所」拡張では、ユーザーの場所に基づいて行動できます。 この拡張は、Places Query Service APIへのインターフェイスです。 GPS座標とジオフェンス領域イベントを含むイベントをリッスンすると、この拡張は、ルールエンジンで処理される新しいイベントをディスパッチします。 また、Places拡張機能は、APIから取得したアプリデータに最も近いPOIのリストを取得し、配信します。 APIから返される領域はキャッシュと永続性に保存されるので、オフライン処理に制限があります。

## Adobe Experience Platform LaunchにPlaces拡張をインストールする

1. In Experience Platform Launch, click the **[!UICONTROL Extensions]** tab.
1. タブで、 **[!UICONTROL Catalog]** 拡張機能を見つ **[!UICONTROL Places]** けてをクリックします **[!UICONTROL Install]**。
1. このプロパティで使用する場所ライブラリを選択します。 これらのライブラリは、アプリでアクセス可能になります。
1. **[!UICONTROL Save]**&#x200B;をクリックします。

   をクリックす **[!UICONTROL Save]**&#x200B;ると、Experience Platform SDKは選択したライブラリ内のPOIに関するPlaces Servicesを検索します。 POIデータはアプリの作成時にライブラリのダウンロードに含まれませんが、POIの場所ベースのサブセットは実行時にエンドユーザーのデバイスにダウンロードされ、ユーザーのGPS座標に基づきます。

1. 公開プロセスを完了してSDK設定を更新します。

   エクスペリエンスプラットフォームの起動での投稿について詳しくは、投稿を参照し [てくださ](https://docs.adobe.com/content/help/en/launch/using/reference/publish/overview.html)い。

### Configure the Places extension {#configure-places-extension}

![](//help/assets/places-extension.png)

## アプリに場所拡張を追加する {#add-places-to-app}

Places拡張機能はAndroidおよびiOSアプリに追加できます。

### Android

Javaを使用してPlaces拡張をアプリに追加するには：

1. アプリのグレードファイルを使用して、プロジェクトに場所拡張を追加します。

   ```java
   implementation 'com.adobe.marketing.mobile:places:1.+'
   implementation 'com.adobe.marketing.mobile:sdk-core:1.+'
   ```

1. アプリのメインアクティビティにPlaces拡張を読み込みます。

   ```java
   import com.adobe.marketing.mobile.Places;
   ```


### iOS

Objective-CまたはSwiftを使用してアプリに場所拡張を追加するには：

1. プロジェクトに場所とモバ [イルコア](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core) (Mobile Core)ライブラリを追加します。 次のポッドを `Podfile`

   ```objective-c
   pod 'ACPPlaces', '~> 1.0'
   pod 'ACPCore', '~> 2.0'    # minimum Core version for Places is 2.0.3
   ```

   また、Cocoapodを使用していない場合は、GithubのリリースページからMobile coreライブラリとPlacesライブラリを手動で含め [ること](https://github.com/Adobe-Marketing-Cloud/acp-sdks/releases/) もできます。

1. Cocoapodの更新：

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

### Mobile coreでのPlaces拡張の登録 {#register-places-mobile-core}

AndroidおよびiOSでMobile coreにPlaces拡張を登録する必要があります。

#### Android

アプリのメソッドで、Places `OnCreate` 拡張を登録します。

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

アプリのメソッドで、Places `application:didFinishLaunchingWithOptions:` 拡張を他のSDK登録コールに登録します。

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

特に、デバイスがバックグラウンドで場所の更新を受け取っていない場合は、場所のデータがすぐに古くなる可能性があります。

構成設定を設定して、デバイス上のPlacesメンバーシップデータの有効期間を制 `places.membershipttl` 御します。 渡される値は、Places状態がデバイスに対して有効なままになる秒数を表します。

#### Android

コールバック内で、 `MobileCore.start()` 呼び出す前に必要な変更を加えて設定を更新しま `lifecycleStart`す。

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

のメソッドのコールバックの最 `ACPCore`初の `start:` 行で、 `updateConfiguration:`

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

実行時にSDK設定をプログラム的に更新するには、次の情報を使用してPlaces拡張の設定値を変更します。 詳しくは、設定APIリファレン [スを参照してください](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/configuration/configuration-api-reference)。

| キー | 必須 | 説明 |
| :--- | :--- | :--- |
| `places.libraries` | ○ | モバイルアプリ用のPlaces拡張ライブラリ。 ライブラリIDと、モバイルアプリがサポートするライブラリの名前を指定します。 |
| `places.endpoint` | ○ | デフォルトのPlaces Query Serviceエンドポイント。ライブラリとPOIに関する情報の取得に使用されます。 |
| `places.membershipttl` | × | デフォルト値の3600（1時間の秒数）。 デバイスのメンバーシップ情報を保持する時間（秒）を示します。 |
