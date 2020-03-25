---
title: Adobe Target
description: この節では、Places ServiceをAdobe Targetと共に使用する方法について説明します。
translation-type: tm+mt
source-git-commit: d33e4e2d798c7048bdd275cdf6c0aabf3434f789

---


# Adobe TargetでのPlacesサービスの使用 {#places-target}

このドキュメントでは、Places拡張機能がアプリケーションに実装されていることを前提としています。 Places拡張機能の導入に関するヘルプが必要な場合は、Places拡張機能を参照 [してくださ](/help/places-ext-aep-sdks/places-extension/places-extension.md)い。

Places拡張が入口と出口のイベントを送信した後、「開始のルール」を利用して、Places ServiceデータをAdobe Target SDKイベントに添付できます。 「起動」で目的のプロパティを選択し、次のタスクを実行して、このタイプのルールを作成できます。

## 1.ルールの作成

1. タブで、をク **[!UICONTROL Rules]** リックしま **[!UICONTROL Create New Rule]**&#x200B;す。

   次の情報に留意してください。

   * このプロパティに対する既存のルールがない場合、ボタンは画面の中央に表示されます。
   * プロパティにルールが含まれている場合、ボタンは画面の右上に表示されます。

## 2.イベントの選択

1. ルールのリストで簡単に認識できるように、意味のある名前を付けます。

   この例では、Ruleという名前が付けられていま **[!UICONTROL Attach Places Service Data to Target Content Requested]**&#x200B;す。

1. Under the **[!UICONTROL Events]** section, click **[!UICONTROL Add]**.
1. ドロップダ **[!UICONTROL Extension]** ウンリストから、を選択しま **[!UICONTROL Adobe Target]**&#x200B;す。
1. ドロップダ **[!UICONTROL Event Type]** ウンリストから、を選択しま **[!UICONTROL Content Requested]**&#x200B;す。
1. 「**[!UICONTROL Keep Changes]**」をクリックします。

![イベントの追加](/help/assets/ad-setEvent_target.png)

## 3.条件の追加

>[!IMPORTANT]
>
>ルールに条件を追加する場合は、この手順を実行します。 それ以外の場合は、以下の「アクショ *ンの定義* 」に進みます。

次の例では、アプリを5回以上起動したユーザーに対してのみルールをトリガーする条件を作成します。

1. Under the **[!UICONTROL Conditions]** section, click **[!UICONTROL Add]**.
1. ドロップダ **[!UICONTROL Extension]** ウンリストから、を選択しま **[!UICONTROL Mobile Core]**&#x200B;す。
1. ドロップダ **[!UICONTROL Condition Type]** ウンリストから、を選択しま **[!UICONTROL Launches]**&#x200B;す。
1. 右側のウィンドウで、ドロップダウンリストと数値コントロールを変更し、条件が読み上げられるようにしま **[!UICONTROL User has launched the app greater than or equal to 5 times]**&#x200B;す。
1. 「**[!UICONTROL Keep Changes]**」をクリックします。

![条件の追加](/help/assets/ad-setCondition_target.png)

## 4.アクションの定義

1. Under the **[!UICONTROL Actions]** section, click **[!UICONTROL Add]**.
1. ドロップダ **[!UICONTROL Extension]** ウンリストから、を選択しま **[!UICONTROL Mobile Core]**&#x200B;す。
1. ドロップダ **[!UICONTROL Action Type]** ウンリストから、を選択しま **[!UICONTROL Attach Data]**&#x200B;す。
1. 右側のウィンドウのフィールドで、 **[!UICONTROL JSON Payload]** このイベントに追加するデータを入力します。
1. 「**[!UICONTROL Keep Changes]**」をクリックします。

右側のウィンドウで、このイベントをリッスンする拡張でSDKイベントがリッスンする前に、SDKイベントにデータを追加するフリーフォームJSONペイロードを追加できます。

次の例では、Targetイベ `poiCity` ント `poiName` で処理される各リクエ **[!UICONTROL mboxparameters]** ストのに、およびの値が追加されます。 新しいキーの値は、このイベントの処理時にSDKによって動的に決定されます。

>[!TIP]
>
>このJSONペイロードは、オブジェクトに特別な表記を使用 `request` します。 元のイベントでは、は `request` 匿名オブジェクトの配列です。 「データを添付」を使用して配列内のすべてのオブジェクトにデータを添付する場合、配列を含むことがわかっているキーの表記によって、その配列内のすべてのオブジェクトにペイロードが適用されます。 `[*]`
>
>の表記は、配 `request[*]` 列内の各オブジェク _トのように大きく読み上げ`request`る_。

![アクションを定義する](/help/assets/ad-setAction-target.png)

## 5.ルールを保存し、プロパティを再構築する

設定が完了したら、ルールが次の図のように表示されることを確認します。

![完了規則](/help/assets/ad-ruleComplete-target.png)

1. **[!UICONTROL Save]** をクリックします。
1. 起動プロパティを再構築し、正しい環境に展開します。
