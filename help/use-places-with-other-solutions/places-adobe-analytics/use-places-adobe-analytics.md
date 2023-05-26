---
title: POI 入口および出口データを Analytics に送信
description: この節では、POI 入口データと出口データを Analytics に送信する方法について説明します。
exl-id: 69e96261-4902-47dd-a930-a8f3d19c179c
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 3%

---

# POI 入口および出口データを Analytics に送信 {#places-data-analytics}


>[!IMPORTANT]
>
>この節では、アプリケーションに Places Service が実装されていることを前提としています。 Places Service の実装について詳しくは、 [Places 拡張機能](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Places Service が入口イベントと出口イベントを送信した後、Experience Platform Launchでルールを作成して、Places Service データをAdobe Analyticsに送信できます。 このタイプのルールを作成するには、Launch でプロパティを選択し、次の手順を実行します。

## 1.ルールを作成する

1. の **[!UICONTROL ルール]** タブ、クリック **[!UICONTROL 新規ルールの作成]**.

   次の情報に留意してください。

   * このプロパティのルールが存在しない場合、 **[!UICONTROL 新規ルールの作成]** ボタンが画面の中央に表示されます。
   * プロパティにルールがある場合、 **[!UICONTROL 新規ルールの作成]** ボタンが画面の右上に表示されます。

## 2.イベントを選択します

1. ルールに意味のある名前を入力します。

   これにより、ルールをルールのリストで簡単に認識できるようになります。 この例では、ルールの名前は **[!UICONTROL Analytics へのデータ送信]**.

1. 内 **[!UICONTROL イベント]** セクションで、 **[!UICONTROL 追加]**.

1. 次の **[!UICONTROL 拡張]** ドロップダウンリストで、「 **[!UICONTROL Places Service]**.

1. 次の **[!UICONTROL イベントタイプ]** ドロップダウンリストで、「 **[!UICONTROL POI を入力]**.

1. 「**[!UICONTROL 変更を保存]**」をクリックします。

   ![&quot;イベントを選択&quot;](/help/assets/pt-selectEvent.png)


## 3.条件を追加

>[!IMPORTANT]
>
>ルールに条件を追加するには、この手順を実行します。 それ以外の場合は、スキップして *アクションの定義* 下

この例では、現在の POI の名前が等しい場合にのみルールをトリガーさせる条件が作成されます **[!UICONTROL マイ POI]**.

1. 以下 **[!UICONTROL 条件]** セクションで、 **[!UICONTROL 追加]**.

1. 次の **[!UICONTROL 拡張]** ドロップダウンリストで、「 **[!UICONTROL Places Service]**.

1. 次の **[!UICONTROL 条件タイプ]** ドロップダウンリストで、「 **[!UICONTROL 名前]**.

1. 右側のウィンドウのテキストフィールドに、 **[!UICONTROL マイ POI]**.

1. 「**[!UICONTROL 変更を保存]**」をクリックします。

   ![&quot;条件を設定&quot;](/help/assets/pt-setCondition.png)


## 4.アクションを定義する

1. 以下 **[!UICONTROL アクション]** セクションで、 **[!UICONTROL 追加]**.

1. 次の **[!UICONTROL 拡張]** ドロップダウンリストで、「 **[!UICONTROL Adobe Analytics]**.

1. 次の **[!UICONTROL アクションタイプ]** ドロップダウンリストで、「 **[!UICONTROL 追跡]**.

1. 右側のウィンドウで、Analytics に送信するアクションまたは状態を追加します。

   このリクエストに追加のコンテキストデータを追加することもできます。 データ要素を使用すると、SDK からこのデータを動的に取得できます。

1. 「**[!UICONTROL 変更を保存]**」をクリックします。

   次の例では、 `TrackAction` 呼び出しは、 `poi.name` このエントリイベントをトリガーした POI の名前と等しい：

   ![&quot;アクションを設定&quot;](/help/assets/pt-setAction.png)

## 5.ルールを保存し、プロパティを再構築します。

設定が完了したら、ルールが次の画像のようになっていることを確認します。

![&quot;ルールが作成されました&quot;](/help/assets/pt-ruleComplete.png)

1. **[!UICONTROL 保存]**&#x200B;をクリックします。

1. Launch プロパティを再構築し、正しい環境にデプロイします。
