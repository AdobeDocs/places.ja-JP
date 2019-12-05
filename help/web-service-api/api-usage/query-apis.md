---
title: 概要
description: クエリAPIの理解と使用を参照してください。
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---



# クエリAPI

呼び出し元に最も近いPOIに対してクエリを実行できるGETメソッド。

## リクエスト

```text
GET https://query.places.adobe.com/placesedgequery
```

次の入力を使用して、サービスは呼び出し元に最も近いPOIのリストを返します。

* 呼び出し元の位置\(latitude, longitude\)。
* 検索に含めるPOIライブラリのID。
* 返すPOIの最大数です。  デフォルト値は 100 です。

   発信者とPOIとの距離は、発信者からPOIのジオフェンスの端までの距離と定義される。 この応答では、呼び出し元を含むPOIが呼び出し元としてマークされます。

引数は、次のクエリパラメーターとして指定します。

* (**Required**) `latitude`

   発信者の緯度(-85 ～ 85)。
* (**Required**) `longitude`

   発信者の経度(-180 ～ 180)。

* (**オプション**) `limit`

   返すPOIの最大数です。

* (**Required**) `library`

   クエリーを実行するライブラリのID。 複数のライブラリに対してクエリーを実行する場合は、必ずライブラリパラメーターの複数のコピーをクエリーに含めてください。

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

POIは、発 `places.pois` 信者からPOIの端までの距離で分類される。 の下のPOIには `places.userWithin` 呼び出し元が含まれ、これらのPOIはランク順に並べられ、次にradiusが増えます。

## サンプル呼び出し

呼び出しの例を次に示します。

```text
GET https://query.places.adobe.com/placesedgequery?latitude=<userLatitude>&longitude=<userLongitude>&library=<libID1>&library=<libID2>&limit=20
```
