---
title: Analytics追加リクエストの場所のコンテキスト
description: この節では、Analyticsリクエストに場所コンテキストを追加する方法について説明します。
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 1%

---


# Analytics追加リクエストの場所のコンテキスト {#run-reports-aa-locserv-data}

>[!IMPORTANT]
>
>このドキュメントは、アプリケーションにPlaces Serviceが実装されていることを前提としています。 Places Serviceの導入について詳しくは、「Places拡張」を参照して [ください](/help/places-ext-aep-sdks/places-extension/places-extension.md)。

Places Serviceが入口イベントと出口イベントを送信した後、Experience Platform Launchでルールを作成し、Places ServiceデータをすべてのAdobe Analyticsに添付できます。 このタイプのルールを作成するには、「起動」でプロパティを選択し、次の手順を実行します。

## 1.ルールを作成する

1. On the **[!UICONTROL Rules]** tab, click **[!UICONTROL Create New Rule]**.

   次の情報に留意してください。
   * このプロパティに対して既存のルールがない場合、 **[!UICONTROL Create New Rule]** ボタンは画面の中央に表示されます。
   * プロパティにルールが含まれている場合、この **[!UICONTROL Create New Rule]** ボタンは画面の右上に表示されます。

## 2.イベントの選択

1. ルールに意味のある名前を付け、ルールのリストで簡単に認識できるようにします。

   この例では、ルールに名前が付けられてい **[!UICONTROL Attach Places Service Data to Analytics Track Action Events]**&#x200B;ます。

1. Under the **[!UICONTROL Events]** section, click **[!UICONTROL Add]**.

1. ドロップダウン **[!UICONTROL Extension]** リストで、を選択し **[!UICONTROL Mobile Core]**&#x200B;ます。

1. ドロップダウン **[!UICONTROL Event Type]** リストで、を選択し **[!UICONTROL Track Action]**&#x200B;ます。

次に、このルールに含めるトリガーを決定します。 この例では、トリガーはすべての `TrackAction` 呼び出しに基づいています。 イベントを設定したら、をクリックし **[!UICONTROL Keep Changes]**&#x200B;ます。

![イベントの作成](/help/assets/ad-setEvent_use-analytics-data.png)


## 3.追加条件

>[!IMPORTANT]
>
>ルールに条件を追加するには、次の手順を実行します。 それ以外の場合は、次の「アクションの *定義* 」の節に進みます。

この例では、AT&amp;Tのお客様に対してのみルールをトリガーする条件を作成します。

1. Under the **[!UICONTROL Conditions]** section, click **[!UICONTROL Add]**.

1. ドロップダウン **[!UICONTROL Extension]** リストで、を選択し **[!UICONTROL Mobile Core]**&#x200B;ます。

1. ドロップダウン **[!UICONTROL Condition Type]** リストで、を選択し **[!UICONTROL Carrier Name]**&#x200B;ます。

1. 右側のウィンドウで、チェックボックスを選択し **[!UICONTROL AT&T]** ます。

1. 「**[!UICONTROL Keep Changes]**」をクリックします。

![&quot;条件の作成&quot;](/help/assets/ad-setCondition_use-analytics-data.png)

## 4.アクションの定義

1. Under the **[!UICONTROL Actions]** section, click **[!UICONTROL Add]**.

1. ドロップダウン **[!UICONTROL Extension]** リストで、を選択し **[!UICONTROL Mobile Core]**&#x200B;ます。

1. ドロップダウン **[!UICONTROL Action Type]** リストで、を選択し **[!UICONTROL Attach Data]**&#x200B;ます。

1. 右側のウィンドウのフィールドで、このイベントに追加するデータを **[!UICONTROL JSON Payload]** 入力します。

1. 「**[!UICONTROL Keep Changes]**」をクリックします。

右側のウィンドウで、このイベントをリッスンする拡張がイベントを聞く前に、SDKイベントにデータを追加するフリーフォームJSONペイロードを追加できます。 この例では、Analytics拡張機能による処理の前に、一部のコンテキストデータがこのイベントに追加されます。 追加されたコンテキストデータが、送信Analyticsヒットになります。

次の例では、 `poi.city``poi.name` との値がAnalyticsイベントのコンテキストデータに追加されます。 新しいキーの値は、このイベントが処理するときに、SDKによって動的に決定されます。

![「アクションの作成」](/help/assets/ad-setAction_use-analytics-data.png)

## 5.ルールを保存し、プロパティを再構築します

設定が完了したら、ルールが次の図のように表示されることを確認します。

![「ルールは完了です。」](/help/assets/ad-ruleComplete_use-analytics-data.png)

1. **[!UICONTROL Save]** をクリックします。

1. Launchプロパティを再構築し、正しい環境に展開します。
