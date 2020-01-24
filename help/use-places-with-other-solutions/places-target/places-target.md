---
title: Adobe Target
description: ここでは、Places ServiceをAdobe targetと共に使用する方法について説明します。
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b

---


# Adobe targetでのPlacesサービスの使用 {#places-target}

このドキュメントでは、アプリケーションにPlaces拡張機能が実装されていることを前提としています。 Places拡張機能の実装に関するヘルプが必要な場合は、Places拡張機能を参照 [してください](/help/places-ext-aep-sdks/places-extension/places-extension.md)。

Places拡張機能が入口と出口のイベントを送信した後、「起動中のルール」を利用して、Places ServiceデータをAdobe Target SDKイベントに添付できます。 「起動」で目的のプロパティを選択し、次のタスクを実行して、このタイプのルールを作成できます。

## 1.ルールの作成

1. タブで、をク **[!UICONTROL Rules]**リックしま**[!UICONTROL Create New Rule]**&#x200B;す。

   次の情報に留意してください。

   * このプロパティに対する既存のルールがない場合、ボタンは画面の中央に表示されます。
   * プロパティにルールが含まれている場合、ボタンは画面の右上に表示されます。

## 2.イベントの選択

1. ルールに意味のある名前を付け、ルールのリストで簡単に認識できるようにします。

   この例では、Ruleという名前が付けられていま **[!UICONTROL Attach Places Service Data to Target Content Requested]**す。

1. セクションの下 **[!UICONTROL Events]**のをクリックしま**[!UICONTROL Add]**&#x200B;す。

1. ドロップダウ **[!UICONTROL Extension]**ンリストから、を選択しま**[!UICONTROL Adobe Target]**&#x200B;す。

1. ドロップダウ **[!UICONTROL Event Type]**ンリストから、を選択しま**[!UICONTROL Content Requested]**&#x200B;す。

1. **[!UICONTROL Keep Changes]**をクリックします。

![イベントの追加](/help/assets/ad-setEvent_target.png)

## 3.条件の追加

>[!IMPORTANT]
>
>ルールに条件を追加する場合は、この手順を実行します。 それ以外の場合は、以下の「アクシ *ョンの定義* 」に進みます。

次の例では、アプリを5回以上起動したユーザーに対してのみルールをトリガーする条件を作成します。

1. セクションの下 **[!UICONTROL Conditions]**のをクリックしま**[!UICONTROL Add]**&#x200B;す。

1. ドロップダウ **[!UICONTROL Extension]**ンリストから、を選択しま**[!UICONTROL Mobile Core]**&#x200B;す。

1. ドロップダウ **[!UICONTROL Condition Type]**ンリストから、を選択しま**[!UICONTROL Launches]**&#x200B;す。

1. 右側のウィンドウで、ドロップダウンリストと番号コントロールを変更して、条件が読み上げられるようにしま **[!UICONTROL User has launched the app greater than or equal to 5 times]**す。

1. **[!UICONTROL Keep Changes]**をクリックします。

![条件の追加](/help/assets/ad-setCondition_target.png)

## 4.アクションの定義

1. セクションの下 **[!UICONTROL Actions]**のをクリックしま**[!UICONTROL Add]**&#x200B;す。

1. ドロップダウ **[!UICONTROL Extension]**ンリストから、を選択しま**[!UICONTROL Mobile Core]**&#x200B;す。

1. ドロップダウ **[!UICONTROL Action Type]**ンリストから、を選択しま**[!UICONTROL Attach Data]**&#x200B;す。

1. 右側のウィンドウのフィールド **[!UICONTROL JSON Payload]**に、このイベントに追加するデータを入力します。

1. **[!UICONTROL Keep Changes]**をクリックします。

右側のウィンドウで、このイベントをリッスンする拡張でSDKイベントがリッスンする前に、SDKイベントにデータを追加するフリーフォームJSONペイロードを追加できます。

次の例では、Targetイベ `poiCity` ントで `poiName` 処理される各リクエ **[!UICONTROL mboxparameters]**ストのに、との値が追加されます。 新しいキーの値は、このイベントの処理時にSDKによって動的に決定されます。

>[!TIP]
>
>このJSONペイロードは、オブジェクトに特別な表記を使用 `request` します。 元のイベントでは、 `request` は匿名オブジェクトの配列です。 「Attach Data」を使用して配列内のすべてのオブジェクトにデータをアタッチする場合、配列を含むことがわかっているキーの表記法によって、その配列内のすべてのオブジェクトにペイロードが適用されます。 `[*]`
>
>の表記は、配 `request[*]` 列内の各オブジェクトにつ _いて大きく読み上げることがで`request`きる_。

![アクションを定義する](/help/assets/ad-setAction-target.png)

## 5.ルールを保存し、プロパティを再構築します

設定が完了したら、ルールが次の画像のようになっていることを確認します。

![完了規則](/help/assets/ad-ruleComplete-target.png)

1. クリック **[!UICONTROL Save]**

1. 起動プロパティを再構築し、正しい環境に展開します。
