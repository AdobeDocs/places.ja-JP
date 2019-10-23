---
title: Placesプロパティのルールの作成
seo-title: Placesプロパティのルールの作成
description: '場所SDKは、現在の場所を追跡し、現在の場所を中心に設定済みのPOIを監視し、これらのPOIの入口イベントと出口イベントを追跡します。 '
seo-description: '場所SDKは、現在の場所を追跡し、現在の場所を中心に設定済みのPOIを監視し、これらのPOIの入口イベントと出口イベントを追跡します。 '
translation-type: tm+mt
source-git-commit: f6c92bbd4fb21999f5c96ea0df8ede6919d1bc79

---


# Placesプロパティのルールを作成する {#creating-rule-places-property}

Location Service SDKは、現在の場所を追跡し、現在の場所を中心に設定済みのPOIを監視し、これらのPOIの入口イベントと出口イベントを追跡します。

## ルール

イベント、条件、およびアクションで構成されるルールを設定できます。 各ルールは、次の内容で構成されます。

* 1つ以上のイベント
* （オプション）条件
* 1つ以上のアクション

### イベント

場所には、ルールを実行できる次のイベントがあります。

* **[!UICONTROL Enter POI]**&#x200B;に設定されているPOIに顧客が入ったときに、Places SDKによってトリガーされます。
* **[!UICONTROL Exit POI]**&#x200B;を呼び出します。これは、設定したPOIから顧客が離れたときに、Places SDKによってトリガーされます。

### 条件

条件は、イベントに関連付けられたデータ、またはそのインスタンスの拡張の共有状態が、アクションを実行するために満たす必要がある条件を定義します。 例えば、サンフランシスコ市内の喫茶店への入口に対してのみアクションをトリガーする条件を設定できます。

ロケーションサービスSDKは、次の状態を維持します。

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
>この例では、米国内のすべてのコーヒーショップのPOIライブラリを作成済みであることを前提としています。 POIとライブラリの作成について詳しくは、POIの作成を参照し [て、場所UIのライブラリの管理で](/help/poi-mgmt-ui/create-a-poi-ui.md)*ライブラリの作成を参照してください*[](/help/poi-mgmt-ui/manage-libraries-in-the-places-ui.md)。

サンフランシスコで喫茶店に入ったときにSlackに投稿を返すルールを作成する手順の例を次に示します。

イベント、条件およびアクションは、次の方法で定義します。

* **イベント**:ロケーションサービスエントリイベント。
* **条件**:現在のPOI **の市** はサンフランシスコ
* **アクション**:顧客が入力したコーヒーショップの名前をSlackにポストバックします。

### 前提条件

ルールを作成する前に、Experience Platform Launchでデータ要素を作成する必要があります。 データ要素は、ポストバックメッセージにPOIに関する必要な情報を自動的に入力します。

エクスペリエンスプラットフォームの起動でデータ要素を作成するには：

1. Click the **[!UICONTROL Data Elements]** tab.
2. 「**[!UICONTROL Add Data Element]**」をクリックします。
3. Type a name, for example, **[!UICONTROL Current coffee shop name]**.
4. ドロップダ **[!UICONTROL Extension]** ウンリストで、を選択しま **[!UICONTROL Places – Beta]**&#x200B;す。
5. で、を **[!UICONTROL Data Element]**&#x200B;選択しま **[!UICONTROL City]**&#x200B;す。
6. 右側のウィンドウで、「現在のPOI」 **を選択します**。
7. 「**[!UICONTROL Save]**」をクリックします。

### Experience Platform Launchでのロケーションサービス用のルールの作成

![](//help/assets/create-a-rule.png)

1. 「エクスペリエンスプラットフォームの起動」で、タブをクリ **[!UICONTROL Rules]** ックします。
2. 「**Add Rule**」をクリックします。
3. ルールの名前を入力します(例：SFのコーヒーショ **ップのトラックエントリ**)。

### イベントの作成

1. 「イベント」セクションで、をクリックしま **[!UICONTROL + Add]**&#x200B;す。 イベントは、ルールを実行するタイミングを決定します。
2. ドロップダ **[!UICONTROL Extension]** ウンリストで、を選択しま **[!UICONTROL Places – Beta]**&#x200B;す。
3. ドロップダ **[!UICONTROL Event Type]** ウンリストで、を選択しま **[!UICONTROL Enter POI]**&#x200B;す。
4. に、 **[!UICONTROL Name]**&#x200B;イベントの名前（例：）を入力します **[!UICONTROL Entering a coffee shop]**。
5. 「**[!UICONTROL Keep Changes]**」をクリックします。

### 条件の作成

1. 「条件」セクションで、をクリックしま **[!UICONTROL +Add]**&#x200B;す。 条件は、アクションを実行するために満たす必要がある条件を決定します。
2. で、「 **[!UICONTROL Logic Type]**&#x200B;標準」を選択します。これにより、条件が満たされた場合にアクションを実行できます。
3. 「拡張」ド **ロップダウン** ・リストで、「」を選択しま **[!UICONTROL Places – Beta]**&#x200B;す。
4. で、を **[!UICONTROL Condition Type]**&#x200B;選択しま **[!UICONTROL City]**&#x200B;す。
5. Type a condition name, for example, **[!UICONTROL Coffee shop in SF]**.
6. 右側のウィンドウでをクリ **[!UICONTROL Current POI]**&#x200B;ックし、ドロップダウンリストで都市の1 **[!UICONTROL San Francisco]** つとして選択します。
7. 「**[!UICONTROL Keep Changes]**」をクリックします。

### アクションの作成

1. セクションで **[!UICONTROL Actions]** 「+追加」をク **[!UICONTROリックします]**。
2. 「拡張機能」ド **[!UICONTRO ロップダウンリストで]** 、デフォルトの「 **[!UICONTRO Mobile Core]** 」オプションを選択したままにします。
3. アクションのタイプを選択します(例：「ポストバック **[!UICONTRO を送信」]**)。

   a.「」 **[!UICONTROL URL]**&#x200B;に、SlackのポストバックURLを入力します(例： `https://hooks.slack.com/services/`)。

   b.投稿の本文を送信するには、「投稿の本文を追加」チ **[!UICONTRO ェックボックスを]** 選択します。

   c.「投 **[!UICONTRO 稿本文]**」で、次のように投稿本文を追加します。 `{ "text": "A customer has entered" }`

   c.コンテンツタイプ(例： **[!UICONTRO application/json)を入力します]**。

   d.タイムアウト値(例： **5**)を選択します。

4. Click **[!UICONTRO Keep Changes]**.

### ルールの発行

1. ルールをアクティブ化するには、ルールを発行する必要があります。 エクスペリエンスプラットフォームの起動でのルールの発行について詳しくは、「発行」を参照し [てくださ](https://docs.adobelaunch.com/launch-reference/publishing)い。