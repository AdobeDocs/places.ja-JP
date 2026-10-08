---
title: Adobe Target
description: この節では、Adobe TargetでPlaces サービスを使用する方法について説明します。
exl-id: 6ee91fca-ea48-4de2-8dcf-87981813c678
TQID: https://experienceleague.adobe.com/WsfkEJD0mN5aYKETjcnqiC13dVe5NPYeKfOCTOK82uE
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
    internal-label: CX Enterprise
  - id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
    internal-label: Target
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
feature_v2:
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
    internal-label: Data collection
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
    internal-label: Places
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
source-git-commit: d8704da9c84a066f72471421290d4b46c65f41e1
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 4%
---
# Adobe TargetでのPlaces サービスの使用 {#places-target}

このドキュメントでは、アプリケーションにPlaces拡張機能が実装されていることを前提としています。 Places拡張機能の実装に関するサポートが必要な場合は、[Places拡張機能](/help/places-ext-aep-sdks/places-extension/places-extension.md)を参照してください。

Places拡張機能がエントリと離脱に対してイベントを送信すると、Launchのルールを活用して、Places サービスのデータをAdobe Target SDK イベントに添付できます。 Launchで目的のプロパティを選択した状態で、次のタスクを実行することで、このタイプのルールを作成できます。

## &#x200B;1. ルールの作成

1. 「**[!UICONTROL ルール]**」タブで、**[!UICONTROL 新しいルールを作成]**&#x200B;をクリックします。

   次の情報に留意してください。

   * このプロパティに既存のルールがない場合、ボタンは画面の中央に表示されます。
   * プロパティにルールがある場合、ボタンは画面の右上に表示されます。

## &#x200B;2. イベントの選択

1. ルールに意味のある名前を付けると、ルールのリストで簡単に認識できます。

   この例では、ルールの名前は&#x200B;**[!UICONTROL Attach Places Service Data to Target Content Requested]**&#x200B;です。

1. **[!UICONTROL イベント]** セクションで、**[!UICONTROL 追加]**&#x200B;をクリックします。
1. **[!UICONTROL 拡張機能]** ドロップダウンリストから、**[!UICONTROL Adobe Target]**&#x200B;を選択します。
1. 「**[!UICONTROL イベントタイプ]**」ドロップダウンリストから、「**[!UICONTROL 要求されたコンテンツ]**」を選択します。
1. 「**[!UICONTROL 変更を保存]**」をクリックします。

![&#x200B; イベントを追加](/help/assets/ad-setEvent_target.png)

## &#x200B;3. 条件を追加

>[!IMPORTANT]
>
>ルールに条件を追加する場合は、この手順を実行します。 それ以外は、以下の「*アクションを定義*」にスキップします。

次の例では、アプリを5回以上起動したユーザーに対してのみルールをトリガーにする条件が作成されています。

1. **[!UICONTROL 条件]** セクションで、**[!UICONTROL 追加]**&#x200B;をクリックします。
1. **[!UICONTROL 拡張機能]** ドロップダウンリストから、**[!UICONTROL モバイルコア]**&#x200B;を選択します。
1. **[!UICONTROL 条件タイプ]** ドロップダウンリストから、**[!UICONTROL 起動]**&#x200B;を選択します。
1. 右側のペインで、条件に「**[!UICONTROL ユーザーが5回以上アプリを起動しました]**」と表示されるように、ドロップダウンリストと数値制御を変更します。
1. 「**[!UICONTROL 変更を保存]**」をクリックします。

![条件を追加](/help/assets/ad-setCondition_target.png)

## &#x200B;4. アクションを定義

1. 「**[!UICONTROL アクション]**」セクションで、**[!UICONTROL 追加]**&#x200B;をクリックします。
1. **[!UICONTROL 拡張機能]** ドロップダウンリストから、**[!UICONTROL モバイルコア]**&#x200B;を選択します。
1. 「**[!UICONTROL アクションタイプ]**」ドロップダウンリストから、「**[!UICONTROL データを添付]**」を選択します。
1. 右側のペインの&#x200B;**[!UICONTROL JSON ペイロード]** フィールドに、このイベントに追加するデータを入力します。
1. 「**[!UICONTROL 変更を保存]**」をクリックします。

右側のペインでは、このイベントをリッスンする拡張機能がリッスンする前にSDK イベントにデータを追加するフリーフォーム JSON ペイロードを追加できます。

次の例では、Target イベントで処理されるリクエストごとに`poiCity`と`poiName`の値が&#x200B;**[!UICONTROL mboxparameters]**&#x200B;に追加されています。 新しいキーの値は、このイベントプロセス時にSDKによって動的に決定されます。

>[!TIP]
>
>このJSON ペイロードは、`request` オブジェクトに特別な表記法を使用します。 元のイベントでは、`request`は匿名オブジェクトの配列です。 データの添付を使用して配列内のすべてのオブジェクトにデータを添付する場合、配列を含んでいることがわかっているキーの`[*]`表記により、その配列内のすべてのオブジェクトにペイロードが適用されます。
>
>`request[*]`の表記法は、`request`配列&#x200B;_の各オブジェクトについて_&#x200B;として読み上げることができます。

![&#x200B; アクションを定義](/help/assets/ad-setAction-target.png)

## &#x200B;5. ルールを保存し、プロパティを再構築する

設定が完了したら、ルールが次の画像のようになっていることを確認します。

![&#x200B; ルールを完了しました](/help/assets/ad-ruleComplete-target.png)

1. 「**[!UICONTROL 保存]**」をクリックします。
1. Launch プロパティを再構築し、正しい環境にデプロイします。
