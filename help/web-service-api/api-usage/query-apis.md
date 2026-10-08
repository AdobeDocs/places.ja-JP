---
title: 概要
description: クエリ APIの概要と使用。
exl-id: cc61a49c-1cf2-407f-b81a-3d38fcb622cc
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: d8704da9c84a066f72471421290d4b46c65f41e1
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 3%
---
# クエリ API

呼び出し元に最も近いPOIをクエリできるGET メソッド。

## リクエスト

```text
GET https://query.places.adobe.com/placesedgequery
```

次の入力を使用すると、サービスは呼び出し元に最も近いPOIのリストを返します。

* 呼び出し元の位置（緯度、経度）。
* 検索に含めるPOI ライブラリのID。
* 返されるPOIの最大数。  デフォルト値は 100 です。

  発信者とPOI間の距離は、発信者からPOIのジオフェンスの端までの距離として定義されます。 応答では、呼び出し元を含むPOIは、呼び出し元を持つとマークされます。

引数は、次のクエリパラメーターとして指定されます。

* （**必須**） `latitude`

  呼び出し元の緯度は–85 ～ 85である必要があります。
* （**必須**） `longitude`

  呼び出し元の経度は–180 ～ 180にする必要があります。

* （**オプション**） `limit`

  返されるPOIの最大数。

* （**必須**） `library`

  クエリするライブラリのID。 複数のライブラリをクエリするには、クエリにライブラリパラメーターの複数のコピーが含まれていることを確認します。

正常に返されたJSON形式の例を次に示します。

```markup
{
    "places": {
        "userWithin": [
            {
                "p": [
                    "poi id",
                    "poi name",
                    "poi center's latitude",
                    "poi center's longitude",
                    poiRadius,
                    rank
                ],
                "x": {
                    "country": "US",
                    "city": "Fremont",
                    "street": "Vineyard Heights",
                    "Color": "Blue",
                    "state": "CA",
                    <other POI metadata>
                }
            }
        ],
        "pois": [
            {
                "p": [
                    "poi id",
                    "poi name",
                    "poi center's latitude",
                    "poi center's longitude",
                    poiRadius,
                    rank
                ],
                "x": {
                    "country": "US",
                    "city": "Milpitas",
                    "street": null,
                    "state": "CA"
                }
            },
            {
                "p": [
                    "poi id",
                    "poi name",
                    "poi center's latitude",
                    "poi center's longitude",
                    poiRadius,
                    rank
                ],
                "x": {
                    "country": "US",
                    "city": "Fremont",
                    "street": null,
                    "state": "CA"
                }
            }
        ]
    }
}
```

`places.pois`未満のPOIは、発信者からPOIのエッジまでの距離で並べ替えられます。 `places.userWithin`の下のPOIには呼び出し元が含まれており、これらのPOIはランク順に並べられ、次に半径を増やします。

## サンプル呼び出し

次に、呼び出しの例を示します。

```text
GET https://query.places.adobe.com/placesedgequery?latitude=<userLatitude>&longitude=<userLongitude>&library=<libID1>&library=<libID2>&limit=20
```
