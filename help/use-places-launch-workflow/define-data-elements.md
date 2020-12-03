---
title: データ要素の定義
description: この節では、場所のExperience Platform Launchでデータ要素を作成、使用、および公開する方法について説明します。
translation-type: tm+mt
source-git-commit: c22efc36f2eac6b20fc555d998c3988d8c31169e
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 1%

---


# Define a data element {#define-data-elements}

次の情報は、データ要素と、データ要素を作成して発行する方法を理解するのに役立ちます。

## データ要素について

データ要素は、アプリのデータディクショナリの構成要素で、マーケティングや広告のテクノロジー全体でデータを収集、整理、配信するために使用されます。

データ要素は変数で、値を訪問者ID、通信事業者名、広告ID、プッシュIDなどにマップできます。 Experience Platform Launchでは、変数名でこの値を参照できます。 このデータ要素のコレクションは、ルール(イベント、条件、アクション)の作成に使用できる定義済みデータのディクショナリになり、このディクショナリはExperience Platform Launch全体で共有され、プロパティ内の任意の拡張子と共に使用できます。

Places拡張子を使用して、次のターゲットから値を参照できます。

* 現在のPOI。顧客の所在地のPOIを指します。

   ユーザーが複数のPOIに配置されている場合は、そのユーザーがライブラリに属している上位のランクが選択されます。 複数のPOIが最上位のライブラリに属する場合は、半径が最も小さいPOIが選択されます。
* POIから最後に離脱した場合。これは、ユーザーが最後に離脱したPOIを示します。
* 最後に入力されたPOI。ユーザーが最後に入力したPOIを示します。

各POIには、次のデータ参照が含まれます。

* **[!UICONTROL Category]**:POIのカテゴリ
* **[!UICONTROL City]**:ポイ市
* **[!UICONTROL Country]**:ポイの国
* **[!UICONTROL Latitude]**:POIの緯度
* **[!UICONTROL Longitude]**:POIの経度
* **[!UICONTROL Metadata]**:POIのカスタムメタデータ
* **[!UICONTROL Name]**:POI名
* **[!UICONTROL Radius]**:陰核心半径
* **[!UICONTROL Region ID]**:POIのID
* **[!UICONTROL Region/State]**:POIの地域、都道府県、州

### データ要素の作成

1. アプリのプロパティページで、 **[!UICONTROL Data Elements]** タブをクリックします。

1. 「**[!UICONTROL Create New Data Element]**」をクリックします。

1. インストールされている拡張機能のリストで、を検索し **[!UICONTROL Places]**&#x200B;ます。

1. ドロップダウン **[!UICONTROL Data Element Type]** リストで、このデータ要素のデータ参照を選択します。

1. POIターゲットを選択します。

1. このデータ要素がカスタムメタデータ参照の場合は、メタデータキーを選択します。

1. データ要素の名前を入力し、をクリックし **[!UICONTROL Save]**&#x200B;ます。

   ![データ要素の作成](/help/assets/create-de-7-v3.png)


## データ要素の使用

データ要素の作成後、データ要素ピッカーが存在する場合は、任意のルールコンポーネントのデータ要素を使用できます。

![データ要素の使用](/help/assets/use-de-v2.png)

ルールコンポーネントにデータ要素ピッカーが存在しない場合は、データ要素名をトークンでラップして、データ要素を使用でき **[!UICONTROL %%]** ます。
例えば、データ要素名がである場合 **[!UICONTROL Last POI City]**&#x200B;は、テキスト入力 **[!UICONTROL LAST POI City]** にを追加できます。


## データ要素の発行

データ要素がいずれかのルールコンポーネントで使用されている場合、これらのデータ要素もライブラリに含めて発行する必要があります。
