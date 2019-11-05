---
title: Adobe Analyticsへの場所データの送信
seo-title: Adobe Analyticsへの場所データの送信
description: この節では、PlacesデータをAnalyticsに送信する方法について説明します。
seo-description: この節では、PlacesデータをAnalyticsに送信する方法について説明します。
translation-type: tm+mt
source-git-commit: 95dd010db8a860ebf489d04c7a70ec9cda8b3fb1

---


# Adobe Analyticsへの場所データの送信 {#places-data-analytics}


>[!IMPORTANT]
>
>この節では、アプリケーションにPlacesが実装されていることを前提としています。 場所の実装について詳しくは、場所の拡張を参照 [してください](/help/places-ext-aep-sdks/places-extension/places-extension.md)。

場所が入口イベントと出口イベントを送信した後、エクスペリエンスプラットフォーム起動に場所データをAdobe Analyticsに送信するルールを作成できます。 このタイプのルールを作成するには、「起動」でプロパティを選択し、次の手順を実行します。

## 1.ルールの作成

1. タブで、をク **[!UICONTROL Rules]** リックしま **[!UICONTROL Create New Rule]**&#x200B;す。

   次の情報に留意してください。

   * このプロパティに対する既存のルールがない場合、ボ **[!UICONTROL Create New Rule]** タンは画面の中央に表示されます。
   * プロパティにルールが含まれ **[!UICONTROL Create New Rule]** ている場合、ボタンは画面の右上に表示されます。

## 2.イベントの選択

1. ルールに意味のある名前を入力します。

   これにより、ルールはルールのリストで簡単に認識できます。 この例では、Ruleという名前が付けられていま **[!UICONTROL Send Data to Analytics]**&#x200B;す。

1. In the **[!UICONTROL Events]** section, click **[!UICONTROL Add]**.

1. ドロップダウ **[!UICONTROL Extension]** ンリストから、を選択しま **[!UICONTROL Places]**&#x200B;す。

1. ドロップダウ **[!UICONTROL Event Type]** ンリストから、を選択しま **[!UICONTROL Enter POI]**&#x200B;す。

1. 「**[!UICONTROL Keep Changes]**」をクリックします。

   !["イベントを選択"](/help/assets/pt-selectEvent.png)


## 3.条件の追加

>[!IMPORTANT]
>
>ルールに条件を追加するには、この手順を実行します。 それ以外の場合は、以下の「ア *クションの定義* 」に進みます。

この例では、現在のPOIの名前が等しい場合にのみルールをトリガーする条件が作成されます **[!UICONTROL My POI]**。

1. セクションの下 **[!UICONTROL Conditions]** のをクリックしま **[!UICONTROL Add]**&#x200B;す。

1. ドロップダウ **[!UICONTROL Extension]** ンリストから、を選択しま **[!UICONTROL Places]**&#x200B;す。

1. ドロップダウ **[!UICONTROL Condition Type]** ンリストから、を選択しま **[!UICONTROL Name]**&#x200B;す。

1. 右側のペインのテキストフィールドに、と入力します **[!UICONTROL My POI]**。

1. 「**[!UICONTROL Keep Changes]**」をクリックします。

   !["条件を設定"](/help/assets/pt-setCondition.png)


## 4.アクションの定義

1. セクションの下 **[!UICONTROL Actions]** のをクリックしま **[!UICONTROL Add]**&#x200B;す。

1. ドロップダウ **[!UICONTROL Extension]** ンリストから、を選択しま **[!UICONTROL Adobe Analytics]**&#x200B;す。

1. ドロップダウ **[!UICONTROL Action Type]** ンリストから、を選択しま **[!UICONTROL Track]**&#x200B;す。

1. 右側のウィンドウで、Analyticsに送信するアクションまたは状態を追加します。

   また、このリクエストに追加のコンテキストデータを追加することもできます。 データ要素を使用して、SDKからこのデータを動的に取得できます。

1. 「**[!UICONTROL Keep Changes]**」をクリックします。

   次の例では、このエントリイ `TrackAction` ベントをトリガーしたPOIの名前と等しい追加のコンテキストデ `poi.name` ータを使用して、呼び出しがAnalyticsに送信されます。

   !["アクションを設定"](/help/assets/pt-setAction.png)

## 5.ルールを保存し、プロパティを再構築します

設定が完了したら、ルールが次の画像のようになっていることを確認します。

!["ルールが作成されました"](/help/assets/pt-ruleComplete.png)

1. 「**[!UICONTROL Save]**」をクリックします

1. 起動プロパティを再構築し、正しい環境に展開します。
