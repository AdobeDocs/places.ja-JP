---
title: Places Service プロパティのルールの作成
description: Places SDK は、現在の場所を追跡し、現在の場所周辺に設定された POI を監視し、これらの POI の入口イベントと出口イベントを追跡します。
exl-id: dd5aa7ac-55f9-44dc-8632-e483ef3b91a0
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '911'
ht-degree: 13%

---

# 入口ルールと出口ルールの作成 {#create-entry-exit-rules}

モバイルアプリケーションにインストールされた Places 拡張機能とリージョンのモニタリングソリューションを使用すると、場所の入口イベントや出口イベントなど、トリガーまたは条件付きの場所データを含むルールをAdobe Experience Platform Launchで作成できます。

## ルール

イベント、条件、アクションで構成されるルールを設定できます。 各ルールは、次の内容で構成されます。

* 1 つ以上のイベント
* （任意）条件
* 1 つ以上のアクション

### Places Service イベント

Places Service には、ルールを実行できる次のイベントが用意されています。

* **POI を入力** は、顧客が設定した POI に入ると Places SDK によってトリガーされます。
* **POI を終了** は、顧客が設定した POI を終了すると、Places SDK によってトリガーされます。

### Places Service 条件

条件は、イベントに関連付けられたデータまたはそのインスタンスの拡張機能の共有状態が、アクションを実行するために満たす必要がある条件を定義します。 例えば、サンフランシスコ市内のみのコーヒーショップにエントリした際のアクションをトリガーにする条件を設定できます。

Places SDK は次の状態を維持します。

* 現在の POI。現在お客様が所在する POI を指します。
* 前回の離脱 POI：顧客が離脱した最新の POI を参照します。
* 前回エントリした POI。顧客が最後に入力した最新の POI を表します。

各 POI には、次のデータ要素が含まれます。

* ID
* 名前
* 緯度/経度
* 半径
* メタデータ （市区町村、国、都道府県、カテゴリなど）

### アクション

アクションは、発生したイベントに対して、ルールの条件が満たされたときにアプリが何を実行するかを定義します。 例えば、顧客が POI に入った際に、モバイルデバイスに表示するお知らせメッセージを設定できます。

## ルールの作成：例

