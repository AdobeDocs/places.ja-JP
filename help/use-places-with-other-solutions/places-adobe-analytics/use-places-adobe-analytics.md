---
title: Adobe Analyticsへの場所データの送信
seo-title: Adobe Analyticsへの場所データの送信
description: この節では、PlacesデータをAnalyticsに送信する方法について説明します。
seo-description: 'この節では、PlacesデータをAnalyticsに送信する方法について説明します。 '
translation-type: tm+mt
source-git-commit: fd98249c01fba93250dc7111798c76f3c96c6e20

---


# Adobe Analyticsへの場所データの送信 {#places-data-analytics}


>[!IMPORTANT]
>
>このドキュメントでは、アプリケーションにPlacesが実装されていることを前提としています。 場所の実装の詳細については、「場所の拡張」を参 [照してください](/help/places-ext-aep-sdks/places-extension/places-extension.md)。

場所が入口イベントと出口イベントを送信した後、エクスペリエンスプラットフォーム起動に場所データをAdobe Analyticsに送信するルールを作成できます。 このタイプのルールを作成するには、「起動」でプロパティを選択し、次の手順を実行します。

## 1.ルールの作成

1. タブで、をク **[!UICONTROL Rules]** リックしま **[!UICONTROL Create New Rule]**&#x200B;す。

   次の情報に留意してください。

   * このプロパティに対する既存のルールがない場合、ボタンは画面の中央に表示されます。
   * プロパティにルールが含まれている場合、ボタンは画面の右上に表示されます。

## 2.イベントの選択

1. ルールに意味のある名前を付け、ルールのリストで簡単に認識できるようにします。 この例では、ルールの名前は「 **Send Data to Analytics」です**。

2. In the **[!UICONTROL Events]** section, click **[!UICONTROL Add]**.

3. ドロップダウ **[!UICONTROL Extension]** ンリストから、を選択しま **[!UICONTROL Places]**&#x200B;す。

4. ドロップダウ **[!UICONTROL Event Type]** ンリストから、を選択しま **[!UICONTROL Enter POI]**&#x200B;す。

5. 「**[!UICONTROL Keep Changes]**」をクリックします。

   !["イベントを選択"](/help/assets/pt-selectEvent.png)


## 3.条件の追加

>[!IMPORTANT]
>
>ルールに条件を追加する場合は、この手順を実行します。 それ以外の場合は、以下の「ア *クションの定義* 」に進みます。


この例では、現在のPOIの名前が等しい場合にのみルールをトリガーする条件が作成されます **[!UICONTROL My POI]**。

1. セクションの下 **[!UICONTROL Conditions]** のをクリックしま **[!UICONTROL Add]**&#x200B;す。

2. ドロップダウ **[!UICONTROL Extension]** ンリストから、を選択しま **[!UICONTROL Places]**&#x200B;す。

3. ドロップダウ **[!UICONTROL Condition Type]** ンリストから、を選択しま **[!UICONTROL Name]**&#x200B;す。

4. 右側のウィンドウのテキストフィールドに、と入力します **[!UICONTROL My POI]**。

5. 「**[!UICONTROL Keep Changes]**」をクリックします。

   !["条件を設定"](/help/assets/ad-setCondition.png)


## 4.アクションの定義

1. セクションの下 **[!UICONTROL Actions]** のをクリックしま **[!UICONTROL Add]**&#x200B;す。

2. ドロップダウ **[!UICONTROL Extension]** ンリストから、を選択しま **[!UICONTROL Adobe Analytics]**&#x200B;す。

3. ドロップダウ **[!UICONTROL Action Type]** ンリストから、を選択しま **[!UICONTROL Track]**&#x200B;す。

4. 右側のウィンドウで、Analyticsに送信するアクションまたは状態を追加します。 また、このリクエストに追加のコンテキストデータを追加することもできます。 データ要素を使用して、SDKからこのデータを動的に取得できます。

5. 「**[!UICONTROL Keep Changes]**」をクリックします。

次の例では、このエントリ `TrackAction` イベントをトリガーしたPOIの名前と同じpoi.nameの追加のコンテキストデータと共に **** 、呼び出しがAnalyticsに送信されます。

!["アクションを設定"](/help/assets/pt-setAction.png)

## 5.ルールを保存してプロパティを再構築する

設定が完了したら、ルールが次の画像のようになっていることを確認します。

!["ルールが作成されました"](/help/assets/pt-ruleComplete.png)


1. 「**[!UICONTROL Save]**」をクリックします

2. 起動プロパティを再構築し、正しい環境に展開します。

