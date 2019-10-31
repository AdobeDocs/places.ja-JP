---
title: Placesプロパティのルールの作成
seo-title: Placesプロパティのルールの作成
description: '場所SDKは、現在の場所を追跡し、現在の場所を中心に設定済みのPOIを監視し、これらのPOIの入口イベントと出口イベントを追跡します。 '
seo-description: '場所SDKは、現在の場所を追跡し、現在の場所を中心に設定済みのPOIを監視し、これらのPOIの入口イベントと出口イベントを追跡します。 '
translation-type: tm+mt
source-git-commit: 84b23934a6e9f9fd61c068693bae3daca24de253

---


# 入口ルールと出口ルールの作成 {#create-entry-exit-rules}

モバイルアプリケーションにプレースモニター拡張機能がインストールされている場合、Adobe Experience Platform Launchで、場所の入口イベントや出口イベントなど、場所のデータをトリガーまたは条件付きで表示するルールを作成できます。

## ルール

イベント、条件、およびアクションで構成されるルールを設定できます。 各ルールは、次の内容で構成されます。

* 1つ以上のイベント
* （オプション）条件
* 1つ以上のアクション

### 場所イベント

場所には、ルールを実行できる次のイベントがあります。

* **POIと入力します**。これは、設定したPOIに顧客が入ったときにPlaces SDKによってトリガーされます。
* **出口POI**。顧客が設定したPOIを離れると、Places SDKによってトリガーされます。

### 配置条件

条件は、イベントに関連付けられたデータ、またはそのインスタンスの拡張の共有状態が、アクションを実行するために満たす必要がある条件を定義します。 例えば、サンフランシスコ市内の喫茶店への入口に対してのみアクションをトリガーする条件を設定できます。

配置SDKは次の状態を維持します。

* 現在のPOIは、お客様の現在の所在地のPOIを指します。
* POIから離脱した最後のPOIは、顧客が最後に離脱したPOIを指します。
* 最後に入力されたPOIは、顧客が入力した最新のPOIを指します。

各POIには、次のデータ要素が含まれます。

* ID
* 名前:
* 緯度/経度
* 半径
* 市、国、州、カテゴリなどのメタデータ

### アクション

アクションは、発生したイベントでルールが満たされた場合にアプリが実行する動作を定義します。 例えば、顧客がPOIを入力したときに、モバイルデバイスに表示するようにお知らせメッセージを設定できます。

## ルールの作成：例