>[!CAUTION]
>
>この例では、米国内の全コーヒーショップの POI ライブラリを作成済みであることを前提としています。POI とライブラリの作成について詳しくは、[&#x200B; 複数のライブラリの管理 &#x200B;](/help/poi-mgmt-ui/create-a-poi-ui.md) の [POI の作成 *および* ライブラリの作成 &#x200B;](https://experienceleague.adobe.com/docs/places/using/poi-mgmt-ui/manage-libraries-in-the-places-ui.html?lang=ja) を参照してください。

以下の手順は、サンフランシスコのコーヒーショップに入ったときにSlackに投稿を返すルールを作成する方法の例です。

イベント、条件、アクションは、次のように定義されます。

* **イベント**：エントリイベントを配置します。
* **条件**：**現在の POI** の市区町村はサンフランシスコ
* **アクション**：お客様が入力したコーヒーショップの名前をSlackにポストバックを送信します。

### 前提条件

ルールを作成する前に、Adobe Experience Platform Launchでデータ要素を作成する必要があります。 データ要素は、POI に関して必要な情報をポストバックメッセージに自動的に入力します。

Experience Platform Launchにデータ要素を作成するには：

1. 「**データ要素**」タブをクリックします。
1. 「**データ要素を追加**」をクリックします。
1. 名前（例：**現在のコーヒーショップ名**）を入力します。
1. 「**拡張機能**」ドロップダウンリストで、「**場所 – Beta**」を選択します。
1. 「**データ要素**」で「**市区町村**」を選択します。
1. 右側のペインで「**現在の POI**」を選択します。
1. 「**保存**」をクリックします。

### Places Service 用のExperience Platform Launchでルールを作成します

![&#x200B; ルールの作成 &#x200B;](/help/assets/placesrule.png)

1. Experience Platform Launch で、「**[!UICONTROL ルール]**」タブをクリックします。
1. 「**[!UICONTROL ルールを追加]**」をクリックします。
1. ルールの名前を入力します（例：**[!UICONTROL コーヒーショップのエントリを SF で追跡]**）。

### イベントの作成

1. 「イベント」セクションで、「**[!UICONTROL +追加]**」をクリックします。 イベントは、ルールを実行するタイミングを決定します。
1. 「**[!UICONTROL 拡張機能]**」ドロップダウンリストで、「**[!UICONTROL 場所 – Beta]**」を選択します。
1. **[!UICONTROL イベントタイプ]**&#x200B;ドロップダウンリストで、「**[!UICONTROL POI を入力]**」を選択します。
1. 「**[!UICONTROL 名前]**」に、イベントの名前を入力します（例：「**[!UICONTROL コーヒーショップへの来店]**」）。
1. 「**[!UICONTROL 変更を保存]**」をクリックします。

### 条件の作成

1. 「条件」セクションで、「**[!UICONTROL +追加]**」をクリックします。 条件は、アクションを実行するために満たす必要がある条件を決定します。
1. 「**[!UICONTROL 論理タイプ]**」で「標準」を選択し、条件が満たされた場合にアクションを実行できます。
1. 「**[!UICONTROL 拡張機能]**」ドロップダウンリストで、「**[!UICONTROL 場所 – Beta]**」を選択します。
1. 「**[!UICONTROL 条件タイプ]**」で「**[!UICONTROL 市区町村]**」を選択します。
1. 条件名（例：**[!UICONTROL Coffee shop in SF]**）を入力します。
1. 右側のウィンドウで「**[!UICONTROL 現在の POI]**」をクリックし、ドロップダウンリストで「**[!UICONTROL サンフランシスコ]**」を市区町村の 1 つとして選択します。
1. 「**[!UICONTROL 変更を保存]**」をクリックします。

### アクションの作成

1. 「**[!UICONTROL アクション]**」セクションで、「**[!UICONTROL +追加]**」をクリックします。
1. 「**[!UICONTROL 拡張機能]**」ドロップダウンリストで、デフォルトの「**[!UICONTROL Mobile Core]**」オプションを選択したままにします。
1. アクションタイプを選択します（例：**[!UICONTROL ポストバックを送信]**。

   a. **[!UICONTROL URL]** に、Slackのポストバック URL （例：`https://hooks.slack.com/services/`）を入力します。

   b.投稿本文を送信するには、「**[!UICONTROL Post本文を追加]**」チェックボックスをオンにします。

   c. **[!UICONTROL Postの本文]** に、次のように後の本文を追加します：`{ "text": "A customer has entered" }`

   c. コンテンツタイプを入力します（例：**[!UICONTROL application/json]**）。

   d. タイムアウト値を選択します（例：**[!UICONTROL 5]**）。

1. 「**[!UICONTROL 変更を保存]**」をクリックします。

### ルールのPublish

1. ルールをアクティベートするには、ルールを公開する必要があります。 Experience Platform Launchでのルールの公開について詳しくは、「[&#x200B; 公開 &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/tags/publish/overview.html?lang=ja)」を参照してください。

### 開業・廃業を超えた思考

Places Service のExperience Platform Launchのトリガールールへのジオフェンスの入口と出口の使用は非常に強力ですが、他のイベントが発生する条件として場所データを使用することもできます。 例えば、アプリ内の特定の trackAction 呼び出しイベントに基づいて、Mobile Core Track Action イベントトリガーを実行する準備を整えることができます。 このイベントに基づいて、アクションが実行される前に、イベントに追加の位置条件を配置できます。 例えば、ユーザーの現在の場所に特定の Places Service メタデータが含まれている場合に **のみ**、購入 `trackAction` ークスイベントが発生したときにアプリ内調査を開きます。

![&#x200B; 条件の作成 &#x200B;](/help/assets/places-condition.png)
