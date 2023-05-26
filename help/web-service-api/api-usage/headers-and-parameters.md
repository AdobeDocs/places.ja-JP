---
title: ヘッダーとパラメーター
description: Places Service REST API で使用できるヘッダーとパラメーター。
exl-id: 3c7e76de-f0ff-4966-a3ec-7f64d819c140
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 17%

---

# ヘッダーとパラメーター {#headers-and-parameters}

Places Service REST API で使用可能なヘッダーとパラメーターの詳細を次に示します。

## サポートされているヘッダー

| ヘッダー | 説明 | メソッド | 例 |
| :--- | :--- | :--- | :--- |
| `Authorization` | bearer トークン | すべて |  |
| `x-api-key` | API キー | すべて | `19776964b4cde49e08d8f62e5824f777b` |
| `x-gw-ims-org-id` | 組織 ID | すべて | `18FB61145BAC2FFB0A494777@AdobeOrg` |
| `Content-Type` | 送信または受信するコンテンツの形式 | PUT、POST | `application/json` |
| `Accept-Language` | エラーメッセージに使用される言語 | オプション | `en-US` |

## ライブラリパラメーター

| パラメーター | 説明 | タイプ | 上限 | リクエストまたは応答 | 例 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `id` | ライブラリの ID | 割り当て済み | n/a | 応答 | `"id": "b2488788-2d2a-462b-b1a2-305272777dda"` |
| `name` | ライブラリの名前 | 文字列 | 256 文字 | 両方、リクエストで必須 | `"name": "Amazing Places"` |
| `orgID` | 組織の Experience Cloud 組織 ID | 割り当て済み | n/a | 応答 | `"orgID": "777F20F55BACA09E0A495D8F@AdobeOrg"` |
| `poiCount` | ライブラリ内の POI の数 | 整数 | 最大 150,000 | 応答 | `"poiCount": 25149` |
| `metadataDescriptors` | 一意の POI メタデータキーと値のペアごとのカウント | 混合 | n/a | 応答 |  |
| `poiCountInCities` | 一意の POI 市区町村値ごとにカウント | 混合 | n/a | 応答 |  |

## POI パラメーター

| パラメーター | 説明 | タイプ | 上限 | リクエストまたは応答 | 例 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `data` | Poi データ | POI の詳細の配列 | n/a | 両方 |  |
| `id` | POI の ID | 割り当て済み | n/a | 応答 | `"id": "1455462b-7f9c-4220-9f42-5bbce777a0d1"` |
| `name` | POI の名前 | 文字列 | 512 文字 | 両方、オプション\* | `"name": "My Favorite Place"` |
| `description` | POI の説明 | 文字列 | 512 文字 | 両方、オプション\* | `"description": "This is a very good place."` |
| `location` | POI のタイプと座標の配列 | 配列（混在） | n/a | 両方 | `"location": {"type": "Point", "coordinates": [-122.201007, 37.604713]` |
| `type` | POI のタイプ | 文字列 | 現在は「ポイント」のみがサポートされています | 両方、リクエストで必須 | `"type": "Point"` |
| `coordinates` | POI の経度と緯度の配列 | 配列（浮動小数点） | 経度：-180～180、緯度 —85～85 | 両方、リクエストで必須 | `"coordinates": [-122.201007, 37.604713]` |
| `radius` | POI の周りの円形ジオフェンスのサイズ | float | 10～2000 メートル | 両方、リクエストで必須 | `"radius": 100` |
| `country` | POI の国 | 文字列 | 32 文字 | 両方、オプション* | `"country": "United States"` |
| `state` | POI の州 | 文字列 | 32 文字 | 両方、オプション* | `"state": "California"` |
| `city` | POI の市区町村 | 文字列 | 32 文字 | 両方、オプション* | `"city": "San Jose"` |
| `street` | POI の住所 | 文字列 | 256 文字 | 両方、オプション* | `"street": "122 Woz Way"` |
| `category` | POI のカテゴリ | 文字列 | 100 文字 | 両方、オプション* | `"category": "cafe"` |
| `icon` | POI のアイコン | 文字列 | 50 文字 | 両方、オプション* | `"icon": "star"` |
| `color` | POI の色 | 文字列 | 8 文字 | 両方、オプション* | `"color": "blue"` |
| `metadata` | POI のキーと値のペアの配列 | array(string) | キー：256 文字、値：256 文字、最大 10 組 | 両方、オプション* | `"metadata": {"region": "Equator"}` |
| `lib_id` | POI が含まれるライブラリの ID | n/a | n/a | 両方、必須 | `"lib_id": "ac7a0b25-c6c2-43ba-bbc6-2b1777b80fe9"` |

* パラメータ値が含まれていない場合、値はに設定されます。 `empty` データベース内。 既存のキーと値のペアが含まれていない場合、その POI のキーと値のペアがデータベースから削除されます。
