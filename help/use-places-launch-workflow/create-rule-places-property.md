---
title: Places Service プロパティのルールの作成
description: Places SDK は、現在の場所を追跡し、現在の場所に関する設定済みの POI を監視し、これらの POI の入口イベントと出口イベントを追跡します。
exl-id: dd5aa7ac-55f9-44dc-8632-e483ef3b91a0
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '922'
ht-degree: 15%

---

# 入口ルールと出口ルールの作成 {#create-entry-exit-rules}

Places 拡張機能と地域監視ソリューションをモバイルアプリケーションにインストールすると、場所の入口イベントや出口イベントを含む、場所のデータをトリガーまたは条件付きでトリガーするルールをAdobe Experience Platform Launchで作成できます。

## ルール

イベント、条件、アクションで構成されるルールを設定できます。 各ルールは、次の内容で構成されます。

* 1 つ以上のイベント
* （オプション）条件
* 1 つ以上のアクション

### Places Service イベント

Places Service は、ルールを実行できる次のイベントを提供します。

* **POI を入力**：設定した POI に顧客が入ると Places SDK によってトリガーされます。
* **出口 POI**：設定した POI から顧客が離脱すると、Places SDK によってトリガーされます。

### Places サービス条件

条件は、アクションを実行するために、イベントに関連付けられたデータ、またはそのインスタンスの拡張機能の共有状態が満たす必要がある条件を定義します。 例えば、サンフランシスコの都市に限り、喫茶店へのエントリに対するアクションをトリガーする条件を設定できます。

Places SDK は、次の状態を管理します。

* 現在の POI：顧客が現在いる POI を指します。
* 最後に離脱した POI。顧客が最後に離脱した POI を示します。
* 最後に入力された POI。顧客が入力した最新の POI を示します。

各 POI には次のデータ要素が含まれます。

* ID
* 名前
* 緯度/経度
* 半径
* メタデータ（市区町村、国、州、カテゴリなど）

### アクション

アクションは、実行されたイベントに対してルールが満たされた場合にアプリが実行する動作を定義します。 例えば、顧客が POI を入力する際に、モバイルデバイスに表示するようこそメッセージを設定できます。

## ルールの作成：例

