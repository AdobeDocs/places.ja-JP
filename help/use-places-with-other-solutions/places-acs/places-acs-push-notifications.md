---
title: Places Service を使用したプッシュ通知
description: この節では、Places Service をCampaign Standardのプッシュ通知で使用する方法に関する情報を提供します。
exl-id: 4b50f552-deb8-49cd-9221-fbbf33aaa5f9
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '1005'
ht-degree: 3%

---

# Places Service を使用したプッシュ通知 {#push-notifications}

この節では、過去の位置情報情報を使用して、Adobe Campaign Standard経由で配信されるプッシュ通知をターゲットにする方法を学びます。

## 前提条件

開始する前に、次の作業を実行します。

* Adobe Experience Platform Mobile SDK を使用してモバイルアプリケーションを設定し、 [Adobe Campaign Standard拡張機能](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard).

* の統合 [Adobe Experience Platform Mobile SDK](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) をアプリに追加します。
* を [Adobe Campaign Standard Extension](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) をモバイルアプリ設定に追加します。

* [POI の作成](/help/poi-mgmt-ui/create-a-poi-ui.md) （Places Service POI 管理インターフェイス）を参照してください。

* を有効にしてインストールする [Places 拡張機能](/help/places-ext-aep-sdks/places-extension/places-extension.md).


## Experience Platform Launchでのデータ要素の作成