>[!CAUTION]
>
>この例では、米国内のすべてのコーヒーショップのPOIライブラリを作成済みであることを前提としています。 POIとライブラリの作成について詳しくは、「POIの作成」と「複数のラ [イブラリの管理](/help/poi-mgmt-ui/create-a-poi-ui.md)** 」を [参照してください](https://docs.adobe.com/content/help/en/places/using/poi-mgmt-ui/manage-libraries-in-the-places-ui.html)。

サンフランシスコで喫茶店に入ったときにSlackに投稿を返すルールを作成する手順の例を次に示します。

イベント、条件およびアクションは、次の方法で定義します。

* **イベント**:エントリイベントを配置します。
* **条件**:現在のPOI **の市** はサンフランシスコ
* **アクション**:顧客が入力したコーヒーショップの名前をSlackにポストバックします。

### 前提条件

ルールを作成する前に、Adobe Experience Platform Launchでデータ要素を作成する必要があります。 データ要素は、ポストバックメッセージにPOIに関する必要な情報を自動的に入力します。

エクスペリエンスプラットフォームの起動でデータ要素を作成するには：

1. 「データ要素」 **タブをクリックします** 。
2. Click **Add Data Element**.
3. 「現在の喫茶店名」などの名前 **を入力します**。
4. 「拡張機能」 **ドロップダウン** ・リストで **、「場所 — ベータ」**&#x200B;を選択します。
5. 「デー **タ要素**」で「市区町村 **」を選択**&#x200B;します。
6. 右側のウィンドウで、「現在のPOI」 **を選択します**。
7. **保存** をクリックします。

### Experience Platform Launchでの場所のルールの作成

![ルールの作成](/help/assets/placesrule.png)

1. 「エクスペリエンスプラットフォームの起動」で、タブをクリ **[!UICONTROL Rules]** ックします。
2. 「**[!UICONTROL Add Rule]**」をクリックします。
3. 例えば、ルールの名前を入力します **[!UICONTROL Track entry for coffee shop in SF]**。

### イベントの作成

1. 「イベント」セクションで、をクリックしま **[!UICONTROL + Add]**&#x200B;す。 イベントは、ルールを実行するタイミングを決定します。
2. ドロップダ **[!UICONTROL Extension]** ウンリストで、を選択しま **[!UICONTROL Places – Beta]**&#x200B;す。
3. ドロップダ **[!UICONTROL Event Type]** ウンリストで、を選択しま **[!UICONTROL Enter POI]**&#x200B;す。
4. に、 **[!UICONTROL Name]**&#x200B;イベントの名前（例：）を入力します **[!UICONTROL Entering a coffee shop]**。
5. 「**[!UICONTROL Keep Changes]**」をクリックします。

### 条件の作成

1. 「条件」セクションで、をクリックしま **[!UICONTROL +Add]**&#x200B;す。 条件は、アクションを実行するために満たす必要がある条件を決定します。
2. で、「 **[!UICONTROL Logic Type]**&#x200B;標準」を選択します。これにより、条件が満たされた場合にアクションを実行できます。
3. ドロップダ **[!UICONTROL Extension]** ウンリストで、を選択しま **[!UICONTROL Places – Beta]**&#x200B;す。
4. で、を **[!UICONTROL Condition Type]**&#x200B;選択しま **[!UICONTROL City]**&#x200B;す。
5. Type a condition name, for example, **[!UICONTROL Coffee shop in SF]**.
6. 右側のウィンドウでをクリ **[!UICONTROL Current POI]**&#x200B;ックし、ドロップダウンリストで都市の1 **[!UICONTROL San Francisco]** つとして選択します。
7. 「**[!UICONTROL Keep Changes]**」をクリックします。

### アクションの作成

1. In the **[!UICONTROL Actions]** section, click **[!UICONTROL + Add]**.
2. ドロップダウン **[!UICONTROL Extension]** リストで、デフォルトのオプションを選択したま **[!UICONTROL Mobile Core]** まにします。
3. 例えば、アクションのタイプを選択しま **[!UICONTROL Send Postback]**&#x200B;す。

   a.「」 **[!UICONTROL URL]**&#x200B;に、SlackのポストバックURLを入力します(例： `https://hooks.slack.com/services/`)。

   b.投稿の本文を送信するには、チェックボックスを **[!UICONTROL Add Post Body]** 選択します。

   c.で、 **[!UICONTROL Post Body]**&#x200B;次のように投稿の本文を追加します。 `{ "text": "A customer has entered" }`

   c.例えば、コンテンツタイプを入力しま **[!UICONTROL application/json]**&#x200B;す。

   d.例えば、タイムアウト値を選択します **[!UICONTROL 5]**。

4. 「**[!UICONTROL Keep Changes]**」をクリックします。

### ルールの発行

1. ルールをアクティブ化するには、ルールを発行する必要があります。 エクスペリエンスプラットフォームの起動でのルールの発行について詳しくは、「発行」を参照し [てくださ](https://docs.adobelaunch.com/launch-reference/publishing)い。

### 入口と出口を越えた考え方

ロケーションサービスの地域フェンスのエントリと出口を使用して、エクスペリエンスプラットフォーム起動でルールをトリガーするのは非常に強力ですが、場所データを他のイベントの発生条件として使用することもできます。 例えば、アプリ内の特定のtrackAction呼び出しイベントに基づいて、Mobileコア追跡アクションイベントトリガーを起動する準備が整っているとします。 このイベントに基づいて、アクションが実行される前にイベントに追加の場所条件を設定できます。 例えば、購入イベントが発生した場合にアプリ内調査を開き、ユーザーの現在の場所に特定のロケーショ `trackAction` ン **** サービスメタデータが含まれている場合にのみ調査を開きます。

![条件を作成する](/help/assets/places-condition.png)