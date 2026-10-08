---
title: Places サービスを使用したプッシュ通知
description: この節では、Campaign Standardのプッシュ通知でPlaces サービスを使用する方法について説明します。
exl-id: 4b50f552-deb8-49cd-9221-fbbf33aaa5f9
TQID: https://experienceleague.adobe.com/tjJD7Qn27sp8wnNcNdjnANIveyzjG1PZ--3C3rCjrMQ
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
    internal-label: CX Enterprise
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
    internal-label: Target
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
feature_v2:
  - id: c132d929-fa62-4271-803e-b823be07b914
    internal-label: Profile
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
    internal-label: Data collection
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
    internal-label: Places
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
source-git-commit: d8704da9c84a066f72471421290d4b46c65f41e1
workflow-type: tm+mt
source-wordcount: '1026'
ht-degree: 2%
---
# Places サービスを使用したプッシュ通知 {#push-notifications}

このセクションでは、過去の位置情報を使用して、Adobe Campaign Standardを通じて配信されるプッシュ通知をターゲティングする方法について説明します。

## 前提条件

開始する前に、次のタスクを完了します。

* [Adobe Campaign Standard拡張機能](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)を含む、Adobe Experience Platform Mobile SDKで設定されたモバイルアプリケーションを使用している。

* [Adobe Experience Platform モバイル SDK](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk)をアプリに統合します。
* [Adobe Campaign Standard拡張機能](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)をモバイルアプリ設定に追加します。

* [Places サービス POI管理インターフェイスでPOI](/help/poi-mgmt-ui/create-a-poi-ui.md)を作成します。

* [Places拡張機能](/help/places-ext-aep-sdks/places-extension/places-extension.md)を有効にしてインストールします。


## Experience Platform Launchでのデータ要素の作成

