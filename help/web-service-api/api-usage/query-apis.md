---
title: 概要
description: クエリ API の理解と使用。
exl-id: cc61a49c-1cf2-407f-b81a-3d38fcb622cc
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 6%

---

# クエリ API

呼び出し元に最も近い POI に対してクエリを実行できるGETメソッド。

## リクエスト

```text
GET https://query.places.adobe.com/placesedgequery
```

次の入力を使用すると、サービスは呼び出し元に最も近い POI のリストを返します。

* 呼び出し元の位置（緯度、経度）。
* 検索に含める POI ライブラリの ID。
* 返す POI の最大数。  デフォルト値は 100 です。

   呼び出し元と POI の間の距離は、呼び出し元から POI ジオフェンスの端までの距離として定義されます。 応答では、呼び出し元を含む POI は、呼び出し元を持つとマークされます。

引数は、次のクエリパラメーターとして指定します。

* (**必須**) `latitude`

   呼び出し元の緯度（ —85 ～ 85 の範囲）。
* (**必須**) `longitude`

   呼び出し元の経度（ —180 ～ 180 の範囲）。

* (**オプション**) `limit`

   返す POI の最大数。

* (**必須**) `library`

   クエリするライブラリの ID。 複数のライブラリに対してクエリを実行する場合は、必ずライブラリパラメーターの複数のコピーをクエリに含めてください。

正常に返された JSON 形式の例を次に示します。

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

以下の POI `places.pois` は、呼び出し元から POI の端までの距離で並べ替えられます。 以下の POI `places.userWithin` に呼び出し元が含まれ、これらの POI はランク別、その後半径を増やして並べ替えられます。

## サンプル呼び出し

次に呼び出しの例を示します。

```text
GET https://query.places.adobe.com/placesedgequery?latitude=<userLatitude>&longitude=<userLongitude>&library=<libID1>&library=<libID2>&limit=20
```
