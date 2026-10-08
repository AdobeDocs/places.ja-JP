---
title: Places サービスを使用したアプリ内メッセージ
description: この節では、Campaign StandardでプッシュメッセージをCampaign Standardのアプリ内メッセージと共に使用する方法について説明します。
exl-id: c80727b8-20c9-4ca0-9f2c-20ec646bb7fa
TQID: https://experienceleague.adobe.com/H2gW4nvnx8Es33S8nCt52OIUsNOY5SG1SZVJPw0BFFg
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
    internal-label: CX Enterprise
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
    internal-label: Target
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
  - id: f002a92a-b99f-47a4-90c8-65e0e415bc7a
    internal-label: Pass
feature_v2:
  - id: d833d0ef-8ed5-4cff-a5e7-9f12abd02a31
    internal-label: SDKs
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
    internal-label: Data collection
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
    internal-label: Places
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
    internal-label: Metadata
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
source-git-commit: d8704da9c84a066f72471421290d4b46c65f41e1
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%
---
# Places サービスを使用したアプリ内メッセージ {#in-app-messages-loc-service}

この情報は、Places サービス情報を使用して、アプリ内メッセージやローカル通知を送信する方法を理解するのに役立ちます。

## 前提条件

開始する前に、次のタスクを完了します。

* [Adobe Campaign Standard拡張機能](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)を含む、Adobe Experience Platform Mobile SDKで設定されたモバイルアプリケーションを使用している。

* [Adobe Experience Platform モバイル SDK](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk)をアプリに統合します。
* [Adobe Campaign Standard拡張機能](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)をモバイルアプリ設定に追加します。

* [Places サービス POI管理インターフェイスでPOI](/help/poi-mgmt-ui/create-a-poi-ui.md)を作成します。

* [Places拡張機能](/help/places-ext-aep-sdks/places-extension/places-extension.md)とリージョンモニタリングソリューション（[CoreLocation documentation](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) for iOS、または[Android location documentation](https://developer.android.com/training/location/geofencing)）をモバイルアプリケーションにインストールして設定します。

## ジオフェンスの出入りに基づくアプリ内メッセージの送信

1. Adobe Campaign Standard インスタンスで、**[!UICONTROL アプリ内メッセージの作成]**&#x200B;をクリックします。
1. メッセージの種類として、**[!UICONTROL モバイルアプリケーションのすべてのユーザーをターゲット]**&#x200B;を選択します。
1. 「**[!UICONTROL 次へ]**」をクリックし、一般的な詳細を入力します。
1. 左側のペインで、Places サービスに関連する様々なトリガーを使用できることを確認します。

   * ユーザーがPOI ジオフェンスを入力した場合は、アプリ内メッセージを表示するように選択できます。
   * Places サービス UIで定義されたメタデータを使用して、オーディエンスをフィルタリングすることもできます。

   以下の例では、無料ドリンクプログラムに参加しているバケーションリゾートに入ったユーザーにのみ表示されるアプリ内メッセージをトリガーできます。また、そのユーザーが到着したときにクーポンを送りたい場合もあります。

   ![&quot;アプリ内メッセージの場所メタデータ&quot;](/help/assets/last-entered-vacation.png)

1. 「**[!UICONTROL 次へ]**」をクリックして、配信用のアプリ内メッセージの作成を完了します。

   ![&quot;イベントを作成&quot;](/help/assets/prepare-ACS.png)

   アプリ内メッセージ配信をテストするには、XcodeまたはAndroid studioでアプリケーションを起動し、位置情報シミュレーターを使用してメッセージ条件に合ったPOIを選択します。

   ![&quot;ドリンククーポン&quot;](/help/assets/drink-coupon-on-app.png)

Adobe Campaign StandardでPlaces サービスを利用すると、ジオフェンスの出入りに基づいてメッセージをセグメント化し、ターゲティングする強力なツールが得られます。 この統合により、よりパーソナライズされたコンテキストに沿ったユースケースを構築できます。

<!--I changed this embed to a link to pass validation. We should not link to youtube videos, so please upload this to MCP-->

[Adobe Experience Platform Location ServiceとCampaign Messaging](https://www.youtube.com/watch?v=ikiTTQw9c-o)
