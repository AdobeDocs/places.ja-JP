---
title: Places Serviceプロパティ用のルールの作成
description: '配置SDKは、現在の場所を追跡し、現在の場所の周りで設定済みのPOIを監視し、これらのPOIの入口と出口のイベントを追跡します。 '
translation-type: tm+mt
source-git-commit: c22efc36f2eac6b20fc555d998c3988d8c31169e
workflow-type: tm+mt
source-wordcount: '866'
ht-degree: 7%

---


# 入口ルールと出口ルールの作成 {#create-entry-exit-rules}

Places拡張機能とPlaces Monitor拡張機能をモバイルアプリケーションにインストールすると、場所の入口データや出口イベントを含む、トリガーまたは条件付きの場所データを、Adobe Experience Platform Launchでルールを作成できます。

## ルール

イベント、条件、およびアクションで構成されるルールを設定できます。 各ルールは、次の内容で構成されます。

* 1つ以上のイベント
* （オプション）条件
* 1つ以上のアクション

### Placesサービスイベント

サービスオファーに、ルールを実行できる次のイベントを配置します。

* **POI**&#x200B;と入力します。これは、設定したPOIに顧客が入ったときに、Places SDKによってトリガーされます。
* **出口POI**。顧客が設定したPOIから離れたときに、Places SDKによってトリガーされます。

### サービス条件を配置

条件は、イベントに関連付けられたデータ、またはそのインスタンスの拡張の共有状態が、アクションを実行するために満たす必要がある条件を定義します。 例えば、サンフランシスコの町のみの喫茶店への入口に対してアクションをトリガーする条件を設定できます。

配置SDKは次の状態を維持します。

* 現在のPOI。顧客の所在地のPOIを指します。
* 最後に離脱したPOI。顧客が最後に離脱したPOIを示します。
* 最後に入力されたPOI。顧客が入力した最新のPOIを示します。

各POIには、次のデータ要素が含まれます。

* ID
* 名前
* 緯度/経度
* 半径
* 市区町村、国、州、カテゴリなどのメタデータ

### アクション

アクションは、呼び出されたイベントがルールの条件を満たした場合にアプリが実行する動作を定義します。 例えば、顧客がPOIを入力した場合に、モバイルデバイスに表示するようにお知らせメッセージを設定できます。

## ルールの作成：例

>[!CAUTION]
>
>この例では、米国内の全コーヒーショップの POI ライブラリを作成済みであることを前提としています。For more information about creating POIs and libraries, see [Create a POI](/help/poi-mgmt-ui/create-a-poi-ui.md) and *Create a Library* in [Manage multiple libraries](https://docs.adobe.com/content/help/en/places/using/poi-mgmt-ui/manage-libraries-in-the-places-ui.html).

以下の手順は、サンフランシスコで喫茶店に入ったときにSlackに投稿を返すルールの作成方法の例です。

イベント、条件およびアクションは、次の方法で定義します。

* **イベント**:入力イベントを配置します。
* **条件**：**現在の POI** の市区町村はサンフランシスコ
* **アクション**:顧客が入力した喫茶店の名前をSlackにポストバックします。

### 前提条件

ルールを作成する前に、Adobe Experience Platform Launchでデータ要素を作成する必要があります。 データ要素は、ポストバックメッセージにPOIに関して必要な情報を自動的に入力します。

Experience Platform Launchでデータ要素を作成するには：

1. 「 **データ要素** 」タブをクリックします。
1. Click **Add Data Element**.
1. 名前を入力します(例： **現在の喫茶店名**)。
1. 「 **拡張子** 」ドロップダウンリストで、「 **場所**— ベータ版」を選択します。
1. 「**データ要素**」で「**市区町村**」を選択します。
1. 右側のウィンドウで、「 **現在のPOI**」を選択します。
1. 「**保存**」をクリックします。

### Places ServiceのExperience Platform Launchでのルールの作成

![ルールの作成](/help/assets/placesrule.png)

1. In Experience Platform Launch, click the **[!UICONTROL Rules]** tab.
1. 「**[!UICONTROL Add Rule]**」をクリックします。
1. ルールの名前を入力します(例： **[!UICONTROL Track entry for coffee shop in SF]**)。

### イベントの作成

1. In the Events section, click **[!UICONTROL + Add]**. イベントは、ルールをいつ実行するかを決定します。
1. In the **[!UICONTROL Extension]** drop-down list, select **[!UICONTROL Places – Beta]**.
1. In the **[!UICONTROL Event Type]** drop-down list, select **[!UICONTROL Enter POI]**.
1. に、 **[!UICONTROL Name]**&#x200B;イベントの名前を入力します(例： **[!UICONTROL Entering a coffee shop]**)。
1. 「**[!UICONTROL Keep Changes]**」をクリックします。

### 条件の作成

1. In the Conditions section, click **[!UICONTROL +Add]**. 条件は、アクションを実行するために満たす必要がある条件を決定します。
1. In **[!UICONTROL Logic Type]**, select Regular, which allows actions to execute if the condition is met.
1. In the **[!UICONTROL Extension]** drop-down list, select **[!UICONTROL Places – Beta]**.
1. 「**[!UICONTROL Condition Type]**」で、「**[!UICONTROL City]**」を選択します。
1. 例えば、条件名を入力し **[!UICONTROL Coffee shop in SF]**&#x200B;ます。
1. In the right pane, click **[!UICONTROL Current POI]**, and in the drop-down list, select **[!UICONTROL San Francisco]** as one of your cities.
1. 「**[!UICONTROL Keep Changes]**」をクリックします。

### アクションの作成

1. 「**[!UICONTROL Actions]**」セクションで、「**[!UICONTROL + Add]**」をクリックします。
1. ドロップダウン **[!UICONTROL Extension]** リストで、デフォルトの **[!UICONTROL Mobile Core]** オプションを選択したままにします。
1. 例えば、アクションタイプを選択し **[!UICONTROL Send Postback]**&#x200B;ます。

   a.に、Slack **[!UICONTROL URL]**&#x200B;のポストバックURLを入力します(例： `https://hooks.slack.com/services/`)。

   b.投稿の本文を送信するには、チェックボックスをオンにし **[!UICONTROL Add Post Body]** ます。

   c.で、投稿本文 **[!UICONTROL Post Body]**&#x200B;を追加します。例： `{ "text": "A customer has entered" }`

   c.例えば、コンテンツタイプを入力し **[!UICONTROL application/json]**&#x200B;ます。

   d.例えば、タイムアウト値を選択し **[!UICONTROL 5]**&#x200B;ます。

1. 「**[!UICONTROL Keep Changes]**」をクリックします。

### ルールを発行する

1. ルールをアクティブ化するには、発行する必要があります。 Experience Platform Launchでのルールの発行について詳しくは、 [発行を参照してください](https://docs.adobe.com/content/help/ja-JP/launch/using/reference/publish/overview.html)。

### 入口と出口を越えた考え方

Places Service Geo-fenceのエントリと出口を使用してExperience Platform Launch内のルールをトリガーするのは非常に強力ですが、場所データを他のイベントが実行する条件として使用することもできます。 例えば、アプリ内の特定のtrackAction呼び出しイベントに基づいて、モバイルコア追跡アクションイベントトリガーを起動する準備ができているとします。 このイベントに基づいて、アクションが実行される前に、追加の場所条件をイベントに配置できます。 例えば、購入 `trackAction` イベントが発生した場合にアプリ内調査を開き、ユーザーの現在の場所に特定のPlaces Serviceメタデータが含まれている場合にの **** み表示します。

![条件を作る](/help/assets/places-condition.png)