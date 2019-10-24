---
title: '[配置]拡張子'
seo-title: '[配置]拡張子'
description: 「場所」拡張では、ユーザーの場所に基づいて行動できます。
seo-description: 「場所」拡張では、ユーザーの場所に基づいて行動できます。
translation-type: tm+mt
source-git-commit: fd1b37a0f50d93de1efff4cb38fc23253f02d517

---


# [配置]拡張子 {#places-extension}

「場所」拡張では、ユーザーの場所に基づいて行動できます。 この拡張は、Places Query Service APIへのインターフェイスです。 GPS座標とジオフェンス領域イベントを含むイベントをリッスンすると、この拡張は、ルールエンジンで処理される新しいイベントをディスパッチします。 また、Places拡張機能は、APIから取得したアプリデータに最も近いPOIのリストを取得し、配信します。 APIから返される領域はキャッシュと永続性に保存されるので、オフライン処理に制限があります。

## Adobe Experience Platform LaunchにPlaces拡張をインストールする

1. 「エクスペリエンスプラットフォームの起動」で、タブをクリ **[!UICONTROL Extensions]** ックします。
2. タブで、 **[!UICONTROL Catalog]** 拡張機能を見つ **[!UICONTROL Places]** けてをクリックします **[!UICONTROL Install]**。
3. このプロパティで使用する場所ライブラリを選択します。 これらのライブラリは、アプリでアクセス可能になります。
4. 「**[!UICONTROL Save]**」をクリックします。

   をクリックす **[!UICONTROL Save]**&#x200B;ると、Experience Platform SDKは選択したライブラリ内のPOIに関するPlaces Servicesを検索します。 POIデータはアプリの作成時にライブラリのダウンロードに含まれませんが、POIの場所ベースのサブセットは実行時にエンドユーザーのデバイスにダウンロードされ、ユーザーのGPS座標に基づきます。

5. 公開プロセスを完了してSDK設定を更新します。

   エクスペリエンスプラットフォームの起動での投稿について詳しくは、投稿を参照し [てくださ](https://docs.adobelaunch.com/launch-reference/publishing)い。

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

2. アプリのメインアクティビティにPlaces拡張を読み込みます。

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

   また、Cocoapodを使用していない場合は、Githubのリリースページから手動でMobile CoreライブラリとPlacesライブラリを含める [こともで](https://github.com/Adobe-Marketing-Cloud/acp-sdks/releases/) きます。

2. Cocoapodの更新：

   ```objective-c
   pod update
   ```

3. Xcodeを開き、AppDelegateクラスで、CoreヘッダーとPlacesヘッダーを読み込みます。

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

### モバイルコアへの場所の登録 {#register-places-mobile-core}

AndroidおよびiOSでMobile coreにPlacesを登録する必要があります。

#### Android

アプリのメソッドで、ロケーシ `OnCreate` ョンサービスの拡張機能を登録します。

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

## 設定キー

実行時にSDK設定をプログラム的に更新するには、次の情報を使用してPlaces設定値を変更します。 詳しくは、設定APIリファレン [スを参照してください](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/configuration/configuration-api-reference)。

| キー | 必須 | 説明 |
| :--- | :--- | :--- |
| `places.libraries` | ○ | モバイルアプリ用の場所ライブラリ。 ライブラリIDと、モバイルアプリがサポートするライブラリの名前を指定します。 |
| `places.endpoint` | ○ | デフォルトのExperience Platform Location Query Serviceエンドポイント。ライブラリとPOIに関する情報の取得に使用されます。 |

