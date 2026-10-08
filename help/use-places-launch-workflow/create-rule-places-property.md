---
title: Places サービスプロパティのルールの作成
description: Places SDKは、現在の場所を追跡し、現在の場所に設定されたPOIをモニタリングし、これらのPOIの入退出イベントをトラッキングします。
exl-id: dd5aa7ac-55f9-44dc-8632-e483ef3b91a0
TQID: https://experienceleague.adobe.com/jyGVmk-oKX6-5vxZBx6Mz-QF8SBYxAWssvAxJ0QLYWQ
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
    internal-label: CX Enterprise
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
    internal-label: Analytics
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
feature_v2:
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
    internal-label: Data collection
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
    internal-label: Places
  - id: f9a2105e-7a47-4e85-9193-31a519a2cb83
    internal-label: Data elements
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
    internal-label: Metadata
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
source-git-commit: d8704da9c84a066f72471421290d4b46c65f41e1
workflow-type: tm+mt
source-wordcount: '939'
ht-degree: 13%
---
# 入口と出口のルールの作成 {#create-entry-exit-rules}

Places拡張機能とリージョンモニタリングソリューションをモバイルアプリケーションにインストールすると、位置情報の入力イベントや終了イベントなどの位置情報をトリガーまたは条件とするルールをAdobe Experience Platform Launchで作成できます。

## ルール

イベント、条件、アクションで構成されるルールを設定できます。 各ルールは、次の要素で構成されます。

* 1つ以上のイベント
* （オプション）条件
* 1つ以上のアクション

### Places サービスイベント

Places サービスには、ルールを実行できる次のイベントが用意されています。

* **POI**&#x200B;を入力します。これは、お客様が設定したPOIを入力したときにPlaces SDKによってトリガーされます。
* **POI**&#x200B;を終了します。これは、お客様が設定したPOIを終了したときにPlaces SDKによってトリガーされます。

### Places サービス条件

条件は、イベントに関連付けられたデータ、またはそのインスタンスでの拡張機能の共有状態が、アクションを実行するために満たす必要がある基準を定義します。 例えば、条件を設定して、サンフランシスコ市でのみコーヒーショップへのエントリに対するアクションをトリガーできます。

Places SDKでは、次のステートが維持されます。

* 現在のPOI：顧客が現在配置されているPOI。
* 最後に離脱したPOI。顧客が離脱した最新のPOIを指します。
* 最後に入力したPOI。顧客が入力した最新のPOIを指します。

各POIには、次のデータ要素が含まれます。

* ID
* 名前
* 緯度/経度
* 半径
* 都市、国、州、カテゴリーなどのメタデータ

### アクション

アクションは、発火したイベントのルールが満たされた場合にアプリが実行する処理を定義します。 例えば、顧客がPOIを入力したときに、ウェルカムメッセージをモバイルデバイスに表示するように設定できます。

## ルールの作成：例

>[!CAUTION]
>
>この例では、米国内の全コーヒーショップの POI ライブラリを作成済みであることを前提としています。 POIとライブラリの作成について詳しくは、[POIの作成](/help/poi-mgmt-ui/create-a-poi-ui.md)および&#x200B;*ライブラリの作成*&#x200B;を[複数ライブラリの管理](https://experienceleague.adobe.com/docs/places/using/poi-mgmt-ui/manage-libraries-in-the-places-ui.html)で参照してください。

次の手順は、サンフランシスコのコーヒーショップに入ったときにSlackに投稿を送り返すルールを作成する方法の例です。

イベント、条件、アクションは、次の方法で定義されます。

* **イベント**: エントリイベントを配置します。
* **条件**：**現在の POI** の市区町村はサンフランシスコ
* **アクション**：お客様が入力したコーヒーショップの名前をSlackにポストバックします。

### 前提条件

ルールを作成する前に、Adobe Experience Platform Launchでデータ要素を作成する必要があります。 データ要素は、ポストバックメッセージでPOIに関する必要な情報を自動的に入力します。

Experience Platform Launchでデータ要素を作成するには：

1. 「**データ要素**」タブをクリックします。
1. 「**データ要素を追加**」をクリックします。
1. 名前を入力します。例：**現在のコーヒーショップ名**。
1. **拡張機能** ドロップダウンリストで、**場所 – Beta**&#x200B;を選択します。
1. 「**データ要素**」で「**市区町村**」を選択します。
1. 右側のペインで、**現在のPOI**&#x200B;を選択します。
1. 「**保存**」をクリックします。

