---
title: Placesサービスでのプッシュ通知
description: この節では、Places ServiceをCampaign Standardでプッシュ通知と共に使用する方法について説明します。
translation-type: tm+mt
source-git-commit: fd469358845e14c47a58b40bb18c9144828a8996
workflow-type: tm+mt
source-wordcount: '911'
ht-degree: 1%

---


# Placesサービスでのプッシュ通知 {#push-notifications}

この節では、過去の地域情報を使用して、Adobe Campaign Standard経由で配信されるターゲットのプッシュ通知を行う方法について説明します。

## 前提条件

開始する前に、次のタスクを実行します。

* Adobe Experience PlatformモバイルSDKを使用して設定したモバイルアプリケーション( [Adobe Campaign Standard拡張を含む](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard))がある。

* アプリに [Adobe Experience PlatformモバイルSDK](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) を統合します。
* 追加 [](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) Adobe Campaign Standard拡張機能をモバイルアプリ設定に追加します。

* [Places Service POI管理インターフェイスでPOI](/help/poi-mgmt-ui/create-a-poi-ui.md) を作成します。

* Places拡張機能を有効にしてインスト [ールします](/help/places-ext-aep-sdks/places-extension/places-extension.md)。


## Experience Platform Launchでのデータ要素の作成

Places拡張機能とPlaces Monitor拡張機能がアプリケーションで正しく動作していることを確認した後、Experience Platform Launchでデータ要素を作成する必要があります。 データ要素を使用すると、Mobile SDKイベントハブを介して提供される拡張機能から提供される情報を読み取り、クライアントアプリケーションからデータを取得するエイリアスとして機能できます。 Places拡張からデータを取得し、Places Service情報をキャンペーンに送信するには、いくつかのデータ要素を作成する必要があります。

データ要素を作成するには：

1. Experience Platform Launchモバイルプロパティで、 **[!UICONTROL Data Elements]** タブをクリックし、をクリックし **[!UICONTROL Add Data Element]**&#x200B;ます。
1. In the **[!UICONTROL Extension]** drop-down list, select **[!UICONTROL Places Service]**.
1. ドロップダウン **[!UICONTROL Data Element Type]** リストで、を選択し **[!UICONTROL Name]**&#x200B;ます。
1. 右側のウィンドウで、ユーザーが現在いるPOIの名前を取得 **[!UICONTROL Current POI]** するかどうかを選択できます。

   **[!UICONTROL Last Entered]** ユーザーが最後に入力したPOIの名前を取得し、ユーザーが最後に退出したPOIの名前を **[!UICONTROL Last Exited]** 入力します。 この例では、データ要素の名前(例：「 **[!UICONTROL Last Entered]** and clicked」)を選択 **[!UICONTROL Last Entered POI Name]** し、入力しました **[!UICONTROL Save]**。

   ![&quot;Campaign Standard内のプッシュメッセージ&quot;](/help/assets/ACS_Push1.png)

1. Repeat the steps 1-4 above and create data elements for *Last Entered POI Latitude*, *Last Entered POI Longitude*, and *Last Entered POI Radius*.

Places Serviceのデータ要素に加えて、 *App IDと* Experience CloudIDのMobile Coreデータ要素を作成します **。

## 場所のデータをAdobe Campaign Standardに送信するルールを作成する

Experience Platform Launch内のルールを使用すると、イベントトリガーに基づいて複雑なマルチソリューションワークフローを作成できます。 ルールを使用すると、新しいルールを作成したり、既存のルールを変更したりできます。また、モバイルアプリケーションに更新を動的にデプロイすることもできます。 次の例では、ユーザーが地域フェンスのPOIに入るとルールがトリガーされます。 ルールがトリガーされた後、Campaign Standardに更新が送信され、Experience CloudIDに基づいて、特定のユーザーの特定のPOIへのエントリを記録します。