>[!CAUTION]
>
>この例では、米国内の全コーヒーショップの POI ライブラリを作成済みであることを前提としています。POI とライブラリの作成について詳しくは、 [POI の作成](/help/poi-mgmt-ui/create-a-poi-ui.md) および *ライブラリの作成* in [複数のライブラリを管理](https://experienceleague.adobe.com/docs/places/using/poi-mgmt-ui/manage-libraries-in-the-places-ui.html).

以下の手順は、サンフランシスコで喫茶店に入ったときにSlackに投稿を返すルールを作成する方法の例です。

イベント、条件およびアクションは、次の方法で定義されます。

* **イベント**：場所エントリイベント。
* **条件**：**現在の POI** の市区町村はサンフランシスコ
* **アクション**：顧客が入力したSlackショップの名前をコーヒー店にポストバックを送信します。

### 前提条件

ルールを作成する前に、Adobe Experience Platform Launchでデータ要素を作成する必要があります。 データ要素は、ポストバックメッセージに POI に関する必要な情報を自動的に入力します。

データ要素を「Experience Platform Launch」で作成するには：

1. 次をクリック： **データ要素** タブをクリックします。
1. 「**データ要素の追加**」をクリックします。
1. 名前を入力します（例： ）。 **現在のコーヒーショップ名**.
1. Adobe Analytics の **拡張** ドロップダウンリストで、「 **Places — ベータ版**.
1. 「**データ要素**」で「**市区町村**」を選択します。
1. 右側のウィンドウで、「 」を選択します。 **現在の POI**.
1. 「**保存**」をクリックします。

### Places Service のExperience Platform Launchでのルールの作成

![ルールの作成](/help/assets/placesrule.png)

1. Experience Platform Launch で、「**[!UICONTROL ルール]**」タブをクリックします。
1. 「**[!UICONTROL Add Rule]**」をクリックします。
1. ルールの名前を入力します（例： ）。 **[!UICONTROL SF でコーヒーショップのエントリを追跡する]**.

### イベントの作成

1. 「イベント」セクションで、 **[!UICONTROL +追加]**. イベントは、ルールを実行するタイミングを決定します。
1. Adobe Analytics の **[!UICONTROL 拡張]** ドロップダウンリストで、「 **[!UICONTROL Places — ベータ版]**.
1. **[!UICONTROL イベントタイプ]**&#x200B;ドロップダウンリストで、「**[!UICONTROL POI を入力]**」を選択します。
1. 「**[!UICONTROL 名前]**」に、イベントの名前を入力します（例：「**[!UICONTROL コーヒーショップへの来店]**」）。
1. 「**[!UICONTROL 変更を保存]**」をクリックします。

### 条件の作成

1. 「条件」セクションで、 **[!UICONTROL +追加]**. 条件は、アクションを実行するために満たす必要がある条件を決定します。
1. 「**[!UICONTROL 論理タイプ]**」で「標準」を選択し、条件が満たされた場合にアクションを実行できます。
1. Adobe Analytics の **[!UICONTROL 拡張]** ドロップダウンリストで、「 **[!UICONTROL Places — ベータ版]**.
1. 「**[!UICONTROL 条件タイプ]**」で「**[!UICONTROL 市区町村]**」を選択します。
1. 条件名を入力します（例： ）。 **[!UICONTROL SF のコーヒーショップ]**.
1. 右側のウィンドウで「**[!UICONTROL 現在の POI]**」をクリックし、ドロップダウンリストで「**[!UICONTROL サンフランシスコ]**」を市区町村の 1 つとして選択します。
1. 「**[!UICONTROL 変更を保存]**」をクリックします。

### アクションの作成

1. Adobe Analytics の **[!UICONTROL アクション]** セクションで、 **[!UICONTROL +追加]**.
1. Adobe Analytics の **[!UICONTROL 拡張]** ドロップダウンリストをデフォルトのままにする。 **[!UICONTROL Mobile Core]** オプションが選択されています。
1. アクションタイプを選択します。例： **[!UICONTROL ポストバックを送信]**.

   a.の場合 **[!UICONTROL URL]**、Slackのポストバック URL を入力します。例： `https://hooks.slack.com/services/`.

   b.投稿本文を送信するには、 **[!UICONTROL POST 本文を追加]** 」チェックボックスをオンにします。

   c.イン **[!UICONTROL POST 本文]**、次のように post 本文を追加します。 `{ "text": "A customer has entered" }`

   c.例えばコンテンツタイプを入力します。 **[!UICONTROL application/json]**.

   d.タイムアウト値を選択します。例： **[!UICONTROL 5]**.

1. 「**[!UICONTROL 変更を保存]**」をクリックします。

### ルールを発行する

1. ルールをアクティブ化するには、公開する必要があります。 ルールの公開について詳しくは、Experience Platform Launch [公開](https://experienceleague.adobe.com/docs/experience-platform/tags/publish/overview.html?lang=ja).

### 入口と出口を越えた思考

Places Service のジオフェンスのエントリと出口をExperience Platform Launch内のトリガールールに使用すると非常に強力ですが、他のイベントを実行する際の条件として位置データを使用することもできます。 例えば、アプリ内の特定の trackAction 呼び出しイベントに基づいて、Mobile Core Track Action イベントトリガーを実行する準備が整っているとします。 このイベントに基づいて、アクションが実行される前に、イベントに追加の位置条件を追加できます。 例えば、購入時にアプリ内調査を開くなどです。 `trackAction` イベントが発生するが、 **のみ** ユーザーの現在の場所に特定の Places サービスメタデータが含まれている場合。

![条件の作成](/help/assets/places-condition.png)
