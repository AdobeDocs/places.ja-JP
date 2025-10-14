---
title: POI 入口データと出口データの Analytics への送信
description: この節では、POI エントリおよび離脱データを Analytics に送信する方法について説明します。
exl-id: 69e96261-4902-47dd-a930-a8f3d19c179c
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 3%

---

# POI 入口データと出口データの Analytics への送信 {#places-data-analytics}


>[!IMPORTANT]
>
>この節では、アプリケーションに Places Service が実装されていることを前提としています。 Places Service の実装について詳しくは、[Places 拡張機能 &#x200B;](/help/places-ext-aep-sdks/places-extension/places-extension.md) を参照してください。

Places Service が入口イベントと出口イベントを送信した後、Experience Platform Launchでルールを作成して、Places Service データをAdobe Analyticsに送信できます。 このタイプのルールを作成するには、Launch でプロパティを選択し、次の手順を実行します。

## 1. ルールを作成する

1. 「**[!UICONTROL ルール]**」タブで、「**[!UICONTROL 新規ルールを作成]**」をクリックします。

   次の情報に留意してください。

   * このプロパティに既存のルールがない場合、「**[!UICONTROL 新しいルールの作成]**」ボタンが画面の中央にあります。
   * プロパティにルールがある場合、「**[!UICONTROL 新しいルールを作成]**」ボタンが画面の右上に表示されます。

## 2. イベントを選択する

1. ルールにわかりやすい名前を入力します。

   これにより、ルールはルールのリストで簡単に認識できます。 この例では、ルールの名前は **[!UICONTROL Analytics にデータを送信]** です。

1. 「**[!UICONTROL イベント]**」セクションで、「**[!UICONTROL 追加]**」をクリックします。

1. **[!UICONTROL 拡張機能]** ドロップダウンリストから、「**[!UICONTROL Places Service]**」を選択します。

1. **[!UICONTROL イベントタイプ]** ドロップダウンリストから、「**[!UICONTROL POI を入力]**」を選択します。

1. 「**[!UICONTROL 変更を保存]**」をクリックします。

   ![&#x200B; イベントを選択」 &#x200B;](/help/assets/pt-selectEvent.png)


## 3.条件を追加

>[!IMPORTANT]
>
>ルールに条件を追加するには、この手順を完了します。 それ以外の場合は、以下の *アクションを定義* にスキップします。

この例では、現在の POI の名前が **[!UICONTROL My POI]** に等しい場合にのみルールをトリガーさせる条件を作成します。

1. 「**[!UICONTROL 条件]**」セクションで、「**[!UICONTROL 追加]**」をクリックします。

1. **[!UICONTROL 拡張機能]** ドロップダウンリストから、「**[!UICONTROL Places Service]**」を選択します。

1. **[!UICONTROL 条件タイプ]** ドロップダウンリストから「**[!UICONTROL 名前]**」を選択します。

1. 右側のペインのテキストフィールドに「**[!UICONTROL My POI]**」と入力します。

1. 「**[!UICONTROL 変更を保存]**」をクリックします。

   ![&#x200B; 「条件を設定」 &#x200B;](/help/assets/pt-setCondition.png)


## 4. アクションを定義する

1. 「**[!UICONTROL アクション]**」セクションで、「**[!UICONTROL 追加]**」をクリックします。

1. **[!UICONTROL 拡張機能]** ドロップダウンリストから、「**[!UICONTROL Adobe Analytics]**」を選択します。

1. **[!UICONTROL アクションタイプ]** ドロップダウンリストから「**[!UICONTROL トラック]**」を選択します。

1. 右側のパネルで、Analytics に送信するアクションまたは状態を追加します。

   また、このリクエストにコンテキストデータを追加することもできます。 データ要素を使用して、このデータを SDK から動的に取得できることに注意してください。

1. 「**[!UICONTROL 変更を保存]**」をクリックします。

   次の例では、このエントリイベントをトリガーした POI の名前と同じ `poi.name` の追加のコンテキストデータを持つ `TrackAction` 呼び出しが Analytics に送信されます。

   ![&#x200B; 「アクションを設定」 &#x200B;](/help/assets/pt-setAction.png)

## 5. ルールを保存し、プロパティを再構築する

設定が完了したら、ルールが次の画像のようになっていることを確認します。

![&#x200B; 「ルールが作成されました」 &#x200B;](/help/assets/pt-ruleComplete.png)

1. **[!UICONTROL 保存]**&#x200B;をクリックします。

1. Launch プロパティを再構築し、正しい環境にデプロイします。