1. Experience Platform Launchモバイルプロパティの **[!UICONTROL Rules]** タブで、をクリックし **[!UICONTROL Add Rule]**&#x200B;ます。
1. セクションの下で、をクリック **[!UICONTROL Events]** し、拡張子 **[!UICONTROL +]****[!UICONTROL Places Service]** として選択します。
1. For the **[!UICONTROL Event Type]**, select **[!UICONTROL Enter POI]**.
1. ルールに名前を付けます(例： **ユーザー入力POI**)。
1. 「**[!UICONTROL Keep Changes]**」をクリックします。
1. セクションは空白のままにし **[!UICONTROL Conditions]** てください。

   このセクションでは、このルールをいつ実行するかをフィルターまたは制限できます。

1. Under the **[!UICONTROL Actions]** section, click **[!UICONTROL +]**.
1. ドロップダウン **[!UICONTROL Extension]** リストでを選択し、ドロップダウンリスト **[!UICONTROL Mobile Core]** で **[!UICONTROL Action Type]** を選択し **[!UICONTROL Send Postback]**&#x200B;ます。
1. では、Campaign Standard **[!UICONTROL URL]**&#x200B;の場所のエンドポイントを作成する必要があります。

   URLは、のようになり `https:///rest/head/mobileAppV5//locations/`ます。
キャンペーンサーバーおよびpKey用に以前に作成した正しいデータ要素を使用していることを確認します。

1. ボックスをクリックして投稿の本文を追加し、次の内容を送信します。

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

1. 前の節で作成したデータ要素を使用していることを確認します。
1. に、 **[!UICONTROL Content Type]**&#x200B;と入力し **[!UICONTROL application/json]**&#x200B;ます。
1. 「**[!UICONTROL Keep Changes]**」をクリックします。

>[!IMPORTANT]
>
>* SlackWebフックを追加のアクションとして設定して、エントリがトリガーされていて、適切なデータが収集されていることを検証すると便利です。
>* 最近の変更をアプリに公開して、ルールとすべてのデータ要素が設定の一部としてデプロイされていることを確認してください。 公開した後、モバイルアプリケーションを再起動して、最新の設定の更新を取得します。


## 場所データを使用したターゲットキャンペーンメッセージ

キャンペーンに場所のデータが入力されたので、POIをオーディエンスセグメントツールとして使用できます。

1. Adobe Campaign Standardインスタンスで、をクリックし **[!UICONTROL Create Push Notification]**&#x200B;ます。
1. プッシュ通知タイプに対して、を選択し **[!UICONTROL Send push to Campaign profiles]**&#x200B;ます。
1. をクリック **[!UICONTROL Next]** し、一般的な詳細を入力します。
1. オーディエンス画面で、をクリックし **[!UICONTROL Count]** て、プッシュ通知を送信する推定ユーザー数を指定します。

   >[!TIP]
   >
   >この例では、アプリケーションがテストされる3台のインストール済みデバイスがあるので、カウントは3になります。

1. 左側のペインで、 **[!UICONTROL Profile]** タブを展開し、 **[!UICONTROL POI location]** フィルターをメイン領域にドラッグします。
1. POIフィルタウィンドウで、ターゲットするPOIの正確な名前を入力します。

   >[!TIP]
   >
   >このPOIに対して、ユーザーが以前に訪問してからの期間を指定することもできます。

   ![&quot;ACSでのプッシュメッセージ2&quot;](/help/assets/ACS_push2.png)

1. 「**[!UICONTROL Confirm]**」をクリックします。
1. 上部でカウントを再度実行して、オーディエンスのサイズ変更を確認します。

   カウントの更新が表示されない場合は、エントリをトリガーしたデバイスがないPOI名を入力した可能性があります。 様々なテストデバイスからのPOIエントリの一覧が見られるので、この状況ではSlackWebフックを持つことは有用です。

1. 追加のPOI位置フィルターーをドラッグして、メッセージに複数のPOIを含めることができます。
1. Click **[!UICONTROL Next]** to finish creating the push notification for delivery.

   ![&quot;ACSでのプッシュメッセージ3&quot;](/help/assets/ACS_push3.png)

Places ServiceをAdobe Campaign Standardと共に使用すると、地域フェンスの入口と出口に基づいてユーザーにメッセージを分類し、ターゲットするための強力なツールが提供されます。 この統合により、よりパーソナライズされた状況に応じた使用例を構築できます。