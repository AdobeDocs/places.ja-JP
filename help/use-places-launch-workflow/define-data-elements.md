---
title: データ要素の定義
description: この節では、Experience Platform Launch for Placesでデータ要素を作成、使用、公開する方法について説明します。
exl-id: 57e88a37-0b0b-4064-ab72-382a36a0d01d
TQID: https://experienceleague.adobe.com/NQ83uUZJtNglAcxD6HNl4Gw1Y8-0-uqfu-hH8H0EITg
product_v2: id: a829a185-511f-4bf8-8dcf-9e684f8011cfid: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: e43347a8-f2c5-4aa4-8623-6f13875d7e3aid: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2: id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2: id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0id: f9a2105e-7a47-4e85-9193-31a519a2cb83
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dcid: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 486
ht-degree: 1%

---

# データ要素の定義 {#define-data-elements}

次の情報は、データ要素とその作成および公開方法を理解するのに役立ちます。

## データ要素について

データ要素は、アプリケーションのデータディクショナリの構成要素であり、マーケティングと広告のテクノロジーをまたいでデータを収集、整理、配信するために使用されます。

data elementは、値をVisitor ID、Carrier Name、Advertising ID、Push IDなどにマッピングできる変数です。 Experience Platform Launchでは、変数名でこの値を参照できます。 このデータ要素のコレクションは、ルール（イベント、条件、アクション）の構築に使用できる定義されたデータのディクショナリとなり、このディクショナリはExperience Platform Launch全体で共有され、プロパティ内の任意の拡張機能で使用できます。

Places拡張機能を使用すると、次のターゲットから値を参照できます。

* 現在のPOI：顧客が現在配置されているPOI。

  ユーザーが複数のPOIに配置されている場合、そのユーザーはランクの高いライブラリに属しています。 複数のPOIが最もランクの高いライブラリに属している場合は、最も半径の小さいPOIが選択されます。
* 最後に離脱したPOI。ユーザーが離脱した最新のPOIを指します。
* 最後に入力したPOI。ユーザーが入力した最新のPOIを指します。

各POIには、次のデータ参照が含まれます。

* **[!UICONTROL カテゴリ]**: POIのカテゴリ
* **[!UICONTROL 都市]**: POIの都市
* **[!UICONTROL 国]**: POIの国
* **[!UICONTROL Latitude]**: POIの緯度
* **[!UICONTROL 経度]**: POIの経度
* **[!UICONTROL メタデータ]**: POIのカスタムメタデータ
* **[!UICONTROL 名前]**: POIの名前
* **[!UICONTROL 半径]**: POIの半径
* **[!UICONTROL 地域ID]**: POIのID
* **[!UICONTROL 地域/州]**:POIの地域、州、または州

### データ要素の作成

1. アプリのプロパティページで、「**[!UICONTROL データ要素]**」タブをクリックします。

1. 「**[!UICONTROL 新規データ要素を作成]**」をクリックします。

1. インストールされている拡張機能のリストで、**[!UICONTROL Places]**&#x200B;を見つけます。

1. 「**[!UICONTROL データ要素タイプ]**」ドロップダウンリストで、このデータ要素のデータ参照を選択します。

1. POI ターゲットを選択します。

1. このデータ要素がカスタムメタデータ参照の場合は、メタデータキーを選択します。

1. データ要素の名前を入力し、**[!UICONTROL 保存]**&#x200B;をクリックします。

   ![ データ要素の作成](/help/assets/create-de-7-v3.png)


## データ要素の使用

データ要素を作成した後、データ要素ピッカーが存在する場合は、任意のルールコンポーネントからデータ要素を使用できます。

![ データ要素を使用](/help/assets/use-de-v2.png)

データ要素ピッカーがルールコンポーネントに存在しない場合は、データ要素名を&#x200B;**[!UICONTROL %]** トークンでラップすることで、データ要素を使用できます。
例えば、データ要素名が**[!UICONTROL 最終POI市区町村]**&#x200B;の場合、テキスト入力に&#x200B;**[!UICONTROL 最終POI市区町村]**&#x200B;を追加できます。


## データ要素の公開

いずれかのルールコンポーネントでデータ要素を使用する場合は、これらのデータ要素もライブラリに含めて公開する必要があります。
