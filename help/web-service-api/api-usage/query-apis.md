---
title: 概要
description: クエリAPIの理解と使用
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 5%

---



# クエリAPI

呼び出し元に最も近いPOIをクエリできるGETメソッド。

## リクエスト

```text
GET https://query.places.adobe.com/placesedgequery
```

次の入力を使用すると、サービスは呼び出し元に最も近いPOIのリストを返します。

* 呼び出し元の位置（緯度、経度）。
* 検索に含めるPOIライブラリのID。
* 返すPOIの最大数です。  デフォルト値は 100 です。

   発信者とPOIとの距離は、発信者からPOIのジオフェンスの端までの距離と定義される。 この応答では、呼び出し元を含むPOIは、呼び出し元を持つものとしてマークされます。

引数は次のクエリパラメーターとして指定します。

* (**必須**) `latitude`

   発信者の緯度（ —85 ～ 85の範囲）。
* (**必須**) `longitude`

   発信者の経度。-180 ～ 180の範囲で指定する必要があります。

* (**オプション**) `limit`

   返すPOIの最大数です。

* (**必須**) `library`

   クエリするライブラリのID。 複数のライブラリをクエリするには、ライブラリパラメーターの複数のコピーをクエリに含めます。

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

下のPOI `places.pois` は、発信者からPOIの端までの距離で分類される。 の下のPOIには呼び出し元が `places.userWithin` 含まれ、これらのPOIはランク順に並べられ、次に半径が増えます。

## サンプル呼び出し

呼び出しの例を次に示します。

```text
GET https://query.places.adobe.com/placesedgequery?latitude=<userLatitude>&longitude=<userLongitude>&library=<libID1>&library=<libID2>&limit=20
```
