---
title: ヘッダーとパラメーター
description: Places Service REST APIで使用できるヘッダーとパラメーター。
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 17%

---


# ヘッダーとパラメーター{#headers-and-parameters}

Places Service REST APIで使用可能なヘッダーとパラメーターの詳細を次に示します。

## サポートされるヘッダー

| ヘッダー | 説明 | メソッド | 例 |
| :--- | :--- | :--- | :--- |
| `Authorization` | 持参人トークン | すべて |  |
| `x-api-key` | APIキー | すべて | `19776964b4cde49e08d8f62e5824f777b` |
| `x-gw-ims-org-id` | 組織ID | すべて | `18FB61145BAC2FFB0A494777@AdobeOrg` |
| `Content-Type` | 送信または受信したコンテンツの形式 | PUT、POST | `application/json` |
| `Accept-Language` | エラーメッセージに使用する言語 | オプション | `en-US` |

## ライブラリパラメーター

| パラメーター | 説明 | タイプ | 制限 | リクエストまたは応答 | 例 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `id` | ライブラリのID | assigned | なし | 応答 | `"id": "b2488788-2d2a-462b-b1a2-305272777dda"` |
| `name` | ライブラリの名前 | 文字列 | 256 文字 | 両方（リクエストに必要） | `"name": "Amazing Places"` |
| `orgID` | 組織のExperience Cloud orgID | assigned | なし | 応答 | `"orgID": "777F20F55BACA09E0A495D8F@AdobeOrg"` |
| `poiCount` | ライブラリ内のPOI数 | 整数 | 最大150,000 | 応答 | `"poiCount": 25149` |
| `metadataDescriptors` | 一意のPOIメタデータキーと値のペアごとの数 | 混合 | なし | 応答 |  |
| `poiCountInCities` | 一意のPOI市区町村値ごとに数えます | 混合 | なし | 応答 |  |

## POIパラメーター

| パラメーター | 説明 | タイプ | 制限 | リクエストまたは応答 | 例 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `data` | Poiデータ | 一連のPOIの詳細 | なし | both |  |
| `id` | POIのID | assigned | なし | response | `"id": "1455462b-7f9c-4220-9f42-5bbce777a0d1"` |
| `name` | POIの名前 | 文字列 | 512 文字 | both, optional\* | `"name": "My Favorite Place"` |
| `description` | POIの説明 | 文字列 | 512 文字 | both, optional\* | `"description": "This is a very good place."` |
| `location` | POIのタイプと座標の配列 | 配列（混在） | なし | both | `"location": {"type": "Point", "coordinates": [-122.201007, 37.604713]` |
| `type` | POIのタイプ | 文字列 | 現在サポートされている「点」のみ | 両方（リクエストに必要） | `"type": "Point"` |
| `coordinates` | POIの経度と緯度の配列 | array (float) | longitude:-180 ～ 180、緯度 —85 ～ 85 | 両方（リクエストに必要） | `"coordinates": [-122.201007, 37.604713]` |
| `radius` | POI周りの円形ジオフェンスのサイズ | float | 10～2000メートル | 両方（リクエストに必要） | `"radius": 100` |
| `country` | POIの国 | 文字列 | 32 文字 | both, optional* | `"country": "United States"` |
| `state` | POIの州 | 文字列 | 32 文字 | both, optional* | `"state": "California"` |
| `city` | POIの市区町村 | 文字列 | 32 文字 | both, optional* | `"city": "San Jose"` |
| `street` | POIの住所 | 文字列 | 256 文字 | both, optional* | `"street": "122 Woz Way"` |
| `category` | POIのカテゴリ | 文字列 | 100 文字 | both, optional* | `"category": "cafe"` |
| `icon` | POIのアイコン | 文字列 | 50 文字 | both, optional* | `"icon": "star"` |
| `color` | POIの色 | 文字列 | 8 文字 | both, optional* | `"color": "blue"` |
| `metadata` | POI用のキー/値のペアの配列 | array(string) | key:256文字、値：256文字、最大10組 | both, optional* | `"metadata": {"region": "Equator"}` |
| `lib_id` | POIが属するライブラリのID | なし | なし | 両方、必須 | `"lib_id": "ac7a0b25-c6c2-43ba-bbc6-2b1777b80fe9"` |

* パラメータ値が含まれていない場合、値はデータベース内で`empty`に設定されます。 既存のキーと値のペアが含まれていない場合、そのPOIのキーと値のペアはデータベースから削除されます。

