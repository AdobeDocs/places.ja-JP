---
title: Places Service のアプリ内メッセージ
description: この節では、Campaign Standardでアプリ内メッセージにCampaign Standardしてプッシュメッセージを使用する方法について説明します。
exl-id: c80727b8-20c9-4ca0-9f2c-20ec646bb7fa
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# Places Service を使用したアプリ内メッセージ {#in-app-messages-loc-service}

この情報は、Places Service 情報を使用してアプリ内メッセージまたはローカル通知を送信する方法を理解するのに役立ちます。

## 前提条件

開始する前に、次のタスクを完了してください。

* モバイルアプリケーションを、[Adobe Campaign Standard extension](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) を含むAdobe Experience Platform Mobile SDK で設定します。

* [Adobe Experience Platform Mobile SDK](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) をアプリに組み込みます。
* [Adobe Campaign Standard拡張機能 &#x200B;](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) をモバイルアプリ設定に追加します。

* Places Service POI 管理インターフェイスでの [POI の作成 &#x200B;](/help/poi-mgmt-ui/create-a-poi-ui.md)。

* モバイルアプリケーションに [Places 拡張機能 &#x200B;](/help/places-ext-aep-sdks/places-extension/places-extension.md) と地域モニタリングソリューション（[CoreLocation ドキュメント &#x200B;](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) for iOSまたは [Android location ドキュメント &#x200B;](https://developer.android.com/training/location/geofencing)）をインストールして設定します。

## ジオフェンスの入口または出口に基づくアプリ内メッセージの送信

1. Adobe Campaign Standard インスタンスで、「**[!UICONTROL アプリ内メッセージを作成]**」をクリックします。
1. メッセージタイプとして「**[!UICONTROL モバイルアプリケーションのすべてのユーザーをターゲットにする]**」を選択します。
1. **[!UICONTROL 次へ]** をクリックして、一般的な詳細を入力します。
1. 左側のペインで、Places Services に関連する様々なトリガーを使用できることを確認します。

   * ユーザーが POI のジオフェンスを入力した場合に、アプリ内メッセージを表示するように選択できます。
   * また、Places Services UI で定義されたメタデータを使用して、オーディエンスをフィルタリングすることもできます。

   次の例では、無料の飲み物プログラムに参加している休暇リゾートに入園しているユーザーにのみ表示されるアプリ内メッセージをトリガーにし、入園時にそのユーザーにクーポンを送信することができます。

   ![&#x200B; 「アプリ内メッセージがメタデータを配置」 &#x200B;](/help/assets/last-entered-vacation.png)

1. 「**[!UICONTROL 次へ]**」をクリックして、配信用のアプリ内メッセージの作成を終了します。

   ![&#x200B; イベントの作成」 &#x200B;](/help/assets/prepare-ACS.png)

   アプリ内メッセージ配信をテストするには、Xcode またはAndroid Studio でアプリを起動し、場所シミュレーターを使用して、メッセージ送信条件に適合する POI を選択します。

   ![&#x200B; 「ドリンククーポン」 &#x200B;](/help/assets/drink-coupon-on-app.png)

Adobe Campaign Standardで Places Services を使用すると、ジオフェンスの入口と出口に基づいてメッセージをセグメント化し、ユーザーをターゲットにする強力なツールを利用できます。 この統合により、よりパーソナライズされたコンテキストに沿ったユースケースを作成できます。

<!--I changed this embed to a link to pass validation. We should not link to youtube videos, so please upload this to MCP-->

[Campaign メッセージングを使用したAdobe Experience Platform ロケーション サービス &#x200B;](https://www.youtube.com/watch?v=ikiTTQw9c-o)
