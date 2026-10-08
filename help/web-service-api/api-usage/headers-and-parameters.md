---
title: ヘッダーとパラメーター
description: Places サービス REST APIで使用できるヘッダーとパラメーター。
exl-id: 3c7e76de-f0ff-4966-a3ec-7f64d819c140
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: d8704da9c84a066f72471421290d4b46c65f41e1
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 19%
---
# ヘッダーとパラメーター {#headers-and-parameters}

Places サービス REST APIで使用できるヘッダーとパラメーターの詳細を次に示します。

## サポートされるヘッダー

| ヘッダー | 説明 | メソッド | 例 |
| :--- | :--- | :--- | :--- |
| `Authorization` | ベアラートークン | すべて |  |
| `x-api-key` | あなたのAPI キー | すべて | `19776964b4cde49e08d8f62e5824f777b` |
| `x-gw-ims-org-id` | 組織ID | すべて | `18FB61145BAC2FFB0A494777@AdobeOrg` |
| `Content-Type` | 送受信されるコンテンツの形式 | PUT、POST | `application/json` |
| `Accept-Language` | エラーメッセージに使用される言語 | オプション | `en-US` |

## ライブラリパラメーター

| パラメーター | 説明 | タイプ | 上限 | リクエストまたはレスポンス | 例 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `id` | ライブラリ ID | 割り | 該当なし | 応答 | `"id": "b2488788-2d2a-462b-b1a2-305272777dda"` |
| `name` | ライブラリの名前 | 文字列 | 256 文字 | 両方（リクエストで必要） | `"name": "Amazing Places"` |
| `orgID` | 組織のExperience Cloud組織ID | 割り | 該当なし | 応答 | `"orgID": "777F20F55BACA09E0A495D8F@AdobeOrg"` |
| `poiCount` | ライブラリ内のPOIの数 | 整数 | 最大150,000 | 応答 | `"poiCount": 25149` |
| `metadataDescriptors` | 一意のPOI メタデータキー値ペアごとにカウント | 混在 | 該当なし | 応答 |  |
| `poiCountInCities` | ユニーク POI都市値ごとにカウント | 混在 | 該当なし | 応答 |  |

## POI パラメーター

| パラメーター | 説明 | タイプ | 上限 | リクエストまたはレスポンス | 例 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `data` | Poi データ | POIの詳細の配列 | 該当なし | 両方 |  |
| `id` | POIのID | 割り | 該当なし | 応答 | `"id": "1455462b-7f9c-4220-9f42-5bbce777a0d1"` |
| `name` | POIの名前 | 文字列 | 512 文字 | 両方、オプション\* | `"name": "My Favorite Place"` |
| `description` | POIの説明 | 文字列 | 512 文字 | 両方、オプション\* | `"description": "This is a very good place."` |
| `location` | POIの型と座標の配列 | 配列（混合） | 該当なし | 両方 | `"location": {"type": "Point", "coordinates": [-122.201007, 37.604713]` |
| `type` | POIの種類 | 文字列 | 現在「点」のみがサポートされています | 両方（リクエストで必要） | `"type": "Point"` |
| `coordinates` | POIの経度と緯度の配列 | 配列（浮動小数） | 経度：-180 ～ 180、緯度–85 ～ 85 | 両方（リクエストで必要） | `"coordinates": [-122.201007, 37.604713]` |
| `radius` | POIを中心とした円形ジオフェンスのサイズ | float | 10～2,000 メートル | 両方（リクエストで必要） | `"radius": 100` |
| `country` | POIの国 | 文字列 | 32 文字 | 両方、オプション* | `"country": "United States"` |
| `state` | POIの状態 | 文字列 | 32 文字 | 両方、オプション* | `"state": "California"` |
| `city` | POIのための都市 | 文字列 | 32 文字 | 両方、オプション* | `"city": "San Jose"` |
| `street` | POIの住所 | 文字列 | 256 文字 | 両方、オプション* | `"street": "122 Woz Way"` |
| `category` | POIのカテゴリ | 文字列 | 100 文字 | 両方、オプション* | `"category": "cafe"` |
| `icon` | POIのアイコン | 文字列 | 50 文字 | 両方、オプション* | `"icon": "star"` |
| `color` | POIのカラー | 文字列 | 8 文字 | 両方、オプション* | `"color": "blue"` |
| `metadata` | POIのキーと値のペアの配列 | array （string） | キー：256文字、値：256文字、最大10組 | 両方、オプション* | `"metadata": {"region": "Equator"}` |
| `lib_id` | POIが使用されているライブラリのID | 該当なし | 該当なし | 両方（必須） | `"lib_id": "ac7a0b25-c6c2-43ba-bbc6-2b1777b80fe9"` |

* パラメーター値が含まれていない場合、値はデータベースの`empty`に設定されます。 既存のキーと値のペアが含まれていない場合、そのキーと値のペアはデータベース内のそのPOIに対して削除されます。