Places 拡張機能と地域監視ソリューション ([CoreLocation ドキュメント](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) (iOSの場合 )、または [Android ロケーションドキュメント](https://developer.android.com/training/location/geofencing)) がアプリケーションで正しく機能している場合は、Experience Platform Launchでデータ要素を作成する必要があります。 データ要素を使用すると、Mobile SDK イベントハブを介して提供される拡張機能によって提供された情報を読み取り、クライアントアプリケーションからデータを取得するエイリアスとしての役割を果たすことができます。 Places 拡張機能からデータを取得して Places サービス情報を Campaign に送信するには、いくつかのデータ要素を作成する必要があります。

データ要素を作成するには：

1. Experience Platform Launchモバイルプロパティで、 **[!UICONTROL データ要素]** タブをクリックし、 **[!UICONTROL データ要素を追加]**.
1. 内 **[!UICONTROL 拡張]** ドロップダウンリストで、「 **[!UICONTROL Places Service]**.
1. 次の **[!UICONTROL データ要素タイプ]** ドロップダウンリストで、「 **[!UICONTROL 名前]**.
1. 右側のウィンドウで、 **[!UICONTROL 現在の POI]** ：ユーザーが現在いる POI の名前を取得します。

   **[!UICONTROL 最終入力日]** ユーザーが最後に入力した POI の名前を取得し、 **[!UICONTROL 前回の終了]** は、ユーザーが最後に出た POI の名前を示します。 この例では、「 **[!UICONTROL 最終入力日]** データ要素の名前を入力します。例： **[!UICONTROL 最後に入力した POI 名]** をクリックし、 **[!UICONTROL 保存]**.

   ![&quot;プッシュメッセージのCampaign Standard&quot;](/help/assets/ACS_Push1.png)

1. 上記の手順 1～4 を繰り返し、 *最後に入った POI の緯度*, *最後に入力した POI の経度*、および *最後に入力した POI 半径*.

Places Service のデータ要素に加えて、用の Mobile コアデータ要素を作成してください *アプリ ID* および *Experience CloudID*.

## ロケーションデータをAdobe Campaign Standardに送信するルールを作成する

Experience Platform Launchのルールを使用すると、イベントワークフローに基づいて、複雑で複数のソリューションから成るトリガーを作成できます。 ルールを使用すると、新しいルールを作成したり、既存のルールを変更したりでき、更新をモバイルアプリケーションに動的にデプロイしたりできます。 次の例では、ユーザーが地域特性 (POI) に入るとルールがトリガーされます。 ルールがトリガーされた後、Campaign Standardに更新が送信され、Experience CloudID に基づいて、特定のユーザーの特定の POI に対するエントリを記録するようになります。

1. Experience Platform Launchのモバイルプロパティで、 **[!UICONTROL ルール]** タブ、クリック **[!UICONTROL ルールを追加]**.
1. 以下 **[!UICONTROL イベント]** セクションで、 **[!UICONTROL +]** を選択し、 **[!UICONTROL Places Service]** を拡張として使用します。
1. の **[!UICONTROL イベントタイプ]**&#x200B;を選択します。 **[!UICONTROL POI を入力]**.
1. ルールに名前を付けます（例： ）。 **ユーザーが POI を入力しました**.
1. 「**[!UICONTROL 変更を保存]**」をクリックします。
1. を **[!UICONTROL 条件]** セクションが空白です。

   このセクションでは、このルールを実行するタイミングをフィルタリングしたり、制限を設定したりできます。

1. 以下 **[!UICONTROL アクション]** セクションで、 **[!UICONTROL +]**.
1. 内 **[!UICONTROL 拡張]** ドロップダウンリストで、「 **[!UICONTROL Mobile Core]** そして **[!UICONTROL アクションタイプ]** ドロップダウンリストで、「 **[!UICONTROL ポストバックを送信]**.
1. In **[!UICONTROL URL]**&#x200B;を使用する場合は、Campaign Standardの場所エンドポイントを作成する必要があります。

   URL は次のようになります。 `https:///rest/head/mobileAppV5//locations/`.
Campaign サーバーおよび pKey 用に以前に作成した正しいデータ要素を使用していることを確認します。

1. ボックスをクリックして、投稿の本文を追加し、以下を送信します。

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
1. 「**[!UICONTROL コンテンツタイプ]**」に、「**[!UICONTROL application/json]**」と入力します。
1. 「**[!UICONTROL 変更を保存]**」をクリックします。

>[!IMPORTANT]
>
>* エントリがトリガーされ、適切なデータが収集されていることを検証する追加のアクションとして、Slackの Web フックを設定すると便利です。
>* アプリに最近の変更を公開して、ルールとすべてのデータ要素が設定の一部としてデプロイされていることを確認してください。 公開した後、モバイルアプリケーションを再度起動して、最新の設定の更新を取得します。


## 場所データを使用したキャンペーンメッセージのターゲット設定

これで、Campaign に場所データが入力され、POI をオーディエンスセグメントツールとして使用できます。

1. Adobe Campaign Standardインスタンスで、 **[!UICONTROL プッシュ通知を作成]**.
1. プッシュ通知タイプで、「 」を選択します。 **[!UICONTROL Campaign プロファイルにプッシュを送信]**.
1. クリック **[!UICONTROL 次へ]** および一般的な詳細を入力します。
1. オーディエンス画面で、 **[!UICONTROL カウント]** を使用して、プッシュ通知を送信する推定ユーザー数を決定します。

   >[!TIP]
   >
   >この例では、アプリケーションがテストされる 3 台のインストール済みデバイスがあるので、カウントは 3 になります。

1. 左側のウィンドウで、を展開します。 **[!UICONTROL プロファイル]** タブをクリックし、 **[!UICONTROL POI の場所]** をメイン領域にフィルターします。
1. POI フィルターウィンドウで、ターゲットにする POI の正確な名前を入力します。

   >[!TIP]
   >
   >追加の選択を行って、ユーザーがこの POI を以前に訪問してからの期間を決定できます。

   ![「ACS でのプッシュメッセージ 2」](/help/assets/ACS_push2.png)

1. 「**[!UICONTROL 確認]**」をクリックします。
1. 上部のカウントを再度実行して、オーディエンスサイズの変更を確認します。

   カウントの更新が表示されない場合は、エントリをトリガーしたデバイスがない POI 名を入力している可能性があります。 SlackWeb フックを持つと、様々なテストデバイスからの POI エントリのリストが表示されるので、この状況で役立ちます。

1. 追加の POI 位置フィルターをドラッグして、メッセージに複数の POI を含めることができます。
1. 「**[!UICONTROL 次へ]**」をクリックして、配信用のプッシュ通知の作成を終了します。

   ![「ACS でのプッシュメッセージ 3」](/help/assets/ACS_push3.png)

Adobe Campaign Standardで Places Service を使用すると、ジオフェンスの入口と出口に基づいてメッセージをセグメント化し、ユーザーにターゲティングするための強力なツールが得られます。 この統合により、よりパーソナライズされたコンテキストに基づくユースケースを構築できます。
