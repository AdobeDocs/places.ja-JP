---
title: Adobe Target
description: ここでは、Places ServiceをAdobe Targetで使用する方法について説明します。
translation-type: tm+mt
source-git-commit: d33e4e2d798c7048bdd275cdf6c0aabf3434f789
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 2%

---


# Adobe Targetでプレイスサービスを使用 {#places-target}

このドキュメントは、アプリケーションにPlaces拡張機能が実装されていることを前提としています。 Places拡張機能の導入について詳しくは、Places拡張機能の導入を参照して [ください](/help/places-ext-aep-sdks/places-extension/places-extension.md)。

Places拡張機能が入口と出口のイベントを送信した後、「開始のルール」を利用して、Places ServiceデータをAdobe TargetSDKイベントに添付できます。 「起動」で目的のプロパティを選択し、次のタスクを実行して、このタイプのルールを作成できます。

## 1.ルールの作成

1. On the **[!UICONTROL Rules]** tab, click **[!UICONTROL Create New Rule]**.

   次の情報に留意してください。

   * このプロパティに対する既存のルールがない場合、ボタンは画面の中央に表示されます。
   * プロパティにルールが含まれている場合、ボタンは画面の右上に表示されます。

## 2.イベントを選択します。

1. ルールに意味のある名前を付け、ルールのリストで簡単に認識できるようにします。

   この例では、ルールに名前が付けられてい **[!UICONTROL Attach Places Service Data to Target Content Requested]**&#x200B;ます。

1. Under the **[!UICONTROL Events]** section, click **[!UICONTROL Add]**.
1. ドロップダウン **[!UICONTROL Extension]** リストで、を選択し **[!UICONTROL Adobe Target]**&#x200B;ます。
1. ドロップダウン **[!UICONTROL Event Type]** リストで、を選択し **[!UICONTROL Content Requested]**&#x200B;ます。
1. 「**[!UICONTROL Keep Changes]**」をクリックします。

![イベントの追加](/help/assets/ad-setEvent_target.png)

## 3.追加条件

>[!IMPORTANT]
>
>ルールに条件を追加する場合は、この手順を実行します。 それ以外の場合は、次の「 *アクションの* 定義」に進みます。

次の例では、条件を作成して、アプリを5回以上起動したユーザーに対してのみルールをトリガーします。

1. Under the **[!UICONTROL Conditions]** section, click **[!UICONTROL Add]**.
1. ドロップダウン **[!UICONTROL Extension]** リストで、を選択し **[!UICONTROL Mobile Core]**&#x200B;ます。
1. ドロップダウン **[!UICONTROL Condition Type]** リストで、を選択し **[!UICONTROL Launches]**&#x200B;ます。
1. 右側のウィンドウで、ドロップダウンリストと数値コントロールを変更して、条件が読み上げられるようにし **[!UICONTROL User has launched the app greater than or equal to 5 times]**&#x200B;ます。
1. 「**[!UICONTROL Keep Changes]**」をクリックします。

![条件を追加する](/help/assets/ad-setCondition_target.png)

## 4.アクションの定義

1. Under the **[!UICONTROL Actions]** section, click **[!UICONTROL Add]**.
1. ドロップダウン **[!UICONTROL Extension]** リストで、を選択し **[!UICONTROL Mobile Core]**&#x200B;ます。
1. ドロップダウン **[!UICONTROL Action Type]** リストで、を選択し **[!UICONTROL Attach Data]**&#x200B;ます。
1. 右側のウィンドウのフィールドで、このイベントに追加するデータを **[!UICONTROL JSON Payload]** 入力します。
1. 「**[!UICONTROL Keep Changes]**」をクリックします。

右側のウィンドウで、フリーフォームJSONペイロードを追加し、このイベントをリッスンする拡張機能がこのペイロードを聞く前に、SDKイベントにデータを追加できます。

次の例では、 `poiCity` との `poiName` 値が、ターゲットイベントで処理され **[!UICONTROL mboxparameters]** る各リクエストのに追加されます。 新しいキーの値は、このイベントの処理時にSDKによって動的に決定されます。

>[!TIP]
>
>このJSONペイロードは、 `request` オブジェクトに特別な表記を使用します。 元のイベントでは、は匿名オブジェクトの配列 `request` です。 「データの添付」を使用して配列内のすべてのオブジェクトにデータを添付する場合、配列を含むことがわかっているキーの `[*]` 表記によって、その配列内のすべてのオブジェクトにペイロードが適用されます。
>
>の表記は、 `request[*]` 配列内の各オブジェクト _について、のように読み上げることができ `request` ます_。

![動作を定義する](/help/assets/ad-setAction-target.png)

## 5.ルールを保存し、プロパティを再構築します

設定が完了したら、ルールが次の図のように表示されることを確認します。

![完了規則](/help/assets/ad-ruleComplete-target.png)

1. **[!UICONTROL Save]** をクリックします。
1. Launchプロパティを再構築し、正しい環境に展開します。