Places拡張機能とリージョンモニタリングソリューション（[CoreLocation documentation](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) for iOS、または[Android location documentation](https://developer.android.com/training/location/geofencing)）がアプリケーションで正しく動作していることを確認したら、Experience Platform Launchでデータ要素を作成する必要があります。 データ要素を使用すると、Mobile SDK イベントハブを介して提供された拡張機能によって提供された情報を読み取り、クライアントアプリケーションからデータを取得するエイリアスとして機能できます。 Places拡張機能からデータを取得し、Places サービス情報をCampaignに送信するには、いくつかのデータ要素を作成する必要があります。

データ要素を作成するには：

1. Experience Platform Launch モバイルプロパティで、**[!UICONTROL データ要素]** タブをクリックし、**[!UICONTROL データ要素を追加]**&#x200B;をクリックします。
1. **[!UICONTROL 拡張機能]** ドロップダウンリストで、「**[!UICONTROL Places Service]**」を選択します。
1. **[!UICONTROL データ要素タイプ]** ドロップダウンリストから、**[!UICONTROL 名前]**&#x200B;を選択します。
1. 右側のパネルで、**[!UICONTROL 現在のPOI]**&#x200B;を選択すると、ユーザーが現在配置されているPOIの名前を取得できます。

   **[!UICONTROL Last Entered]**&#x200B;は、ユーザーが最後に入力したPOIの名前を取得し、**[!UICONTROL Last Exited]**&#x200B;は、ユーザーが最後に残したPOIの名前を提供します。 この例では、**[!UICONTROL Last Entered]**&#x200B;を選択し、**[!UICONTROL Last Entered POI Name]**&#x200B;などのデータ要素の名前を入力して、**[!UICONTROL Save]**&#x200B;をクリックしました。

   ![&quot;Campaign Standardでのプッシュメッセージ&quot;](/help/assets/ACS_Push1.png)

1. 上記の手順1～4を繰り返し、*最後に入力したPOIの緯度*、*最後に入力したPOIの経度*、*最後に入力したPOIの半径*&#x200B;のデータ要素を作成します。

Places サービスのデータ要素に加えて、*アプリ ID*&#x200B;と&#x200B;*Experience Cloud ID*&#x200B;のモバイルコアデータ要素を作成してください。

## 位置情報をAdobe Campaign Standardに送信するルールを作成する

Adobe Experience Platform Launchのルールを利用すれば、イベントのトリガーにもとづいて、複雑なマルチソリューションのワークフローを構築できます。 ルールを使用すると、新しいルールを作成したり、既存のルールを変更したり、更新をモバイルアプリケーションに動的にデプロイしたりできます。 次の例では、ユーザーがジオフェンス設定されたPOIにエントリすると、ルールがトリガーされます。 ルールがトリガーされると、更新がCampaign Standardに送信され、Experience Cloud IDに基づいて特定のユーザーの特定のPOIへのエントリを記録します。

1. Experience Platform Launch モバイルプロパティの「**[!UICONTROL ルール]**」タブで、「**[!UICONTROL ルールを追加]**」をクリックします。
1. **[!UICONTROL イベント]** セクションで、**[!UICONTROL +]**&#x200B;をクリックし、拡張機能として&#x200B;**[!UICONTROL Places Service]**&#x200B;を選択します。
1. **[!UICONTROL イベントタイプ]**&#x200B;で、**[!UICONTROL POI]**&#x200B;を入力を選択します。
1. ルールに名前を付けます。例：**ユーザーがPOI**&#x200B;に入力しました。
1. 「**[!UICONTROL 変更を保存]**」をクリックします。
1. 「**[!UICONTROL 条件]**」セクションを空白のままにします。

   このセクションでは、このルールを適用するタイミングをフィルタリングしたり、制限を設定したりできます。

1. **[!UICONTROL アクション]** セクションで、**[!UICONTROL +]**&#x200B;をクリックします。
1. **[!UICONTROL 拡張機能]** ドロップダウンリストで「**[!UICONTROL モバイルコア]**」を選択し、**[!UICONTROL アクションタイプ]** ドロップダウンリストで「**[!UICONTROL Postbackを送信]**」を選択します。
1. **[!UICONTROL URL]**&#x200B;で、Campaign Standardの場所エンドポイントを作成する必要があります。

   URLは`https:///rest/head/mobileAppV5//locations/`に似ています。
   Campaign サーバーとpKey用に以前に作成した正しいデータ要素を使用していることを確認します。

1. ボックスをクリックして投稿本文を追加し、次の内容を送信します。

   ```
   {
    "locationData": {
    "distances": "{%%Last Entered POI Radius%%}",
    "poiLabel": "{%%Last Entered POI Name%%}",
    "latitude": "{%%Last Entered POI Lat%%}",
    "longitude": "{%%Last Entered POI Long%%}",
    "appId": "{%%AppID%%}",
    "marketingCloudId": “{%%ecid%%}”
    }
   }
   ```

1. 前の節で作成したデータ要素を使用してください。
1. 「**[!UICONTROL コンテンツタイプ]**」に、「**[!UICONTROL application/json]**」と入力します。
1. 「**[!UICONTROL 変更を保存]**」をクリックします。

>[!IMPORTANT]
>
>* エントリがトリガーされ、適切なデータが収集されていることを検証するための追加のアクションとして、Slack web フックを設定すると便利です。
>* ルールとすべてのデータ要素が設定の一部としてデプロイされていることを確認するために、アプリに対する最近の変更を忘れずに公開してください。 公開後、モバイルアプリケーションを再度起動して、最新の設定更新を取得します。

## 位置情報を使用したキャンペーンメッセージのターゲティング

Campaignに位置情報が入力されたので、POIをオーディエンスセグメントツールとして使用できます。

1. Adobe Campaign Standard インスタンスで、**[!UICONTROL プッシュ通知の作成]**&#x200B;をクリックします。
1. プッシュ通知タイプで、**[!UICONTROL キャンペーンプロファイルにプッシュを送信]**&#x200B;を選択します。
1. 「**[!UICONTROL 次へ]**」をクリックし、一般的な詳細を入力します。
1. オーディエンス画面で、**[!UICONTROL Count]**&#x200B;をクリックして、プッシュ通知が送信される推定ユーザー数を決定します。

   >[!TIP]
   >
   >この例では、アプリケーションがテストされている3つのインストール済みデバイスがあるので、カウントは3になります。

1. 左側のペインで、**[!UICONTROL プロファイル]** タブを展開し、**[!UICONTROL POIの場所]** フィルターをメイン領域にドラッグします。
1. POI フィルターウィンドウで、ターゲットにするPOIの正確な名前を入力します。

   >[!TIP]
   >
   >ユーザーが前回このPOIにアクセスしてから時間を決定するために、追加の選択を行うことができます。

   ![ 「ACSのプッシュメッセージ 2」 ](/help/assets/ACS_push2.png)

1. 「**[!UICONTROL 確認]**」をクリックします。
1. 上部で再度カウントを実行して、オーディエンスサイズの変更を確認します。

   カウントの更新が表示されない場合は、エントリをトリガーしたデバイスがないPOI名を入力した可能性があります。 この状況では、さまざまなテストデバイスからのPOI エントリのリストが表示されるため、Slack web フックを持つことは価値があります。

1. 追加のPOI場所フィルターをドラッグして、メッセージに複数のPOIを含めることができます。
1. 「**[!UICONTROL 次へ]**」をクリックして、配信用のプッシュ通知の作成を終了します。

   ![&quot;ACSのプッシュメッセージ 3&quot;](/help/assets/ACS_push3.png)

Adobe Campaign StandardでPlaces サービスを使用すると、ジオフェンスの出入りに基づいてメッセージをセグメント化し、ユーザーにターゲティングする強力なツールが得られます。 この統合により、よりパーソナライズされた、コンテキストに沿ったユースケースを構築することができます。
