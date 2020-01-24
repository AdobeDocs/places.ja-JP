---
title: ヘッダーとパラメーター
description: Places Service REST APIで使用できるヘッダーとパラメーター。
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b

---


# ヘッダーとパラメーター {#headers-and-parameters}

Places Service REST APIで使用できるヘッダーとパラメーターの詳細を以下に示します。

## サポートされるヘッダー

| Header | 説明 | メソッド | 例 |
| :--- | :--- | :--- | :--- |
| `Authorization` | ベアラトークン | すべて |  |
| `x-api-key` | APIキー | すべて | `19776964b4cde49e08d8f62e5824f777b` |
| `x-gw-ims-org-id` | 組織ID | すべて | `18FB61145BAC2FFB0A494777@AdobeOrg` |
| `Content-Type` | 送信または受信したコンテンツの形式 | PUT、POST | `application/json` |
| `Accept-Language` | エラーメッセージに使用する言語 | オプション | `en-US` |

## ライブラリパラメーター

| パラメーター | 説明 | タイプ | 制限 | リクエストまたは応答 | 例 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `id` | ライブラリのID | 割り当て | なし | 応答 | `"id": "b2488788-2d2a-462b-b1a2-305272777dda"` |
| `name` | ライブラリの名前 | string | 256 文字 | 両方、要求で必須 | `"name": "Amazing Places"` |
| `orgID` | 組織のExperience cloud組織ID | 割り当て | なし | 応答 | `"orgID": "777F20F55BACA09E0A495D8F@AdobeOrg"` |
| `poiCount` | ライブラリ内のPOI数 | 整数 | 最大150,000 | 応答 | `"poiCount": 25149` |
| `metadataDescriptors` | 一意のPOIメタデータキーと値の各ペアの数 | 混合 | なし | 応答 |  |
| `poiCountInCities` | 一意のPOI市区町村値ごとの数 | 混合 | なし | 応答 |  |

## POIパラメーター

| パラメーター | 説明 | タイプ | 制限 | リクエストまたは応答 | 例 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `data` | Poiデータ | POIの詳細の配列 | なし | both |  |
| `id` | POIのID | 割り当て | なし | 応答 | `"id": "1455462b-7f9c-4220-9f42-5bbce777a0d1"` |
| `name` | POIの名前 | string | 512 文字 | both, optional\* | `"name": "My Favorite Place"` |
| `description` | POIの説明 | string | 512 文字 | both, optional\* | `"description": "This is a very good place."` |
| `location` | POIのタイプと座標の配列 | 配列（混在） | なし | both | `"location": {"type": "Point", "coordinates": [-122.201007, 37.604713]` |
| `type` | POIのタイプ | string | 現在は「点」のみがサポートされています | 両方、要求で必須 | `"type": "Point"` |
| `coordinates` | POIの経度と緯度の配列 | array (float) | 経度：-180 ～ 180、緯度 —85 ～ 85 | 両方、要求で必須 | `"coordinates": [-122.201007, 37.604713]` |
| `radius` | POI周辺の円形ジオフェンスの大きさ | float | 10～2000メートル | 両方、要求で必須 | `"radius": 100` |
| `country` | POIの国 | string | 32 文字 | both, optional* | `"country": "United States"` |
| `state` | POIの州 | string | 32 文字 | both, optional* | `"state": "California"` |
| `city` | POIの市区町村 | string | 32 文字 | both, optional* | `"city": "San Jose"` |
| `street` | POIの住所 | string | 256 文字 | both, optional* | `"street": "122 Woz Way"` |
| `category` | POIのカテゴリ | string | 100 文字 | both, optional* | `"category": "cafe"` |
| `icon` | POIのアイコン | string | 50 文字 | both, optional* | `"icon": "star"` |
| `color` | POIの色 | string | 8 文字 | both, optional* | `"color": "blue"` |
| `metadata` | POI用のキー/値のペアの配列 | array(string) | キー：256文字、値：256文字、最大10組 | both, optional* | `"metadata": {"region": "Equator"}` |
| `lib_id` | POIが属するライブラリのID | なし | なし | 両方、必須 | `"lib_id": "ac7a0b25-c6c2-43ba-bbc6-2b1777b80fe9"` |

* パラメータ値が含まれていない場合、値はデータベース内でに設定 `empty` されます。 既存のキーと値のペアが含まれていない場合、そのPOIのキーと値のペアはデータベースから削除されます。

