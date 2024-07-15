---
title: Analytics リクエストへの場所コンテキストの追加
description: この節では、Analytics リクエストに場所コンテキストを追加する方法について説明します。
exl-id: bee7b6e3-a75b-4a07-b6e2-f93ce33aa042
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 2%

---

# Analytics リクエストへの場所コンテキストの追加 {#run-reports-aa-locserv-data}

>[!IMPORTANT]
>
>このドキュメントは、アプリケーションに Places Service が実装されていることを前提としています。 Places Service の実装について詳しくは、[Places 拡張機能 ](/help/places-ext-aep-sdks/places-extension/places-extension.md) を参照してください。

Places Service が入口イベントと出口イベントを送信した後、Experience Platform Launchでルールを作成し、Places Service データをすべてのAdobe Analytics イベントに添付できます。 このタイプのルールを作成するには、Launch でプロパティを選択し、次の手順を実行します。

## 1. ルールを作成する

1. 「**[!UICONTROL ルール]**」タブで、「**[!UICONTROL 新規ルールを作成]**」をクリックします。

   次の情報に留意してください。
   * このプロパティに既存のルールがない場合、「**[!UICONTROL 新しいルールの作成]**」ボタンが画面の中央にあります。
   * プロパティにルールがある場合、「**[!UICONTROL 新しいルールを作成]**」ボタンが画面の右上に表示されます。

## 2. イベントを選択する

1. ルールのリスト内でルールがわかりやすい名前を付けると、簡単に認識できます。

   この例では、ルールの名前は **[!UICONTROL Analytics 追跡アクションイベントにサービスデータを添付]** です。

1. 「**[!UICONTROL イベント]**」セクションで、「**[!UICONTROL 追加]**」をクリックします。

1. **[!UICONTROL 拡張機能]** ドロップダウンリストから、「**[!UICONTROL Mobile Core]**」を選択します。

1. **[!UICONTROL イベントタイプ]** ドロップダウンリストから「**[!UICONTROL アクションをトラック]**」を選択します。

これで、このルールに含めるトリガーを決定できます。 この例では、トリガーはすべての `TrackAction` 呼び出しに基づいています。 イベントを設定したら、「**[!UICONTROL 変更を保持]**」をクリックします。

![ イベントの作成」 ](/help/assets/ad-setEvent_use-analytics-data.png)


## 3.条件を追加

>[!IMPORTANT]
>
>ルールに条件を追加するには、次の手順を実行します。 それ以外の場合は、以下の *アクションの定義* の節にスキップします。

この例では、AT&amp;T の顧客に対してのみルールをトリガーにする条件を作成します。

1. 「**[!UICONTROL 条件]**」セクションで、「**[!UICONTROL 追加]**」をクリックします。

1. **[!UICONTROL 拡張機能]** ドロップダウンリストから、「**[!UICONTROL Mobile Core]**」を選択します。

1. **[!UICONTROL 条件タイプ]** ドロップダウンリストから、「**[!UICONTROL 通信事業者名]**」を選択します。

1. 右側のウィンドウで、「**[!UICONTROL AT&amp;T]**」チェックボックスを選択します。

1. 「**[!UICONTROL 変更を保存]**」をクリックします。

![ 「条件の作成」 ](/help/assets/ad-setCondition_use-analytics-data.png)

## 4. アクションを定義する

1. 「**[!UICONTROL アクション]**」セクションで、「**[!UICONTROL 追加]**」をクリックします。

1. **[!UICONTROL 拡張機能]** ドロップダウンリストから、「**[!UICONTROL Mobile Core]**」を選択します。

1. **[!UICONTROL アクションタイプ]** ドロップダウンリストから「**[!UICONTROL データを添付]**」を選択します。

1. 右側のペインの「**[!UICONTROL JSON ペイロード]**」フィールドに、このイベントに追加するデータを入力します。

1. 「**[!UICONTROL 変更を保存]**」をクリックします。

右側のパネルでは、SDK イベントにデータを追加するフリーフォーム JSON ペイロードを追加してから、このイベントをリッスンしている拡張機能でイベントをリッスンすることができます。 この例では、Analytics 拡張機能が処理する前に、一部のコンテキストデータがこのイベントに追加されます。 追加されたコンテキストデータは、送信する Analytics ヒットに含まれるようになります。

次の例では、`poi.city` と `poi.name` の値を Analytics イベントのコンテキストデータに追加します。 新しいキーの値は、このイベントの処理時に SDK によって動的に決定されます。

![ 「アクションを作成」 ](/help/assets/ad-setAction_use-analytics-data.png)

## 5. ルールを保存し、プロパティを再構築する

設定が完了したら、ルールが次の画像のようになっていることを確認します。

![ 「ルールは完了しました。」 ](/help/assets/ad-ruleComplete_use-analytics-data.png)

1. **[!UICONTROL 保存]**&#x200B;をクリックします。

1. Launch プロパティを再構築し、正しい環境にデプロイします。
