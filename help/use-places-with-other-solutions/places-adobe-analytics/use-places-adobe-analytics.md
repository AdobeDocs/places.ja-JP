---
title: POIの入口データと出口データをAnalyticsに送信
description: この節では、POIの入口データと出口データをAnalyticsに送信する方法について説明します。
translation-type: tm+mt
source-git-commit: 8a84fe2dc5a0efe94ce3121e589524e3c7a80c5e
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 3%

---


# POIの入口データと出口データをAnalyticsに送信 {#places-data-analytics}


>[!IMPORTANT]
>
>この節では、アプリケーションにPlaces Serviceが実装されていることを前提としています。 Places Serviceの導入について詳しくは、「Places拡張」を参照して [ください](/help/places-ext-aep-sdks/places-extension/places-extension.md)。

Places Serviceが入口要素と出口イベントを送信した後、Places ServiceデータをAdobe Analyticsに送信するルールをExperience Platform Launchで作成できます。 このタイプのルールを作成するには、「起動」でプロパティを選択し、次の手順を実行します。

## 1.ルールを作成する

1. On the **[!UICONTROL Rules]** tab, click **[!UICONTROL Create New Rule]**.

   次の情報に留意してください。

   * このプロパティに対して既存のルールがない場合、 **[!UICONTROL Create New Rule]** ボタンは画面の中央に表示されます。
   * プロパティにルールが含まれている場合、この **[!UICONTROL Create New Rule]** ボタンは画面の右上に表示されます。

## 2.イベントを選択します。

1. ルールに意味のある名前を入力します。

   この方法により、ルールは、ルールのリストで簡単に認識できます。 この例では、ルールに名前が付けられてい **[!UICONTROL Send Data to Analytics]**&#x200B;ます。

1. 「**[!UICONTROL Events]**」セクションで、「**[!UICONTROL Add]**」をクリックします。

1. ドロップダウン **[!UICONTROL Extension]** リストで、を選択し **[!UICONTROL Places Service]**&#x200B;ます。

1. ドロップダウン **[!UICONTROL Event Type]** リストで、を選択し **[!UICONTROL Enter POI]**&#x200B;ます。

1. 「**[!UICONTROL Keep Changes]**」をクリックします。

   ![&quot;イベントの選択&quot;](/help/assets/pt-selectEvent.png)


## 3.追加条件

>[!IMPORTANT]
>
>ルールに条件を追加するには、この手順を実行します。 それ以外の場合は、「 *次のアクションの定義* 」に進みます。

この例では、現在のPOIの名前が等しい場合にのみルールをトリガーする条件が作成され **[!UICONTROL My POI]**&#x200B;ます。

1. Under the **[!UICONTROL Conditions]** section, click **[!UICONTROL Add]**.

1. ドロップダウン **[!UICONTROL Extension]** リストで、を選択し **[!UICONTROL Places Service]**&#x200B;ます。

1. ドロップダウン **[!UICONTROL Condition Type]** リストで、を選択し **[!UICONTROL Name]**&#x200B;ます。

1. 右側のペインのテキストフィールドに、と入力し **[!UICONTROL My POI]**&#x200B;ます。

1. 「**[!UICONTROL Keep Changes]**」をクリックします。

   ![&quot;条件を設定&quot;](/help/assets/pt-setCondition.png)


## 4.アクションの定義

1. Under the **[!UICONTROL Actions]** section, click **[!UICONTROL Add]**.

1. ドロップダウン **[!UICONTROL Extension]** リストで、を選択し **[!UICONTROL Adobe Analytics]**&#x200B;ます。

1. ドロップダウン **[!UICONTROL Action Type]** リストで、を選択し **[!UICONTROL Track]**&#x200B;ます。

1. 右側のパネルで、Analyticsに送信するアクションまたは状態を追加します。

   このリクエストに追加のコンテキストデータを追加することもできます。 データ要素を使用して、SDKからこのデータを動的に取得できることに注意してください。

1. 「**[!UICONTROL Keep Changes]**」をクリックします。

   次の例では、このエントリイベントをトリガーしたPOIの名前と `TrackAction``poi.name` 等しい追加のコンテキストデータと共に、呼び出しがAnalyticsに送信されます。

   ![&quot;アクションを設定&quot;](/help/assets/pt-setAction.png)

## 5.ルールを保存し、プロパティを再構築します

設定が完了したら、ルールが次の図のように表示されることを確認します。

![&quot;ルールが作成されました&quot;](/help/assets/pt-ruleComplete.png)

1. **[!UICONTROL Save]** をクリックします。

1. Launchプロパティを再構築し、正しい環境に展開します。
