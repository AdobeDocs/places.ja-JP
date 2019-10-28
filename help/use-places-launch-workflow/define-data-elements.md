---
title: データ要素の定義
seo-title: データ要素の定義
description: ここでは、Experience Platform Launch for Placesでデータ要素を作成、使用および公開する方法について説明します。
seo-description: 'ここでは、Experience Platform Launch for Placesでデータ要素を作成、使用および公開する方法について説明します。 '
translation-type: tm+mt
source-git-commit: fd98249c01fba93250dc7111798c76f3c96c6e20

---


# Define a data element {#define-data-elements}

次の情報は、データ要素と、それらの作成および発行方法を理解するのに役立ちます。

## データ要素について

データ要素は、アプリのデータディクショナリの構成要素で、マーケティングや広告テクノロジー全体でデータを収集、整理、配信するために使用されます。

データ要素は、値を訪問者ID、通信業者名、広告ID、プッシュIDなどにマップできる変数です。 エクスペリエンスプラットフォームの起動では、変数名でこの値を参照できます。 このデータ要素のコレクションは、ルール（イベント、条件およびアクション）の構築に使用できる定義済みデータのディクショナリになり、このディクショナリはエクスペリエンスプラットフォーム起動で共有され、プロパティの任意の拡張で使用できます。

「配置」(Places)拡張では、次のターゲットから値を参照できます。

* 現在のPOIは、お客様の現在の所在地のPOIを指します。

   ユーザーが複数のPOIに配置されている場合は、そのユーザーが上位のライブラリに属しているかが選択されます。 複数のPOIが最も高いランクのライブラリに属している場合、半径が最も小さいPOIが選択されます。
* POIから最後に離脱した場合。これは、ユーザーが最後に離脱したPOIを示します。
* 最後に入力されたPOIは、ユーザーが入力した最新のPOIを指します。

各POIには、次のデータ参照が含まれます。

* **[!UICONTROL Category]**:POIのカテゴリ
* **[!IUICONTROL 市区町村]**:POI都市
* **[!UICONTROL Country]**:ポイ州
* **[UICONTROL Latitude]**:POI緯度
* **[UICONTROL Longitude]**:POIの経度
* **[!UICONTROL Metadata]**:poiのカスタムメタデータ
* **[!UICONTROL Name]**:POI地域
* **[!UICONTROL Radius]**:POI半径
* **[!UICONTROL Region ID]**:POIのID
* **[!UICONTROL Region/State]**:POIの地域、都道府県、州

### データ要素の作成

1. アプリのプロパティページで、タブをクリック **[!UICONTROL Data Elements]** します。

2. 「**[!UICONTROL Create New Data Element]**」をクリックします。

   ![データ要素の作成](/help/assets/create-de-2-v3.png)

3. インストールされている拡張機能のリストで、を探しま **[!UICONTROL Places]**&#x200B;す。

4. ドロップダ **[!UICONTROL Data Element Type]** ウンリストで、このデータ要素のデータ参照を選択します。

5. POIターゲットを選択します。

6. このデータ要素がカスタムメタデータ参照の場合は、メタデータキーを選択します。

7. データ要素の名前を入力し、をクリックしま **[!UICONTROL Save]**&#x200B;す。

   ![データ要素の作成](/help/assets/create-de-7-v3.png)


## データ要素を使用する

データ要素を作成した後、データ要素ピッカーが存在する場合は、任意のルールコンポーネントのデータ要素を使用できます。

![データ要素の使用](/help/assets/use-de-v2.png)

データ要素ピッカーがルールコンポーネントに存在しない場合は、データ要素名をトークンでラップして、データ要素を使用で **[!UICONTROL %%]** きます。
例えば、データ要素名がである場合は、テ **[!UICONTROL Last POI City]**&#x200B;キスト入力にを追 **[!UICONTROL LAST POI City]** 加することができます。


## データ要素の発行

データ要素がルールコンポーネントのいずれかで使用されている場合は、これらのデータ要素もライブラリに含めて発行する必要があります。
