---
title: Places Service でのプッシュ通知
description: この節では、Campaign Standardでプッシュ通知を使用して Places Service を設定する方法について説明します。
exl-id: 4b50f552-deb8-49cd-9221-fbbf33aaa5f9
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 2%

---

# Places Service でのプッシュ通知 {#push-notifications}

この節では、過去の位置情報を使用して、Adobe Campaign Standardを通じて配信されるプッシュ通知をターゲットにする方法を説明します。

## 前提条件

開始する前に、次のタスクを完了してください。

* モバイルアプリケーションを、[Adobe Campaign Standard extension](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) を含むAdobe Experience Platform Mobile SDK で設定します。

* [Adobe Experience Platform Mobile SDK](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) をアプリに組み込みます。
* [Adobe Campaign Standard拡張機能 &#x200B;](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) をモバイルアプリ設定に追加します。

* Places Service POI 管理インターフェイスでの [POI の作成 &#x200B;](/help/poi-mgmt-ui/create-a-poi-ui.md)。

* [Places 拡張機能 &#x200B;](/help/places-ext-aep-sdks/places-extension/places-extension.md) を有効にしてインストールします。


## Experience Platform Launchでのデータ要素の作成

アプリケーションで Places 拡張機能と地域モニタリングソリューション（[CoreLocation ドキュメント &#x200B;](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions)for iOS、または [Android location ドキュメント &#x200B;](https://developer.android.com/training/location/geofencing)）が正しく動作していることを確認したら、Experience Platform Launchでデータ要素を作成する必要があります。 データ要素を使用すると、Mobile SDK イベントハブを通じて拡張機能から提供された情報を読み取り、クライアントアプリケーションからデータを取得するためのエイリアスとして機能できます。 Places 拡張機能からデータを取得し、Places Service 情報を Campaign に送信するには、いくつかのデータ要素を作成する必要があります。

データ要素を作成するには：

1. Experience Platform Launchモバイルプロパティで、「**[!UICONTROL データ要素]**」タブをクリックし、「**[!UICONTROL データ要素を追加]**」をクリックします。
1. **[!UICONTROL 拡張機能]** ドロップダウンリストで、「**[!UICONTROL Places Service]**」を選択します。
1. **[!UICONTROL データ要素タイプ]** ドロップダウンリストから、「**[!UICONTROL 名前]**」を選択します。
1. 右側のパネルで「**[!UICONTROL 現在の POI]**」を選択すると、現在ユーザーが配置されている POI の名前が取得されます。

   **[!UICONTROL 最終入力済み]** ユーザーが最後に入力した POI の名前を取得し、**[!UICONTROL 最終離脱済み]** ユーザーが最後に残した POI の名前を提供します。 この例では、「最終入力 **[!UICONTROL を選択し、]** 最終入力 POI 名 **&#x200B;**&#x200B;などのデータ要素の名前を入力して **[!UICONTROL 保存]** をクリックしました。

   ![&#x200B; 「Campaign Standardでのプッシュメッセージ」 &#x200B;](/help/assets/ACS_Push1.png)

1. 上記の手順 1～4 を繰り返し、*最終入力 POI 緯度*、*最終入力 POI 経度*、および *最終入力 POI 半径* のデータ要素を作成します。

Places Service のデータ要素に加えて、{ アプリ ID *と* 2}Experience CloudID *に Mobile Core データ要素を作成していることを確認してください。*

## 場所データをAdobe Campaign Standardに送信するルールを作成する

Experience Platform Launchのルールを使用すると、イベントトリガーに基づいて複雑なマルチソリューションワークフローを作成できます。 ルールを使用すると、新しいルールを作成したり、既存のルールを変更したり、モバイルアプリケーションに更新を動的にデプロイしたりできます。 次の例では、ユーザーが地域ごとに囲まれた POI に入るとルールがトリガーされます。 ルールがトリガーされると、更新がCampaign Standardに送信され、Experience Cloud ID に基づいて、特定のユーザーの特定の POI へのエントリが記録されます。

1. Experience Platform Launchモバイルプロパティの「**[!UICONTROL ルール]**」タブで、「**[!UICONTROL ルールを追加]**」をクリックします。
1. 「**[!UICONTROL イベント]**」セクションで、「**[!UICONTROL +]**」をクリックし、拡張機能として **[!UICONTROL Places Service]** を選択します。
1. **[!UICONTROL イベントタイプ]** で、「**[!UICONTROL POI を入力]**」を選択します。
1. ルールに名前を付けます（例：**ユーザーが POI を入力**）。
1. 「**[!UICONTROL 変更を保存]**」をクリックします。
1. 「**[!UICONTROL 条件]**」セクションは空白のままにします。

   このセクションでは、このルールを実行するタイミングをフィルタリングまたは制限できます。

1. 「**[!UICONTROL アクション]**」セクションで、「**[!UICONTROL +]**」をクリックします。
1. 「**[!UICONTROL 拡張機能]**」ドロップダウンリストで「**[!UICONTROL Mobile Core]**」を選択し、「**[!UICONTROL アクションタイプ]**」ドロップダウンリストで「**[!UICONTROL ポストバックを送信]**」を選択します。
1. **[!UICONTROL URL]** では、Campaign Standard場所エンドポイントを作成する必要があります。

   URL は `https:///rest/head/mobileAppV5//locations/` のようになります。
Campaign サーバーと pKey に、以前に作成した正しいデータ要素を使用していることを確認してください。

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

1. 前の節で作成したデータ要素を使用していることを確認してください。
1. 「**[!UICONTROL コンテンツタイプ]**」に、「**[!UICONTROL application/json]**」と入力します。
1. 「**[!UICONTROL 変更を保存]**」をクリックします。

>[!IMPORTANT]
>
>* エントリがトリガーされ、適切なデータが収集されていることを検証する追加のアクションとして、Slackの Web フックを設定すると役立つ場合があります。
>* 最近の変更をアプリに公開し、ルールとすべてのデータ要素が設定の一部としてデプロイされていることを確認します。 公開したら、モバイルアプリケーションを再度起動して、最新の設定アップデートを取得します。

## 場所データを使用した Campaign メッセージのターゲティング

Campaign に場所データが入力されたので、POI をオーディエンスセグメントツールとして使用できます。

1. Adobe Campaign Standard インスタンスで、「**[!UICONTROL プッシュ通知を作成]**」をクリックします。
1. プッシュ通知タイプの場合は、「**[!UICONTROL キャンペーンプロファイルにプッシュを送信]**」を選択します。
1. **[!UICONTROL 次へ]** をクリックして、一般的な詳細を入力します。
1. オーディエンス画面で **[!UICONTROL カウント]** をクリックして、プッシュ通知が送信される推定ユーザー数を決定します。

   >[!TIP]
   >
   >この例では、アプリケーションがテストされるデバイスが 3 つあるため、カウントは 3 になります。

1. 左側のペインで、「**[!UICONTROL プロファイル]**」タブを展開し、「**[!UICONTROL POI の場所]** フィルターをメイン領域にドラッグします。
1. POI フィルターウィンドウで、ターゲットにする POI の正確な名前を入力します。

   >[!TIP]
   >
   >ユーザーが前回この POI を訪問してからの経過時間を指定するために、追加の選択を行うことができます。

   ![&#x200B; 「ACS のプッシュメッセージ 2」 &#x200B;](/help/assets/ACS_push2.png)

1. 「**[!UICONTROL 確認]**」をクリックします。
1. 上部のカウントを再度実行して、オーディエンスサイズの変化を確認します。

   カウントの更新が表示されない場合は、デバイスがエントリをトリガーしていない POI 名を入力した可能性があります。 この状況では、様々なテストデバイスからの POI エントリのリストを確認できるので、Slackの Web フックを使用すると便利です。

1. 追加の POI 場所フィルターをドラッグして、メッセージに複数の POI を含めることができます。
1. 「**[!UICONTROL 次へ]**」をクリックして、配信用のプッシュ通知の作成を終了します。

   ![&#x200B; 「ACS のプッシュメッセージ 3」 &#x200B;](/help/assets/ACS_push3.png)

Adobe Campaign Standardで Places Service を使用すると、ジオフェンスの入口と出口に基づいてメッセージをセグメント化し、ユーザーをターゲットにする強力なツールを利用できます。 この統合により、よりパーソナライズされたコンテキストに沿ったユースケースを作成できます。
