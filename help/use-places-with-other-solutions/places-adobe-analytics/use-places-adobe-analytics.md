---
title: POIの入口データと出口データをAnalyticsに送信
description: この節では、POIの入口データと出口データをAnalyticsに送信する方法について説明します。
translation-type: tm+mt
source-git-commit: 8a84fe2dc5a0efe94ce3121e589524e3c7a80c5e
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 3%

---


# POIの入口と出口のデータをAnalyticsに送信{#places-data-analytics}


>[!IMPORTANT]
>
>この節では、アプリケーションにPlaces Serviceが実装されていることを前提としています。 Places Serviceの導入について詳しくは、[Places extensions](/help/places-ext-aep-sdks/places-extension/places-extension.md)を参照してください。

Places Serviceが入口要素と出口イベントを送信した後、Places ServiceデータをAdobe Analyticsに送信するルールをExperience Platform Launchで作成できます。 このタイプのルールを作成するには、「起動」でプロパティを選択し、次の手順を実行します。

## 1.ルールを作成する

1. 「**[!UICONTROL ルール]**」タブで、「**[!UICONTROL 新しいルールを作成]**」をクリックします。

   次の情報に留意してください。

   * このプロパティに既存のルールがない場合は、「**[!UICONTROL 新しいルールを作成]**」ボタンが画面の中央に表示されます。
   * プロパティにルールが含まれている場合は、「**[!UICONTROL 新しいルールを作成]**」ボタンが画面の右上に表示されます。

## 2.イベントを選択します。

1. ルールに意味のある名前を入力します。

   この方法により、ルールは、ルールのリストで簡単に認識できます。 この例では、ルールの名前は「**[!UICONTROL Analyticsにデータを送信]**」です。

1. 「**[!UICONTROL イベント]**」セクションで、「**[!UICONTROL 追加]**」をクリックします。

1. 「**[!UICONTROL 拡張子]**」ドロップダウンリストから、「**[!UICONTROL サービスを配置]**」を選択します。

1. **[!UICONTROL イベントタイプ]**&#x200B;ドロップダウンリストから、**[!UICONTROL POIを入力]**&#x200B;を選択します。

1. 「**[!UICONTROL 変更を保存]**」をクリックします。

   ![&quot;イベントの選択&quot;](/help/assets/pt-selectEvent.png)


## 3.追加条件

>[!IMPORTANT]
>
>ルールに条件を追加するには、この手順を実行します。 それ以外の場合は、*下の*&#x200B;アクションを定義するにはに進みます。

この例では、現在のPOIの名前が&#x200B;**[!UICONTROL My POI]**&#x200B;と等しい場合にのみルールがトリガーされる条件が作成されます。

1. 「**[!UICONTROL 条件]**」セクションで、「**[!UICONTROL 追加]**」をクリックします。

1. 「**[!UICONTROL 拡張子]**」ドロップダウンリストから、「**[!UICONTROL サービスを配置]**」を選択します。

1. 「**[!UICONTROL 条件の種類]**」ドロップダウンリストから、「**[!UICONTROL 名前]**」を選択します。

1. 右側のウィンドウのテキストフィールドに、「**[!UICONTROL My POI]**」と入力します。

1. 「**[!UICONTROL 変更を保存]**」をクリックします。

   ![&quot;条件を設定&quot;](/help/assets/pt-setCondition.png)


## 4.アクションの定義

1. 「**[!UICONTROL アクション]**」セクションで、「**[!UICONTROL 追加]**」をクリックします。

1. 「**[!UICONTROL 拡張子]**」ドロップダウンリストから、**[!UICONTROL Adobe Analytics]**&#x200B;を選択します。

1. **[!UICONTROL アクションタイプ]**&#x200B;ドロップダウンリストから、**[!UICONTROL 追跡]**&#x200B;を選択します。

1. 右側のパネルで、Analyticsに送信するアクションまたは状態を追加します。

   このリクエストに追加のコンテキストデータを追加することもできます。 データ要素を使用して、SDKからこのデータを動的に取得できることに注意してください。

1. 「**[!UICONTROL 変更を保存]**」をクリックします。

   次の例では、`TrackAction`呼び出しが、このエントリイベントをトリガーしたPOIの名前と同じ`poi.name`の追加のコンテキストデータと共にAnalyticsに送信されます。

   ![&quot;アクションを設定&quot;](/help/assets/pt-setAction.png)

## 5.ルールを保存し、プロパティを再構築します

設定が完了したら、ルールが次の図のように表示されることを確認します。

![&quot;ルールが作成されました&quot;](/help/assets/pt-ruleComplete.png)

1. **[!UICONTROL 保存]**&#x200B;をクリックします。

1. Launchプロパティを再構築し、正しい環境に展開します。
