---
title: Places Service を使用したアプリ内メッセージ
description: この節では、Campaign Standardでのアプリ内メッセージとのCampaign Standardでプッシュメッセージを使用する方法について説明します。
exl-id: c80727b8-20c9-4ca0-9f2c-20ec646bb7fa
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 4%

---

# Places Service を使用したアプリ内メッセージ {#in-app-messages-loc-service}

この情報は、Places Service 情報を使用してアプリ内メッセージやローカル通知を送信する方法を理解するのに役立ちます。

## 前提条件

開始する前に、次の作業を実行します。

* Adobe Experience Platform Mobile SDK を使用してモバイルアプリケーションを設定し、 [Adobe Campaign Standard拡張機能](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard).

* の統合 [Adobe Experience Platform Mobile SDK](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) をアプリに追加します。
* を [Adobe Campaign Standard Extension](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) をモバイルアプリ設定に追加します。

* [POI の作成](/help/poi-mgmt-ui/create-a-poi-ui.md) （Places Service POI 管理インターフェイス）を参照してください。

* のインストールと設定 [Places 拡張機能](/help/places-ext-aep-sdks/places-extension/places-extension.md) と地域監視ソリューション ([CoreLocation ドキュメント](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) (iOSの場合 )、または [Android ロケーションドキュメント](https://developer.android.com/training/location/geofencing)) を使用して、モバイルアプリケーションで設定できます。

## ジオフェンスの入口または出口に基づくアプリ内メッセージの送信

1. Adobe Campaign Standardインスタンスで、 **[!UICONTROL アプリ内メッセージの作成]**.
1. メッセージのタイプで、「 」を選択します。 **[!UICONTROL モバイルアプリケーションのすべてのユーザーをターゲット設定]**.
1. クリック **[!UICONTROL 次へ]** および一般的な詳細を入力します。
1. 左側のウィンドウで、Places Services に関連する様々なトリガーを使用できることを確認します。

   * ユーザーが POI ジオフェンスに入った場合に、アプリ内メッセージを表示するように選択できます。
   * また、Places Services UI で定義されたメタデータを使用して、オーディエンスをフィルタリングすることもできます。

   次の例では、無料飲み物プログラムに参加している休暇リゾートの 1 つに入ったユーザーにのみ表示されるアプリ内メッセージをトリガーし、ユーザーが到着したらクーポンを送信します。

   ![「アプリ内メッセージ場所メタデータ」](/help/assets/last-entered-vacation.png)

1. 次をクリック： **[!UICONTROL 次へ]** をクリックして、配信用のアプリ内メッセージの作成を完了します。

   ![&quot;イベントの作成&quot;](/help/assets/prepare-ACS.png)

   アプリ内メッセージ配信をテストするには、Xcode または Android Studio でアプリケーションを起動し、場所シミュレーターを使用して、メッセージング条件に合う POI を選択します。

   ![&quot;ドリンククーポン&quot;](/help/assets/drink-coupon-on-app.png)

Adobe Campaign Standardで Places Services を使用すると、ジオフェンスの入口と出口に基づいてメッセージをセグメント化し、ユーザーにターゲティングするための強力なツールが提供されます。 この統合により、よりパーソナライズされたコンテキストに沿ったユースケースを構築できます。

<!--I changed this embed to a link to pass validation. We should not link to youtube videos, so please upload this to MCP-->

[Adobe Experience Platform Location Service と Campaign のメッセージ](https://www.youtube.com/watch?v=ikiTTQw9c-o)
