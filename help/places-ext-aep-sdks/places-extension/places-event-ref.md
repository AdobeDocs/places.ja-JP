---
title: Places イベント参照
description: Places 拡張機能で処理されるイベントのリストです。
feature: Mobile SDK
exl-id: 98210ef4-5ff1-4792-b97b-2845ce02e78a
source-git-commit: f521d5e3b0b69977877d88382ce41fcb7d1c54b9
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 29%

---

# Places イベント参照 {#places-event-reference}

以下に、Places 拡張機能で処理されるイベントの一覧を示します。

## GetCurrentPointsOfInterest

**イベントの詳細**

| タイプ | ソース | 名前 | ペア |
| :--- | :--- | :--- | :--- |
| 場所 | REQUEST_CONTENT | `requestgetuserwithinplaces` | True |

**イベントの説明**

このイベントは、デバイスが現在存在する POI を取得するリクエストです。

**データペイロードの定義**

n/a

## GetNicherPointsOfInterest

**イベントの詳細**

| タイプ | ソース | 名前 | ペア |
| :--- | :--- | :--- | :--- |
| 場所 | REQUEST_CONTENT | `requestgetnearbyplaces` | True |

**イベントの説明**

このイベントは、現在のデバイスの場所と設定済みの Places ライブラリを考慮して、近くの POI を取得するリクエストです。

**データペイロードの定義**

| キー | 値のタイプ | 必須 | デフォルト値 | 説明 |
| :--- | :--- | :--- | :--- | :--- |
| latitude | double | true | n/a | 近くの POI の検索の中心の緯度値が格納されます。 |
| longitude | double | true | n/a | 近くの POI の検索の中心の経度値を保持します。 |
| 半径 | 整数 | false | n/a | 近くの POI の検索で使用される半径（メートル単位）。 |
| count | 整数 | false | 10 | 結果の応答イベントで返される POI の最大数。 |

## ProcessRegionEvent

**イベントの詳細**

| タイプ | ソース | 名前 | ペア |
| :--- | :--- | :--- | :--- |
| 場所 | REQUEST_CONTENT | `requestprocessregionevent` | False |

**イベントの説明**

このイベントにより、Places 拡張機能がジオフェンスのエントリまたは終了イベントを処理します。

**データペイロードの定義**

| キー | 値のタイプ | 必須 | 説明 |
| :--- | :--- | :--- | :--- |
| regionid | 文字列 | true | イベントを生成する地域の ID。 |
| regioneventtype | int | true | 生成される地域イベントのタイプ。 1 は入口、2 は出口です。 |

## Places 拡張機能によってディスパッチされるイベント

この情報は現在進行中です。
