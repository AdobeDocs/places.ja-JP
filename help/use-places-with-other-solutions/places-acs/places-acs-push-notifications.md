---
title: Placesサービスでのプッシュ通知
description: この節では、Places ServiceをCampaign Standardでプッシュ通知と共に使用する方法について説明します。
translation-type: tm+mt
source-git-commit: fd469358845e14c47a58b40bb18c9144828a8996
workflow-type: tm+mt
source-wordcount: '979'
ht-degree: 3%

---


# Placesサービスを使用したプッシュ通知{#push-notifications}

この節では、過去の地域情報を使用して、Adobe Campaign Standard経由で配信されるターゲットのプッシュ通知を行う方法について説明します。

## 前提条件

開始する前に、次のタスクを実行します。

* [Adobe Campaign Standard拡張子](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)を含む、Adobe Experience PlatformモバイルSDKを使用してモバイルアプリを設定します。

* [Adobe Experience PlatformモバイルSDK](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk)をアプリに統合します。
* モバ追加イルアプリ設定の[Adobe Campaign Standard拡張機能](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)。

* [Places Service POI管理インターフェイスで](/help/poi-mgmt-ui/create-a-poi-ui.md) POIを作成します。

* [場所の拡張子](/help/places-ext-aep-sdks/places-extension/places-extension.md)を有効にしてインストールします。


## Experience Platform Launchでのデータ要素の作成

Places拡張機能とPlaces Monitor拡張機能がアプリケーションで正しく動作していることを確認した後、Experience Platform Launchでデータ要素を作成する必要があります。 データ要素を使用すると、Mobile SDKイベントハブを介して提供される拡張機能から提供される情報を読み取り、クライアントアプリケーションからデータを取得するエイリアスとして機能できます。 Places拡張からデータを取得し、Places Service情報をキャンペーンに送信するには、いくつかのデータ要素を作成する必要があります。

データ要素を作成するには：

1. Experience Platform Launchのモバイルプロパティで、「**[!UICONTROL データ要素]**」タブをクリックし、「**[!UICONTROL データ要素追加]**」をクリックします。
1. **[!UICONTROL 拡張機能]**&#x200B;ドロップダウンリストで、「**[!UICONTROL サービスを配置]**」を選択します。
1. 「**[!UICONTROL データ要素タイプ]**」ドロップダウンリストから、「**[!UICONTROL 名前]**」を選択します。
1. 右側のウィンドウで、「**[!UICONTROL 現在のPOI]**」を選択して、ユーザーが現在配置されているPOIの名前を取得できます。

   **[!UICONTROL Last]** Enterrievesは、ユーザーが最後に入力したPOIの名前を取得し、 **[!UICONTROL Last]** Exitedは、ユーザーが最後に残したPOIの名前を提供します。この例では、「**[!UICONTROL 最後に入力した値]**」を選択し、データ要素の名前を入力しました（例：**[!UICONTROL 最後に入力したPOI名]**）。「**[!UICONTROL 保存]**」をクリックしました。

   ![&quot;Campaign Standard内のプッシュメッセージ&quot;](/help/assets/ACS_Push1.png)

1. 上記の手順1 ～ 4を繰り返し、*最後に入力したPOI緯度*、*最後に入力したPOI経度*、*最後に入力したPOI半径*&#x200B;のデータ要素を作成します。

Places Serviceのデータ要素に加えて、*App ID*&#x200B;および&#x200B;*Experience CloudID*&#x200B;用のMobile Coreデータ要素を作成します。

## 場所のデータをAdobe Campaign Standardに送信するルールを作成する

Experience Platform Launch内のルールを使用すると、イベントのトリガーに基づいて複雑で複数のソリューションのワークフローを作成できます。 ルールを使用すると、新しいルールを作成したり、既存のルールを変更したりできます。また、モバイルアプリケーションに更新を動的にデプロイすることもできます。 次の例では、ユーザーが地域フェンスのPOIに入るとルールがトリガーされます。 ルールがトリガーされた後、Campaign Standardに更新が送信され、Experience CloudIDに基づいて、特定のユーザーの特定のPOIへのエントリを記録します。

