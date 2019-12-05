---
title: Analyticsリクエストへの場所のコンテキストの追加
description: この節では、Analyticsリクエストに場所のコンテキストを追加する方法について説明します。
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# Analyticsリクエストへの場所のコンテキストの追加 {#run-reports-aa-locserv-data}

>[!IMPORTANT]
>
>このドキュメントでは、アプリケーションにAdobe Placesが実装されていることを前提としています。 Adobe Placesの実装について詳しくは、Places拡張機能を参照 [してください](/help/places-ext-aep-sdks/places-extension/places-extension.md)。

場所が入口イベントと出口イベントを送信した後、エクスペリエンスプラットフォーム起動にルールを作成し、場所のデータをすべてのAdobe Analyticsイベントに添付できます。 このタイプのルールを作成するには、「起動」でプロパティを選択し、次の手順を実行します。

## 1.ルールの作成

1. タブで、をク **[!UICONTROL Rules]** リックしま **[!UICONTROL Create New Rule]**&#x200B;す。

   次の情報に留意してください。
   * このプロパティに対する既存のルールがない場合、ボ **[!UICONTROL Create New Rule]** タンは画面の中央に表示されます。
   * プロパティにルールが含まれ **[!UICONTROL Create New Rule]** ている場合、ボタンは画面の右上に表示されます。

## 2.イベントを選択します。

1. ルールに意味のある名前を付け、ルールのリストで簡単に認識できるようにします。

   この例では、Ruleという名前が付けられていま **[!UICONTROL Attach Places Data to Analytics Track Action Events]**&#x200B;す。

1. セクションの下 **[!UICONTROL Events]** のをクリックしま **[!UICONTROL Add]**&#x200B;す。

1. ドロップダウ **[!UICONTROL Extension]** ンリストから、を選択しま **[!UICONTROL Mobile Core]**&#x200B;す。

1. ドロップダウ **[!UICONTROL Event Type]** ンリストから、を選択しま **[!UICONTROL Track Action]**&#x200B;す。

これで、このルールに含めるトリガーを決定できます。 この例では、トリガーはすべての呼び出しに基づいてい `TrackAction` ます。 イベントを設定したら、をクリックしま **[!UICONTROL Keep Changes]**&#x200B;す。

![「イベントの作成」](/help/assets/ad-setEvent_use-analytics-data.png)


## 3.条件の追加

>[!IMPORTANT]
>
>ルールに条件を追加するには、次の手順を実行します。 それ以外の場合は、以下の「アクシ *ョンの定義* 」の節に進みます。

この例では、AT&amp;T顧客に対してのみルールをトリガーする条件を作成します。

1. セクションの下 **[!UICONTROL Conditions]** のをクリックしま **[!UICONTROL Add]**&#x200B;す。

1. ドロップダウ **[!UICONTROL Extension]** ンリストから「モバイルコア」 **[!UICONTORL を選択します]**。

1. ドロップダウ **[!UICONTROL Condition Type]** ンリストから、を選択しま **[!UICONTROL Carrier Name]**&#x200B;す。

1. 右側のウィンドウで、チェックボックスを選択 **[!UICONTROL AT&T]** します。

1. 「**[!UICONTROL Keep Changes]**」をクリックします。

!["条件の作成"](/help/assets/ad-setCondition_use-analytics-data.png)

## 4.アクションの定義

1. セクションの下 **[!UICONTROL Actions]** のをクリックしま **[!UICONTROL Add]**&#x200B;す。

1. ドロップダウ **[!UICONTROL Extension]** ンリストから、を選択しま **[!UICONTROL Mobile Core]**&#x200B;す。

1. ドロップダウ **[!UICONTROL Action Type]** ンリストから、を選択しま **[!UICONTROL Attach Data]**&#x200B;す。

1. 右側のウィンドウのフィールド **[!UICONTROL JSON Payload]** に、このイベントに追加するデータを入力します。

1. 「**[!UICONTROL Keep Changes]**」をクリックします。

右側のウィンドウで、このイベントをリッスンする拡張がイベントを受け取る前に、SDKイベントにデータを追加するフリーフォームJSONペイロードを追加できます。 この例では、Analytics拡張で処理される前に、このイベントに一部のコンテキストデータが追加されます。 追加されたコンテキストデータは、送信Analyticsヒットに置かれます。

次の例では、との値 `poi.city` がAnalyticsイ `poi.name` ベントのコンテキストデータに追加されます。 新しいキーの値は、このイベントが処理されるときにSDKによって動的に決定されます。

![「アクションの作成」](/help/assets/ad-setAction_use-analytics-data.png)

## 5.ルールを保存し、プロパティを再構築します

設定が完了したら、ルールが次の画像のようになっていることを確認します。

![「ルールは完了です。」](/help/assets/ad-ruleComplete_use-analytics-data.png)

1. 「**[!UICONTROL Save]**」をクリックします

1. 起動プロパティを再構築し、正しい環境に展開します。
