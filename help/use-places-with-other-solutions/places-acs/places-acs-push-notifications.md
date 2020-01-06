---
title: プッシュ通知
description: ここでは、Campaign Standardで場所をプッシュ通知と共に使用する方法について説明します。
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# ロケーションサービスでのプッシュ通知 {#push-notifications}

このガイドでは、Adobe Campaign Standardを通じて配信されるプッシュ通知をターゲットにする、過去の地域情報を使用する方法を説明します。

## 前提条件

開始する前に、次のタスクを実行します。

* Adobe Campaign Standard拡張機能を含む、Adobe Experience Platform Mobile SDKを使用して設定したモバイルアプリ [ケーションがある](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)。

* Adobe Experience Platform Mobile SDK [をアプリに統合します](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) 。
* モバイルア [プリ設定に](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) Adobe Campaign Standard Extensionを追加します。

* [場所POI管理インターフェイスで](/help/poi-mgmt-ui/create-a-poi-ui.md) 、POIを作成します。

* Places拡張機能を有効にしてインス [トールします](/help/places-ext-aep-sdks/places-extension/places-extension.md)。


## エクスペリエンスプラットフォームの起動でのデータ要素の作成

ロケーションサービス拡張の場所と場所モニターがアプリケーションで正しく機能していることを確認したら、Experience Platform Launchでデータ要素を作成します。 データ要素を使用すると、Mobile SDKイベントハブを介して提供される拡張機能によって提供された情報を読み取り、クライアントアプリケーションからデータを取得するエイリアスとして機能できます。 Places拡張機能からデータを取得し、Places情報をCampaignに送信するには、いくつかのデータ要素を作成する必要があります。

データ要素を作成するには：