1. Experience Platform Launchのモバイルプロパティの「**[!UICONTROL ルール]**」タブで、「**[!UICONTROL ルール]**」追加をクリックします。
1. 「**[!UICONTROL イベント]**」セクションで、「**[!UICONTROL +]**」をクリックし、「**[!UICONTROL サービス]**&#x200B;を拡張子として配置」を選択します。
1. **[!UICONTROL イベントタイプ]**&#x200B;に対して、**[!UICONTROL POIを入力]**&#x200B;を選択します。
1. ルールに名前を付けます（例：**ユーザーがPOI**&#x200B;を入力した）。
1. 「**[!UICONTROL 変更を保存]**」をクリックします。
1. 「**[!UICONTROL 条件]**」セクションは空白のままにします。

   このセクションでは、このルールをいつ実行するかをフィルターまたは制限できます。

1. 「**[!UICONTROL アクション]**」セクションで、「**[!UICONTROL +]**」をクリックします。
1. 「**[!UICONTROL 拡張機能]**」ドロップダウンリストで「**[!UICONTROL モバイルコア]**」を選択し、「**[!UICONTROL アクションタイプ]**」ドロップダウンリストで「**[!UICONTROL ポストバックを送信]**」を選択します。
1. **[!UICONTROL URL]**&#x200B;で、Campaign Standardの場所のエンドポイントを作成する必要があります。

   URLは`https:///rest/head/mobileAppV5//locations/`のようになります。
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
1. 「**[!UICONTROL コンテンツタイプ]**」に、「**[!UICONTROL application/json]**」と入力します。
1. 「**[!UICONTROL 変更を保存]**」をクリックします。

>[!IMPORTANT]
>
>* SlackWebフックを追加のアクションとして設定して、エントリがトリガーされていて、適切なデータが収集されていることを検証すると便利です。
>* 最近の変更をアプリに公開して、ルールとすべてのデータ要素が設定の一部としてデプロイされていることを確認してください。 公開した後、モバイルアプリケーションを再起動して、最新の設定の更新を取得します。


## 場所データを使用したターゲットキャンペーンメッセージ

キャンペーンに場所のデータが入力されたので、POIをオーディエンスセグメントツールとして使用できます。

1. Adobe Campaign Standardインスタンスで、「**[!UICONTROL プッシュ通知を作成]**」をクリックします。
1. プッシュ通知タイプとして、「**[!UICONTROL キャンペーンプロファイルにプッシュを送信]**」を選択します。
1. 「**[!UICONTROL 次へ]**」をクリックし、一般的な詳細を入力します。
1. オーディエンス画面で、「**[!UICONTROL カウント]**」をクリックして、プッシュ通知を送信する推定ユーザー数を指定します。

   >[!TIP]
   >
   >この例では、アプリケーションがテストされる3台のインストール済みデバイスがあるので、カウントは3になります。

1. 左側のウィンドウで、「**[!UICONTROL プロファイル]**」タブを展開し、**[!UICONTROL POI位置]**&#x200B;フィルターをメイン領域にドラッグします。
1. POIフィルタウィンドウで、ターゲットするPOIの正確な名前を入力します。

   >[!TIP]
   >
   >このPOIに対して、ユーザーが以前に訪問してからの期間を指定することもできます。

   ![&quot;ACSでのプッシュメッセージ2&quot;](/help/assets/ACS_push2.png)

1. 「**[!UICONTROL 確認]**」をクリックします。
1. 上部でカウントを再度実行して、オーディエンスのサイズ変更を確認します。

   カウントの更新が表示されない場合は、エントリをトリガーしたデバイスがないPOI名を入力した可能性があります。 様々なテストデバイスからのPOIエントリの一覧が見られるので、この状況ではSlackWebフックを持つことは有用です。

1. 追加のPOI位置フィルターーをドラッグして、メッセージに複数のPOIを含めることができます。
1. 「**[!UICONTROL 次へ]**」をクリックして、配信用のプッシュ通知の作成を終了します。

   ![&quot;ACSでのプッシュメッセージ3&quot;](/help/assets/ACS_push3.png)

Places ServiceをAdobe Campaign Standardと共に使用すると、地域フェンスの入口と出口に基づいてユーザーにメッセージを分類し、ターゲットするための強力なツールが提供されます。 この統合により、よりパーソナライズされた状況に応じた使用例を構築できます。