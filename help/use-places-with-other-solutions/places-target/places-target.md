---
title: Adobe Target
description: この節では、Places Service をAdobe Targetで使用する方法について説明します。
exl-id: 6ee91fca-ea48-4de2-8dcf-87981813c678
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 3%

---

# Adobe Targetでの Places Service の使用 {#places-target}

このドキュメントは、Places 拡張機能がアプリケーションに実装されていることを前提としています。 Places 拡張機能の実装について不明な点がある場合は、 [Places 拡張機能](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Places 拡張機能が入口と出口に対するイベントを送信したら、Launch のルールを利用して、Places Service データをAdobe Target SDK イベントに添付できます。 Launch で目的のプロパティを選択し、次のタスクを実行することで、このタイプのルールを作成できます。

## 1.ルールを作成する

1. の **[!UICONTROL ルール]** タブ、クリック **[!UICONTROL 新規ルールの作成]**.

   次の情報に留意してください。

   * このプロパティに対するルールが存在しない場合、ボタンは画面の中央に表示されます。
   * プロパティにルールが設定されている場合、ボタンは画面の右上に表示されます。

## 2.イベントの選択

1. ルールに意味のある名前を付け、ルールのリストで簡単に認識できるようにします。

   この例では、ルールの名前は **[!UICONTROL Places サービスデータを要求されたターゲットコンテンツに添付]**.

1. 以下 **[!UICONTROL イベント]** セクションで、 **[!UICONTROL 追加]**.
1. 次の **[!UICONTROL 拡張]** ドロップダウンリストで、「 **[!UICONTROL Adobe Target]**.
1. 次の **[!UICONTROL イベントタイプ]** ドロップダウンリストで、「 **[!UICONTROL リクエストされたコンテンツ]**.
1. 「**[!UICONTROL 変更を保存]**」をクリックします。

![イベントの追加](/help/assets/ad-setEvent_target.png)

## 3.条件の追加

>[!IMPORTANT]
>
>ルールに条件を追加する場合は、この手順を実行します。 それ以外の場合は、スキップして *アクションの定義* 下

次の例では、アプリを 5 回以上起動したユーザーに対してのみルールをトリガーする条件が作成されます。

1. 以下 **[!UICONTROL 条件]** セクションで、 **[!UICONTROL 追加]**.
1. 次の **[!UICONTROL 拡張]** ドロップダウンリストで、「 **[!UICONTROL Mobile Core]**.
1. 次の **[!UICONTROL 条件タイプ]** ドロップダウンリストで、「 **[!UICONTROL 起動回数]**.
1. 右側のウィンドウで、ドロップダウンリストと数値コントロールを変更し、条件が **[!UICONTROL ユーザーがアプリを 5 回以上起動しました]**.
1. 「**[!UICONTROL 変更を保存]**」をクリックします。

![条件の追加](/help/assets/ad-setCondition_target.png)

## 4.アクションを定義する

1. 以下 **[!UICONTROL アクション]** セクションで、 **[!UICONTROL 追加]**.
1. 次の **[!UICONTROL 拡張]** ドロップダウンリストで、「 **[!UICONTROL Mobile Core]**.
1. 次の **[!UICONTROL アクションタイプ]** ドロップダウンリストで、「 **[!UICONTROL データを添付]**.
1. 右側のウィンドウの **[!UICONTROL JSON ペイロード]** 「 」フィールドで、このイベントに追加するデータを入力します。
1. 「**[!UICONTROL 変更を保存]**」をクリックします。

右側のウィンドウで、このイベントをリッスンする拡張機能が聞く前に、SDK イベントにデータを追加するフリーフォーム JSON ペイロードを追加できます。

次の例では、 `poiCity` および `poiName` 値が **[!UICONTROL mboxparameters]** Target イベントで処理されるリクエストごとに 新しいキーの値は、このイベントの処理時に SDK によって動的に決定されます。

>[!TIP]
>
>この JSON ペイロードは、 `request` オブジェクト。 元のイベントで `request` は、匿名オブジェクトの配列です。 [ データをアタッチ ] を使用して配列内のすべてのオブジェクトにデータをアタッチする場合、 `[*]` 配列を含むことがわかっているキーの表記を使用すると、その配列内のすべてのオブジェクトにペイロードが適用されます。
>
>の表記 `request[*]` ～として大声で読み上げられる _( `request` 配列_.

![アクションの定義](/help/assets/ad-setAction-target.png)

## 5.ルールを保存し、プロパティを再構築します。

設定が完了したら、ルールが次の画像のようになっていることを確認します。

![完了ルール](/help/assets/ad-ruleComplete-target.png)

1. **[!UICONTROL 保存]**&#x200B;をクリックします。
1. Launch プロパティを再構築し、正しい環境にデプロイします。
