---
title: Adobe Target
description: ここでは、Adobe Targetで Places Service を使用する方法について説明します。
exl-id: 6ee91fca-ea48-4de2-8dcf-87981813c678
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 3%

---

# Adobe Targetでの Places Service の使用 {#places-target}

このドキュメントでは、アプリケーションに Places 拡張機能が実装されていることを前提としています。 Places 拡張機能の実装に関するヘルプが必要な場合は、[Places 拡張機能 ](/help/places-ext-aep-sdks/places-extension/places-extension.md) を参照してください。

Places 拡張機能によって入口と出口のイベントが送信されたら、Launch のルールを活用して、Places Service データをAdobe Target SDK イベントに添付できます。 Launch で目的のプロパティを選択した状態で、次のタスクを実行して、このタイプのルールを作成できます。

## 1. ルールを作成する

1. 「**[!UICONTROL ルール]**」タブで、「**[!UICONTROL 新規ルールを作成]**」をクリックします。

   次の情報に留意してください。

   * このプロパティに既存のルールがない場合、ボタンは画面の中央にあります。
   * プロパティにルールがある場合、ボタンは画面の右上に表示されます。

## 2. イベントを選択する

1. ルールのリスト内でルールがわかりやすい名前を付けると、簡単に認識できます。

   この例では、ルールの名前は **[!UICONTROL Attach Places Service Data to Target Content Requested]** です。

1. 「**[!UICONTROL イベント]**」セクションで、「**[!UICONTROL 追加]**」をクリックします。
1. **[!UICONTROL 拡張機能]** ドロップダウンリストから、「**[!UICONTROL Adobe Target]**」を選択します。
1. **[!UICONTROL イベントタイプ]** ドロップダウンリストから「**[!UICONTROL リクエストされたコンテンツ]**」を選択します。
1. 「**[!UICONTROL 変更を保存]**」をクリックします。

![ イベントを追加 ](/help/assets/ad-setEvent_target.png)

## 3.条件を追加

>[!IMPORTANT]
>
>ルールに条件を追加する場合は、この手順を完了してください。 それ以外の場合は、以下の *アクションを定義* にスキップします。

次の例では、アプリを 5 回以上起動したユーザーに対してのみルールをトリガーにする条件を作成します。

1. 「**[!UICONTROL 条件]**」セクションで、「**[!UICONTROL 追加]**」をクリックします。
1. **[!UICONTROL 拡張機能]** ドロップダウンリストから、「**[!UICONTROL Mobile Core]**」を選択します。
1. **[!UICONTROL 条件タイプ]** ドロップダウンリストから「**[!UICONTROL ローンチ]**」を選択します。
1. 右側のペインで、ドロップダウンリストと数値コントロールを変更して、条件が **[!UICONTROL ユーザーはアプリを 5 回以上起動しました]** となるようにします。
1. 「**[!UICONTROL 変更を保存]**」をクリックします。

![ 条件を追加 ](/help/assets/ad-setCondition_target.png)

## 4. アクションを定義する

1. 「**[!UICONTROL アクション]**」セクションで、「**[!UICONTROL 追加]**」をクリックします。
1. **[!UICONTROL 拡張機能]** ドロップダウンリストから、「**[!UICONTROL Mobile Core]**」を選択します。
1. **[!UICONTROL アクションタイプ]** ドロップダウンリストから「**[!UICONTROL データを添付]**」を選択します。
1. 右側のペインの「**[!UICONTROL JSON ペイロード]**」フィールドに、このイベントに追加するデータを入力します。
1. 「**[!UICONTROL 変更を保存]**」をクリックします。

右側のパネルでは、このイベントをリッスンしている拡張機能にリッスンされる前に、SDK イベントにデータを追加するフリーフォーム JSON ペイロードを追加できます。

次の例では、Target イベントで処理される各リクエストの **[!UICONTROL mboxparameters]** に `poiCity` と `poiName` の値が追加されます。 新しいキーの値は、このイベントの処理時に SDK によって動的に決定されます。

>[!TIP]
>
>この JSON ペイロードでは、`request` オブジェクトに特別な表記を使用します。 元のイベントでは、`request` は匿名オブジェクトの配列です。 「データを添付」を使用して配列内のすべてのオブジェクトにデータを添付する場合、配列を含んでいることがわかっているキーに `[*]` の表記を使用すると、その配列内のすべてのオブジェクトにペイロードが適用されます。
>
>`request[*]` の表記は、（`request` 配列内の各オブジェクトに対して _として読み上げることができ_ す。

![ アクションの定義 ](/help/assets/ad-setAction-target.png)

## 5. ルールを保存し、プロパティを再構築する

設定が完了したら、ルールが次の画像のようになっていることを確認します。

![ 完了したルール ](/help/assets/ad-ruleComplete-target.png)

1. **[!UICONTROL 保存]**&#x200B;をクリックします。
1. Launch プロパティを再構築し、正しい環境にデプロイします。
