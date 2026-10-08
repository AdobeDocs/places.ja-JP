---
title: Places イベント参照
description: Places拡張機能で処理されるイベントのリスト。
feature: Mobile SDK
exl-id: 98210ef4-5ff1-4792-b97b-2845ce02e78a
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
feature_v2:
  - id: a8a79b8d-fdca-499c-a5ef-f88a099d8eb9
    internal-label: Mobile SDK
source-git-commit: d8704da9c84a066f72471421290d4b46c65f41e1
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 17%
---
# Places イベント参照 {#places-event-reference}

Places拡張機能で処理されるイベントのリストを次に示します。

## GetCurrentPointsOfInterest

**イベントの詳細**

| タイプ | ソース | 名前 | ペア |
| :--- | :--- | :--- | :--- |
| PLACES | REQUEST_CONTENT | `requestgetuserwithinplaces` | True |

**イベントの説明**

このイベントは、デバイスが現在配置されているPOIを取得するためのリクエストです。

**データペイロード定義**

該当なし

## GetNearbyPointsOfInterest

**イベントの詳細**

| タイプ | ソース | 名前 | ペア |
| :--- | :--- | :--- | :--- |
| PLACES | REQUEST_CONTENT | `requestgetnearbyplaces` | True |

**イベントの説明**

このイベントは、現在のデバイスの場所と設定されたPlaces ライブラリを考慮して、近くのPOIを取得するためのリクエストです。

**データペイロード定義**

| キー | 値タイプ | 必須 | デフォルト値 | 説明 |
| :--- | :--- | :--- | :--- | :--- |
| 緯度 | double | true | 該当なし | 近くのPOIの検索の中心の緯度値を保持します。 |
| 経度 | double | true | 該当なし | 近くのPOIの検索の中心の経度値を保持します。 |
| 半径 | 整数 | false | 該当なし | 半径（メートル）。近くのPOIの検索で使用されます。 |
| count | 整数 | false | 10 | 結果として返される応答イベントのPOIの最大数。 |

## ProcessRegionEvent

**イベントの詳細**

| タイプ | ソース | 名前 | ペア |
| :--- | :--- | :--- | :--- |
| PLACES | REQUEST_CONTENT | `requestprocessregionevent` | False |

**イベントの説明**

このイベントにより、Places拡張機能がジオフェンスの入口または出口イベントを処理します。

**データペイロード定義**

| キー | 値タイプ | 必須 | 説明 |
| :--- | :--- | :--- | :--- |
| regionid | 文字列 | true | イベントを生成する地域のID。 |
| regioneventtype | int | true | 生成する地域イベントのタイプ。 入口は1、出口は2。 |

## Places拡張機能によってディスパッチされるイベント

この情報は現在公開中です。
