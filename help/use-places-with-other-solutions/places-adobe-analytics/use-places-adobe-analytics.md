---
title: POI入力データと終了データをAnalyticsに送信する
description: この節では、POIのエントリおよび終了データをAnalyticsに送信する方法について説明します。
exl-id: 69e96261-4902-47dd-a930-a8f3d19c179c
TQID: https://experienceleague.adobe.com/H-NkwK7KNSGPjEKYuWNc8F0f3MIu3wBr5FGjypxnqng
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2:
  - id: b069d60e-95f3-44d6-95a8-ddc862a4bc38
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 443
ht-degree: 5%

---

# POI入力データと終了データをAnalyticsに送信する {#places-data-analytics}


>[!IMPORTANT]
>
>このセクションでは、アプリケーションにPlaces サービスが実装されていることを前提としています。 Places サービスの実装について詳しくは、[Places拡張機能](/help/places-ext-aep-sdks/places-extension/places-extension.md)を参照してください。

Places サービスが入口イベントと出口イベントを送信した後、Experience Platform Launchでルールを作成して、Places サービスデータをAdobe Analyticsに送信できます。 このタイプのルールを作成するには、Launchでプロパティを選択し、次の手順を実行します。

## &#x200B;1. ルールの作成

1. 「**[!UICONTROL ルール]**」タブで、**[!UICONTROL 新しいルールを作成]**&#x200B;をクリックします。

   次の情報に留意してください。

   * このプロパティに既存のルールがない場合は、**[!UICONTROL 新しいルールを作成]** ボタンが画面の中央に表示されます。
   * プロパティにルールがある場合は、画面の右上に「**[!UICONTROL 新しいルールを作成]**」ボタンが表示されます。

## &#x200B;2. イベントの選択

1. ルールに意味のある名前を入力します。

   これにより、ルールのリストでルールを簡単に認識できるようになります。 この例では、ルールの名前は&#x200B;**[!UICONTROL Analyticsにデータを送信]**&#x200B;です。

1. **[!UICONTROL イベント]** セクションで、**[!UICONTROL 追加]**&#x200B;をクリックします。

1. **[!UICONTROL 拡張機能]** ドロップダウンリストから、**[!UICONTROL Places サービス]**&#x200B;を選択します。

1. **[!UICONTROL イベントタイプ]** ドロップダウンリストから、**[!UICONTROL POI]**&#x200B;を入力を選択します。

1. 「**[!UICONTROL 変更を保存]**」をクリックします。

   ![&quot;イベントを選択&quot;](/help/assets/pt-selectEvent.png)


## &#x200B;3. 条件を追加

>[!IMPORTANT]
>
>ルールに条件を追加するには、この手順を実行します。 それ以外は、以下の「*アクションを定義*」にスキップします。

この例では、現在のPOIの名前が&#x200B;**[!UICONTROL My POI]**&#x200B;に等しい場合にのみルールをトリガーする条件が作成されます。

1. **[!UICONTROL 条件]** セクションで、**[!UICONTROL 追加]**&#x200B;をクリックします。

1. **[!UICONTROL 拡張機能]** ドロップダウンリストから、**[!UICONTROL Places サービス]**&#x200B;を選択します。

1. **[!UICONTROL 条件タイプ]** ドロップダウンリストから、**[!UICONTROL 名前]**&#x200B;を選択します。

1. 右側のペインのテキストフィールドに、**[!UICONTROL My POI]**&#x200B;と入力します。

1. 「**[!UICONTROL 変更を保存]**」をクリックします。

   ![&quot;条件を設定&quot;](/help/assets/pt-setCondition.png)


## &#x200B;4. アクションを定義

1. 「**[!UICONTROL アクション]**」セクションで、**[!UICONTROL 追加]**&#x200B;をクリックします。

1. **[!UICONTROL 拡張機能]** ドロップダウンリストから、**[!UICONTROL Adobe Analytics]**&#x200B;を選択します。

1. **[!UICONTROL アクションタイプ]** ドロップダウンリストから、**[!UICONTROL トラック]**&#x200B;を選択します。

1. 右側のパネルで、Analyticsに送信するアクションまたは状態を追加します。

   また、このリクエストに追加のコンテキストデータを追加することもできます。 データ要素を使用して、SDKからこのデータを動的に取得できます。

1. 「**[!UICONTROL 変更を保存]**」をクリックします。

   次の例では、このエントリイベントをトリガーしたPOIの名前と同じ`poi.name`の追加のコンテキストデータを含む`TrackAction`呼び出しがAnalyticsに送信されます。

   ![&quot;アクションを設定&quot;](/help/assets/pt-setAction.png)

## &#x200B;5. ルールを保存してプロパティを再構築する

設定が完了したら、ルールが次の画像のようになっていることを確認します。

![&quot;ルールが作成されました&quot;](/help/assets/pt-ruleComplete.png)

1. 「**[!UICONTROL 保存]**」をクリックします。

1. Launch プロパティを再構築し、正しい環境にデプロイします。
