---
title: Adobe Target
description: ここでは、Places ServiceをAdobe Targetで使用する方法について説明します。
translation-type: tm+mt
source-git-commit: d33e4e2d798c7048bdd275cdf6c0aabf3434f789
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 3%

---


# Places ServiceとAdobe Target{#places-target}を使用

このドキュメントは、アプリケーションにPlaces拡張機能が実装されていることを前提としています。 Places拡張機能の導入に関するヘルプが必要な場合は、[Places extensions](/help/places-ext-aep-sdks/places-extension/places-extension.md)を参照してください。

Places拡張機能が入口と出口のイベントを送信した後、「開始のルール」を利用して、Places ServiceデータをAdobe TargetSDKイベントに添付できます。 「起動」で目的のプロパティを選択し、次のタスクを実行して、このタイプのルールを作成できます。

## 1.ルールの作成

1. 「**[!UICONTROL ルール]**」タブで、「**[!UICONTROL 新しいルールを作成]**」をクリックします。

   次の情報に留意してください。

   * このプロパティに対する既存のルールがない場合、ボタンは画面の中央に表示されます。
   * プロパティにルールが含まれている場合、ボタンは画面の右上に表示されます。

## 2.イベントを選択します。

1. ルールに意味のある名前を付け、ルールのリストで簡単に認識できるようにします。

   この例では、ルールの名前は「**[!UICONTROL Attach Places Service Data to Places Content Requested]**」です。

1. 「**[!UICONTROL イベント]**」セクションで、「**[!UICONTROL 追加]**」をクリックします。
1. 「**[!UICONTROL 拡張子]**」ドロップダウンリストから、**[!UICONTROL Adobe Target]**&#x200B;を選択します。
1. **[!UICONTROL イベントタイプ]**&#x200B;ドロップダウンリストから、「**[!UICONTROL 要求されたコンテンツ]**」を選択します。
1. 「**[!UICONTROL 変更を保存]**」をクリックします。

![イベントの追加](/help/assets/ad-setEvent_target.png)

## 3.追加条件

>[!IMPORTANT]
>
>ルールに条件を追加する場合は、この手順を実行します。 それ以外の場合は、下の&#x200B;*アクション*&#x200B;の定義に進みます。

次の例では、条件を作成して、アプリを5回以上起動したユーザーのみにルールがトリガーされるようにしています。

1. 「**[!UICONTROL 条件]**」セクションで、「**[!UICONTROL 追加]**」をクリックします。
1. 「**[!UICONTROL 拡張子]**」ドロップダウンリストから、「**[!UICONTROL モバイルコア]**」を選択します。
1. 「**[!UICONTROL 条件のタイプ]**」ドロップダウンリストから、「**[!UICONTROL 起動回数]**」を選択します。
1. 右側のウィンドウで、「**[!UICONTROL User has launched the app launched than or equal to 5 than]**」という条件になるように、ドロップダウンリストと数値コントロールを変更します。
1. 「**[!UICONTROL 変更を保存]**」をクリックします。

![条件を追加する](/help/assets/ad-setCondition_target.png)

## 4.アクションの定義

1. 「**[!UICONTROL アクション]**」セクションで、「**[!UICONTROL 追加]**」をクリックします。
1. 「**[!UICONTROL 拡張子]**」ドロップダウンリストから、「**[!UICONTROL モバイルコア]**」を選択します。
1. 「**[!UICONTROL アクションタイプ]**」ドロップダウンリストから、「**[!UICONTROL データの添付]**」を選択します。
1. 右側のウィンドウの&#x200B;**[!UICONTROL JSON Payload]**&#x200B;フィールドに、このイベントに追加するデータを入力します。
1. 「**[!UICONTROL 変更を保存]**」をクリックします。

右側のウィンドウで、フリーフォームJSONペイロードを追加し、このイベントをリッスンする拡張機能がこのペイロードを聞く前に、SDKイベントにデータを追加できます。

次の例では、ターゲットイベントで処理されるリクエストごとに、`poiCity`と`poiName`の値が&#x200B;**[!UICONTROL mboxparameters]**&#x200B;に追加されます。 新しいキーの値は、このイベントの処理時にSDKによって動的に決定されます。

>[!TIP]
>
>このJSONペイロードは、`request`オブジェクトに特別な表記を使用します。 元のイベントでは、`request`は匿名オブジェクトの配列です。 データの添付を使用して配列内のすべてのオブジェクトにデータを添付する場合、配列を含むことがわかっているキーの`[*]`表記は、配列内のすべてのオブジェクトにペイロードを適用します。
>
>`request[*]`の表記は、`request`配列&#x200B;_内の各オブジェクトに対して_&#x200B;と読み出すことができます。

![動作を定義する](/help/assets/ad-setAction-target.png)

## 5.ルールを保存し、プロパティを再構築します

設定が完了したら、ルールが次の図のように表示されることを確認します。

![完了規則](/help/assets/ad-ruleComplete-target.png)

1. **[!UICONTROL 保存]**&#x200B;をクリックします。
1. Launchプロパティを再構築し、正しい環境に展開します。
