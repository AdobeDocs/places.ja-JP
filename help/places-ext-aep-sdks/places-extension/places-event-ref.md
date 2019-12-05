---
title: イベント参照を配置
description: 'Places拡張で処理されるイベントのリストです。 '
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# イベント参照を配置 {#places-event-reference}

Places拡張で処理されるイベントの一覧を次に示します。

## GetCurrentPointsOfInterest

**イベントの詳細**

| タイプ | ソース | 名前 | ペア |
| :--- | :--- | :--- | :--- |
| 場所 | REQUEST_CONTENT | `requestgetuserwithinplaces` | True |

**イベントの説明**

このイベントは、デバイスが現在存在するPOIを取得する要求です。

**データペイロードの定義**

なし

## GetNicheredPointsOfInterest

**イベントの詳細**

| タイプ | ソース | 名前 | ペア |
| :--- | :--- | :--- | :--- |
| 場所 | REQUEST_CONTENT | `requestgetnearbyplaces` | True |

**イベントの説明**

このイベントは、現在のデバイスの場所と設定済みの場所ライブラリを考慮して、近くのPOIを取得する要求です。

**データペイロードの定義**

| キー | 値のタイプ | 必須 | デフォルト値 | 説明 |
| :--- | :--- | :--- | :--- | :--- |
| 緯度 | double | true | なし | 近くのPOIの検索中心の緯度の値を保持します。 |
| 経度 | double | true | なし | 近くのPOIを検索する中心の経度値を保持します。 |
| radius | 整数 | false | なし | 周辺のPOIを検索する際に使用する半径（メートル単位）。 |
| count | 整数 | false | 10 | 結果の応答イベントで返すPOIの最大数。 |

## ProcessRegionEvent

**イベントの詳細**

| タイプ | ソース | 名前 | ペア |
| :--- | :--- | :--- | :--- |
| 場所 | REQUEST_CONTENT | `requestprocessregionevent` | False |

**イベントの説明**

このイベントは、Places拡張でジオフェンスエントリまたは終了イベントを処理する原因となります。

**データペイロードの定義**

| キー | 値のタイプ | 必須 | 説明 |
| :--- | :--- | :--- | :--- |
| 地域 | string | true | イベントを生成する領域のID。 |
| regioneventtype | int | true | 生成される領域イベントのタイプ。 入口は1、出口は2です。 |

## Places拡張機能によってディスパッチされるイベント

この情報は現在処理中です。

