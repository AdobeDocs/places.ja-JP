---
title: Analytics リクエストへの場所コンテキストの追加
description: この節では、Analytics リクエストに位置情報を追加する方法について説明します。
exl-id: bee7b6e3-a75b-4a07-b6e2-f93ce33aa042
TQID: https://experienceleague.adobe.com/NR-CowJgzUBMVWcbV-EvdyBDsiwLi72yxM-Vjx5oNwk
product_v2: id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: e55547f1-a1ff-40c6-8978-026e40ab7fa4id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2: id: b069d60e-95f3-44d6-95a8-ddc862a4bc38id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2: id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2: id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 512
ht-degree: 3%

---

# Analytics リクエストへの場所コンテキストの追加 {#run-reports-aa-locserv-data}

>[!IMPORTANT]
>
>このドキュメントでは、アプリケーションにPlaces サービスが実装されていることを前提としています。 Places サービスの実装について詳しくは、[Places拡張機能](/help/places-ext-aep-sdks/places-extension/places-extension.md)を参照してください。

Places サービスが入口イベントと出口イベントを送信した後、Experience Platform Launchでルールを作成し、Places サービスデータをすべてのAdobe Analytics イベントに添付できます。 このタイプのルールを作成するには、Launchでプロパティを選択し、次の手順を実行します。

## &#x200B;1. ルールの作成

1. 「**[!UICONTROL ルール]**」タブで、**[!UICONTROL 新しいルールを作成]**&#x200B;をクリックします。

   次の情報に留意してください。
   * このプロパティに既存のルールがない場合は、**[!UICONTROL 新しいルールを作成]** ボタンが画面の中央に表示されます。
   * プロパティにルールがある場合は、画面の右上に「**[!UICONTROL 新しいルールを作成]**」ボタンが表示されます。

## &#x200B;2. イベントの選択

1. ルールに意味のある名前を付けると、ルールのリストで簡単に認識できます。

   この例では、ルールの名前は&#x200B;**[!UICONTROL 場所サービスデータをAnalytics トラックアクションイベントに添付]**&#x200B;です。

1. **[!UICONTROL イベント]** セクションで、**[!UICONTROL 追加]**&#x200B;をクリックします。

1. **[!UICONTROL 拡張機能]** ドロップダウンリストから、**[!UICONTROL モバイルコア]**&#x200B;を選択します。

1. 「**[!UICONTROL イベントタイプ]**」ドロップダウンリストから、「**[!UICONTROL アクションを追跡]**」を選択します。

これで、このルールに含めるトリガーを決定できます。 この例では、すべての`TrackAction`呼び出しに基づいてトリガーが行われています。 イベントを設定したら、**[!UICONTROL 変更を保持]**&#x200B;をクリックします。

![&quot;イベントを作成&quot;](/help/assets/ad-setEvent_use-analytics-data.png)


## &#x200B;3. 条件を追加

>[!IMPORTANT]
>
>ルールに条件を追加するには、次の手順を実行します。 それ以外は、以下の「*アクションを定義*」セクションにスキップしてください。

この例では、AT&amp;Tのお客様に対してのみルールをトリガーにする条件が作成されます。

1. **[!UICONTROL 条件]** セクションで、**[!UICONTROL 追加]**&#x200B;をクリックします。

1. **[!UICONTROL 拡張機能]** ドロップダウンリストから、**[!UICONTROL モバイルコア]**&#x200B;を選択します。

1. **[!UICONTROL 条件タイプ]** ドロップダウンリストから、**[!UICONTROL キャリア名]**&#x200B;を選択します。

1. 右側のウィンドウで、**[!UICONTROL AT&amp;T]** チェックボックスを選択します。

1. 「**[!UICONTROL 変更を保存]**」をクリックします。

![&quot;条件を作成&quot;](/help/assets/ad-setCondition_use-analytics-data.png)

## &#x200B;4. アクションを定義

1. 「**[!UICONTROL アクション]**」セクションで、**[!UICONTROL 追加]**&#x200B;をクリックします。

1. **[!UICONTROL 拡張機能]** ドロップダウンリストから、**[!UICONTROL モバイルコア]**&#x200B;を選択します。

1. 「**[!UICONTROL アクションタイプ]**」ドロップダウンリストから、「**[!UICONTROL データを添付]**」を選択します。

1. 右側のペインの&#x200B;**[!UICONTROL JSON ペイロード]** フィールドに、このイベントに追加するデータを入力します。

1. 「**[!UICONTROL 変更を保存]**」をクリックします。

右側のペインでは、このイベントをリッスンしている拡張機能がイベントをリッスンする前に、SDK イベントにデータを追加するフリーフォーム JSON ペイロードを追加できます。 この例では、Analytics拡張機能が処理する前に、一部のコンテキストデータがこのイベントに追加されます。 追加されたコンテキストデータは、Analyticsの送信ヒットに表示されます。

次の例では、`poi.city`と`poi.name`の値がAnalytics イベントのコンテキストデータに追加されています。 新しいキーの値は、このイベントの処理時にSDKによって動的に決定されます。

![&quot;アクションを作成&quot;](/help/assets/ad-setAction_use-analytics-data.png)

## &#x200B;5. ルールを保存してプロパティを再構築する

設定が完了したら、ルールが次の画像のようになっていることを確認します。

![ 「ルールは完了しました。」 ](/help/assets/ad-ruleComplete_use-analytics-data.png)

1. 「**[!UICONTROL 保存]**」をクリックします。

1. Launch プロパティを再構築し、正しい環境にデプロイします。
