---
title: Analytics リクエストに場所コンテキストを追加
description: この節では、Analytics リクエストにロケーションコンテキストを追加する方法について説明します。
exl-id: bee7b6e3-a75b-4a07-b6e2-f93ce33aa042
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 2%

---

# Analytics リクエストに場所コンテキストを追加 {#run-reports-aa-locserv-data}

>[!IMPORTANT]
>
>このドキュメントは、アプリケーションに Places Service が実装されていることを前提としています。 Places Service の実装について詳しくは、 [Places 拡張機能](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Places Service が入口イベントと出口イベントを送信した後は、Experience Platform Launch内でルールを作成し、Places Service データをすべてのAdobe Analyticsイベントに関連付けることができます。 このタイプのルールを作成するには、Launch でプロパティを選択し、次の手順を実行します。

## 1.ルールを作成する

1. の **[!UICONTROL ルール]** タブ、クリック **[!UICONTROL 新規ルールの作成]**.

   次の情報に留意してください。
   * このプロパティのルールが存在しない場合、 **[!UICONTROL 新規ルールの作成]** ボタンが画面の中央に表示されます。
   * プロパティにルールがある場合、 **[!UICONTROL 新規ルールの作成]** ボタンが画面の右上に表示されます。

## 2.イベントを選択します

1. ルールに意味のある名前を付け、ルールのリストで簡単に認識できるようにします。

   この例では、ルールの名前は **[!UICONTROL Places サービスデータを Analytics に添付してアクションイベントを追跡する]**.

1. 以下 **[!UICONTROL イベント]** セクションで、 **[!UICONTROL 追加]**.

1. 次の **[!UICONTROL 拡張]** ドロップダウンリストで、「 **[!UICONTROL Mobile Core]**.

1. 次の **[!UICONTROL イベントタイプ]** ドロップダウンリストで、「 **[!UICONTROL アクションの追跡]**.

次に、このルールに含めるトリガーを決定できます。 この例では、トリガーは、 `TrackAction` 呼び出し。 イベントを設定したら、 **[!UICONTROL 変更を保持]**.

![&quot;イベントの作成&quot;](/help/assets/ad-setEvent_use-analytics-data.png)


## 3.条件を追加

>[!IMPORTANT]
>
>ルールに条件を追加するには、次の手順を実行します。 それ以外の場合は、スキップして *アクションの定義* 」の節を参照してください。

この例では、AT&amp;T のお客様に対してのみルールをトリガーする条件が作成されます。

1. 以下 **[!UICONTROL 条件]** セクションで、 **[!UICONTROL 追加]**.

1. 次の **[!UICONTROL 拡張]** ドロップダウンリストで、「 **[!UICONTROL Mobile Core]**.

1. 次の **[!UICONTROL 条件タイプ]** ドロップダウンリストで、「 **[!UICONTROL 通信事業者名]**.

1. 右側のウィンドウで、「 **[!UICONTROL AT&amp;T]** チェックボックス。

1. 「**[!UICONTROL 変更を保存]**」をクリックします。

![&quot;条件の作成&quot;](/help/assets/ad-setCondition_use-analytics-data.png)

## 4.アクションを定義する

1. 以下 **[!UICONTROL アクション]** セクションで、 **[!UICONTROL 追加]**.

1. 次の **[!UICONTROL 拡張]** ドロップダウンリストで、「 **[!UICONTROL Mobile Core]**.

1. 次の **[!UICONTROL アクションタイプ]** ドロップダウンリストで、「 **[!UICONTROL データを添付]**.

1. 右側のウィンドウの **[!UICONTROL JSON ペイロード]** 「 」フィールドで、このイベントに追加するデータを入力します。

1. 「**[!UICONTROL 変更を保存]**」をクリックします。

右側のウィンドウで、このイベントをリッスンしている拡張機能がイベントを聞く前に、SDK イベントにデータを追加するフリーフォーム JSON ペイロードを追加できます。 この例では、一部のコンテキストデータは、Analytics 拡張機能が処理する前にこのイベントに追加されます。 追加されたコンテキストデータは、送信 Analytics ヒットに対するものになります。

次の例では、 `poi.city` および `poi.name` の値が Analytics イベントのコンテキストデータに追加されます。 新しいキーの値は、このイベントが処理される際に SDK によって動的に決定されます。

![&quot;アクションの作成&quot;](/help/assets/ad-setAction_use-analytics-data.png)

## 5.ルールを保存し、プロパティを再構築します。

設定が完了したら、ルールが次の画像のようになっていることを確認します。

![「規則は完成した」](/help/assets/ad-ruleComplete_use-analytics-data.png)

1. **[!UICONTROL 保存]**&#x200B;をクリックします。

1. Launch プロパティを再構築し、正しい環境にデプロイします。