1. エクスペリエンスプラットフォーム起動モバイルプロパティで、タブをク **[!UICONTROL Data Elements]**リックし、「データ要素を**[!UICONTROLA&#x200B;追加」をクリックしま]**す。
1. ドロップダ **[!UICONTROL Extension]**ウンリストで、を選択しま**[!UICONTROL Places]**&#x200B;す。
1. ドロップダウ **[!UICONTROL Data Element Type]**ンリストから、を選択しま**[!UICONTROL Name]**&#x200B;す。
1. 右側のパネルで、ユーザーが現在い **[!UICONTROL Current POI]**るPOIの名前を取得する対象を選択できます。

   **[!UICONTROL Last Entered]**ユーザーが最後に入力したPOIの名前を取得し、ユ**[!UICONTROL Last Exited]** ーザーが最後に残したPOIの名前を提供します。 この例では、「And Clicked」な **[!UICONTROL Last Entered]**ど、データ要素の名前を選択して入力**[!UICONTROL Last Entered POI Name]** します **[!UICONTROL Save]**。

   ![「キャンペーン標準のプッシュメッセージ」](/help/assets/ACS_Push1.png)

1. Repeat the steps 1-4 above and create data elements for *Last Entered POI Latitude*, *Last Entered POI Longitude*, and *Last Entered POI Radius*.

ロケーションサービスのデータ要素に加えて、 *App IDと* Experience Cloud IDのMobile coreデータ要素を必ず作成し *ます*。

## 場所データをAdobe Campaign Standardに送信するルールの作成

エクスペリエンスプラットフォームの起動のルールを使用すると、イベントトリガーに基づいて複雑なマルチソリューションワークフローを作成できます。 ルールを使用すると、新しいルールを作成したり、既存のルールを変更したり、更新をモバイルアプリケーションに動的にデプロイしたりできます。 次の例では、ユーザーが地域フェンスのPOIに入るとルールがトリガーされます。 ルールがトリガーされると、Experience Cloud IDに基づいて特定のユーザーの特定のPOIへのエントリを記録するように、Campaign Standardに更新が送信されます。

1. モバイルを起動プロパティのタブで、を **[!UICONTROL Rules]**クリックしま**[!UICONTROL Add Rule]**&#x200B;す。
1. セクションの **[!UICONTROL Events]**下でをクリックし、**[!UICONTROL +]** 拡張子と **[!UICONTROL Places]**してを選択します。
1. For the **[!UICONTROL Event Type]**, select**[!UICONTROL Enter POI]**.
1. ルールに名前を付けます。例えば、 **User entered POI**。
1. **[!UICONTROL Keep Changes]**をクリックします。
1. セクションは空 **[!UICONTROL Conditions]**白のままにします。

   このセクションでは、このルールをいつ実行するかをフィルターまたは制限できます。

1. セクションの下 **[!UICONTROL Actions]**のをクリックしま**[!UICONTROL +]**&#x200B;す。
1. ドロップダ **[!UICONTROL Extension]**ウンリストでを選択し、ド**[!UICONTROL Mobile Core]** ロップダウン **[!UICONTROL Action Type]**リストでを選択します**[!UICONTROL Send Postback]**。
1. で、キャン **[!UICONTROL URL]**ペーン標準ロケーションエンドポイントを作成する必要があります。

   URLは、に類似している必要がありま `https:///rest/head/mobileAppV5//locations/`す。
CampaignサーバーおよびpKey用に以前に作成した正しいデータ要素を使用していることを確認します。

1. ボックスをクリックして投稿の本文を追加し、以下を送信します。

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
1. に、と **[!UICONTROL Content Type]**入力しま**[!UICONTROL application/json]**&#x200B;す。
1. **[!UICONTROL Keep Changes]**をクリックします。

>[!IMPORTANT]
>
>* Slack webフックを追加のアクションとして設定すると、エントリがトリガーされ、適切なデータが収集されていることを検証できる場合があります。


>* ルールとすべてのデータ要素が設定の一部としてデプロイされていることを確認するために、アプリに最新の変更を公開してください。 公開後、モバイルアプリケーションを再起動して、最新の設定の更新を取得する必要があります。


## 場所データを使用してキャンペーンメッセージをターゲット設定する

キャンペーンに場所のデータが入力されたので、POIをオーディエンスセグメントツールとして使用できます。

1. Adobe Campaign Standardインスタンスで、をクリックしま **[!UICONTROL Create Push Notification]**す。
1. プッシュ通知タイプに対して、を選択しま **[!UICONTROL Send push to Campaign profiles]**す。
1. をクリ **[!UICONTROL Next]**ックし、一般的な詳細を入力します。
1. オーディエンス画面で、をクリック **[!UICONTROL Count]**して、プッシュ通知を送信する推定ユーザー数を決定します。

   >[!TIP]
   >
   >この例では、アプリケーションのテスト対象となる3台のデバイスがインストールされているので、カウントは3になります。

1. 左側のペインで、タブを展開し、 **[!UICONTROL Profile]**フィルターをメイ**[!UICONTROL POI location]** ン領域にドラッグします。
1. POIフィルタウィンドウで、ターゲットにするPOIの正確な名前を入力します。

   >[!TIP]
   >
   >このPOIへのユーザーの前回の訪問からの期間を指定するには、追加の選択を行います。

   ![&quot;ACSでのプッシュメッセージ2&quot;](/help/assets/ACS_push2.png)

1. **[!UICONTROL Confirm]**をクリックします。
1. 上部でもう一度カウントを実行し、オーディエンスのサイズ変更を確認します。

   カウントの更新が表示されない場合は、エントリをトリガーしたデバイスがないPOI名を入力した可能性があります。 Slack webフックを使用すると、様々なテストデバイスからのPOIエントリのリストが表示されるので、この状況で役に立ちます。
1. 追加のPOI位置フィルターをドラッグして、メッセージに複数のPOIを含めることができます。
1. Click **[!UICONTROL Next]**to finish creating the push notification for delivery.

   ![&quot;ACSでのプッシュメッセージ3&quot;](/help/assets/ACS_push3.html)

Adobe Campaign Standardでロケーションサービスを使用すると、地域フェンスの入口と出口に基づいて、ユーザーに対するメッセージをセグメント化およびターゲット化する強力なツールが提供されます。 この統合により、よりパーソナライズされたコンテキスト的な使用例を構築できます。