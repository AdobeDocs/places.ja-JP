---
title: 配置イベント参照
description: 'Places拡張で処理されるイベントのリストです。 '
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 29%

---


# 配置イベント参照 {#places-event-reference}

Places拡張で処理されるイベントのリストを以下に示します。

## GetCurrentPointsOfInterest

**イベントの詳細**

| タイプ | ソース | 名前 | ペア |
| :--- | :--- | :--- | :--- |
| 場所 | REQUEST_CONTENT | `requestgetuserwithinplaces` | True |

**イベントの説明**

このイベントは、デバイスが現在配置されているPOIを取得する要求です。

**データペイロードの定義**

なし

## GetNichroedPointsOfInterest

**イベントの詳細**

| タイプ | ソース | 名前 | ペア |
| :--- | :--- | :--- | :--- |
| 場所 | REQUEST_CONTENT | `requestgetnearbyplaces` | True |

**イベントの説明**

このイベントは、現在のデバイスの場所と設定済みのPlacesライブラリを考慮して、近くのPOIを取得する要求です。

**データペイロードの定義**

| キー | 値のタイプ | 必須 | デフォルト値 | 説明 |
| :--- | :--- | :--- | :--- | :--- |
| latitude | double | true | n/a | 近くのPOIを検索する際の中心の緯度の値を保持します。 |
| longitude | double | true | n/a | 近くのPOIを検索する中心の経度値を保持します。 |
| radius | 整数 | false | なし | 周辺のPOIを検索する際に使用する半径（メートル単位）。 |
| count | 整数 | false | 10 | 結果の応答イベントに返すPOIの最大数。 |

## ProcessRegionEvent

**イベントの詳細**

| タイプ | ソース | 名前 | ペア |
| :--- | :--- | :--- | :--- |
| 場所 | REQUEST_CONTENT | `requestprocessregionevent` | False |

**イベントの説明**

このイベントにより、Places拡張でジオフェンスの入口または出口イベントが処理されます。

**データペイロードの定義**

| キー | 値のタイプ | 必須 | 説明 |
| :--- | :--- | :--- | :--- |
| regionid | 文字列 | true | イベントを生成する地域のID。 |
| regioneventtype | int | true | 生成される地域イベントのタイプ。 1は入口、2は出口です。 |

## Places拡張機能によってディスパッチされるイベント

この情報は現在進行中です。