### Places サービス用のExperience Platform Launchでのルールの作成

![&#x200B; ルールの作成](/help/assets/placesrule.png)

1. Experience Platform Launch で、「**[!UICONTROL ルール]**」タブをクリックします。
1. 「**[!UICONTROL ルールを追加]**」をクリックします。
1. ルールの名前を入力します。例：**[!UICONTROL SF]**&#x200B;のコーヒーショップのエントリを追跡します。

### イベントの作成

1. 「イベント」セクションで、「**[!UICONTROL + Add]**」をクリックします。 ルールを適用するタイミングは、イベントによって決まります。
1. **[!UICONTROL 拡張機能]** ドロップダウンリストで、**[!UICONTROL 場所 – Beta]**&#x200B;を選択します。
1. **[!UICONTROL イベントタイプ]**&#x200B;ドロップダウンリストで、「**[!UICONTROL POI を入力]**」を選択します。
1. 「**[!UICONTROL 名前]**」に、イベントの名前を入力します（例：「**[!UICONTROL コーヒーショップへの来店]**」）。
1. 「**[!UICONTROL 変更を保存]**」をクリックします。

### 条件の作成

1. 「条件」セクションで、「**[!UICONTROL +追加]**」をクリックします。 条件は、アクションを実行するためにどのような基準を満たすべきかを決定します。
1. 「**[!UICONTROL 論理タイプ]**」で「標準」を選択し、条件が満たされた場合にアクションを実行できます。
1. **[!UICONTROL 拡張機能]** ドロップダウンリストで、**[!UICONTROL 場所 – Beta]**&#x200B;を選択します。
1. 「**[!UICONTROL 条件タイプ]**」で「**[!UICONTROL 市区町村]**」を選択します。
1. 条件の名前を入力します。例：**[!UICONTROL SF]**&#x200B;のコーヒーショップ。
1. 右側のウィンドウで「**[!UICONTROL 現在の POI]**」をクリックし、ドロップダウンリストで「**[!UICONTROL サンフランシスコ]**」を市区町村の 1 つとして選択します。
1. 「**[!UICONTROL 変更を保存]**」をクリックします。

### アクションの作成

1. **[!UICONTROL アクション]** セクションで、**[!UICONTROL +追加]**&#x200B;をクリックします。
1. **[!UICONTROL 拡張機能]** ドロップダウンリストで、デフォルトの&#x200B;**[!UICONTROL モバイルコア]** オプションを選択したままにします。
1. アクションの種類（例：**[!UICONTROL Postbackを送信]**&#x200B;など）を選択します。

   a. **[!UICONTROL URL]**&#x200B;に、Slackのポストバック URL （例：`https://hooks.slack.com/services/`）を入力します。

   b. 投稿本文を送信するには、「**[!UICONTROL 投稿本文を追加]**」チェックボックスをオンにします。

   c. **[!UICONTROL 投稿本文]**&#x200B;で、投稿本文を追加します（例：`{ "text": "A customer has entered" }`）

   c. コンテンツタイプ（例：**[!UICONTROL application/json]**）を入力します。

   d. タイムアウト値（例：**[!UICONTROL 5]**）を選択します。

1. 「**[!UICONTROL 変更を保存]**」をクリックします。

### ルールの公開

1. ルールをアクティブにするには、ルールを公開する必要があります。 Experience Platform Launchでのルールの公開について詳しくは、[公開](https://experienceleague.adobe.com/docs/experience-platform/tags/publish/overview.html)を参照してください。

### 入口と出口を超えた思考

Places サービスのジオフェンスの出入りをExperience Platform Launchのトリガールールに使用すると、非常に強力ですが、位置情報を使用して他のイベントを実行することもできます。 例えば、アプリ内の特定のtrackAction コールイベントに基づいて、モバイルコアトラックアクションイベントトリガーを実行する準備ができているとします。 このイベントに基づいて、アクションが実行される前に、イベントに追加の場所の条件を配置できます。 例えば、購入`trackAction` イベントが発生した場合はアプリ内アンケートを開きますが、ユーザーの現在の場所に特定のPlaces サービスのメタデータが含まれている場合は&#x200B;**のみ**。

![条件を作成](/help/assets/places-condition.png)
