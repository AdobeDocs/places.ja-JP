---
title: Analytics追加リクエストの場所のコンテキスト
description: この節では、Analyticsリクエストに場所コンテキストを追加する方法について説明します。
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 2%

---


# Analytics追加リクエストの場所のコンテキスト{#run-reports-aa-locserv-data}

>[!IMPORTANT]
>
>このドキュメントは、アプリケーションにPlaces Serviceが実装されていることを前提としています。 Places Serviceの導入について詳しくは、[Places extensions](/help/places-ext-aep-sdks/places-extension/places-extension.md)を参照してください。

Places Serviceが入口イベントと出口イベントを送信した後、Experience Platform Launchでルールを作成し、Places ServiceデータをすべてのAdobe Analyticsに添付できます。 このタイプのルールを作成するには、「起動」でプロパティを選択し、次の手順を実行します。

## 1.ルールを作成する

1. 「**[!UICONTROL ルール]**」タブで、「**[!UICONTROL 新しいルールを作成]**」をクリックします。

   次の情報に留意してください。
   * このプロパティに既存のルールがない場合は、「**[!UICONTROL 新しいルールを作成]**」ボタンが画面の中央に表示されます。
   * プロパティにルールが含まれている場合は、「**[!UICONTROL 新しいルールを作成]**」ボタンが画面の右上に表示されます。

## 2.イベントの選択

1. ルールに意味のある名前を付け、ルールのリストで簡単に認識できるようにします。

   この例では、ルールの名前は「**[!UICONTROL Attach Places Service Data to Analytics Track Actionイベント]**」です。

1. 「**[!UICONTROL イベント]**」セクションで、「**[!UICONTROL 追加]**」をクリックします。

1. 「**[!UICONTROL 拡張子]**」ドロップダウンリストから、「**[!UICONTROL モバイルコア]**」を選択します。

1. **[!UICONTROL イベントタイプ]**&#x200B;ドロップダウンリストから、「**[!UICONTROL アクションを追跡]**」を選択します。

ここで、このルールに含めるトリガーを指定できます。 この例では、トリガーはすべての`TrackAction`呼び出しに基づいています。 イベントを設定したら、「**[!UICONTROL 変更を保持]**」をクリックします。

![イベントの作成](/help/assets/ad-setEvent_use-analytics-data.png)


## 3.追加条件

>[!IMPORTANT]
>
>ルールに条件を追加するには、次の手順を実行します。 それ以外の場合は、下の&#x200B;*「アクション*&#x200B;を定義する」セクションにスキップしてください。

この例では、AT&amp;Tのお客様に対してのみルールをトリガーする条件が作成されています。

1. 「**[!UICONTROL 条件]**」セクションで、「**[!UICONTROL 追加]**」をクリックします。

1. 「**[!UICONTROL 拡張子]**」ドロップダウンリストから、「**[!UICONTROL モバイルコア]**」を選択します。

1. 「**[!UICONTROL 条件のタイプ]**」ドロップダウンリストから、「**[!UICONTROL 通信事業者名]**」を選択します。

1. 右側のウィンドウで、「**[!UICONTROL AT&amp;T]**」チェックボックスを選択します。

1. 「**[!UICONTROL 変更を保存]**」をクリックします。

![&quot;条件の作成&quot;](/help/assets/ad-setCondition_use-analytics-data.png)

## 4.アクションの定義

1. 「**[!UICONTROL アクション]**」セクションで、「**[!UICONTROL 追加]**」をクリックします。

1. 「**[!UICONTROL 拡張子]**」ドロップダウンリストから、「**[!UICONTROL モバイルコア]**」を選択します。

1. 「**[!UICONTROL アクションタイプ]**」ドロップダウンリストから、「**[!UICONTROL データの添付]**」を選択します。

1. 右側のウィンドウの&#x200B;**[!UICONTROL JSON Payload]**&#x200B;フィールドに、このイベントに追加するデータを入力します。

1. 「**[!UICONTROL 変更を保存]**」をクリックします。

右側のウィンドウで、このイベントをリッスンする拡張がイベントを聞く前に、SDKイベントにデータを追加するフリーフォームJSONペイロードを追加できます。 この例では、Analytics拡張機能による処理の前に、一部のコンテキストデータがこのイベントに追加されます。 追加されたコンテキストデータが、送信Analyticsヒットになります。

次の例では、`poi.city`と`poi.name`の値がAnalyticsイベントのコンテキストデータに追加されます。 新しいキーの値は、このイベントが処理するときに、SDKによって動的に決定されます。

![「アクションの作成」](/help/assets/ad-setAction_use-analytics-data.png)

## 5.ルールを保存し、プロパティを再構築します

設定が完了したら、ルールが次の図のように表示されることを確認します。

![「ルールは完了です。」](/help/assets/ad-ruleComplete_use-analytics-data.png)

1. **[!UICONTROL 保存]**&#x200B;をクリックします。

1. Launchプロパティを再構築し、正しい環境に展開します。
