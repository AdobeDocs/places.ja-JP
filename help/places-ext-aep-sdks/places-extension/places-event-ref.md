---
title: 場所イベント参照
description: Places 拡張機能で処理されるイベントのリスト。
feature: Mobile SDK
exl-id: 98210ef4-5ff1-4792-b97b-2845ce02e78a
source-git-commit: f521d5e3b0b69977877d88382ce41fcb7d1c54b9
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 16%

---

# 場所イベント参照 {#places-event-reference}

以下は、Places 拡張機能で処理されるイベントのリストです。

## GetCurrentPointsOfInterest

**イベントの詳細**

| タイプ | ソース | 名前 | ペア |
| :--- | :--- | :--- | :--- |
| PLACES | REQUEST_コンテンツ | `requestgetuserwithinplaces` | True |

**イベントの説明**

このイベントは、デバイスが現在配置されている POI を取得するためのリクエストです。

**データペイロード定義**

該当なし

## GetNearcomerPointsOfInterest

**イベントの詳細**

| タイプ | ソース | 名前 | ペア |
| :--- | :--- | :--- | :--- |
| PLACES | REQUEST_コンテンツ | `requestgetnearbyplaces` | True |

**イベントの説明**

このイベントは、現在のデバイスの場所と設定済みの Places ライブラリを考慮して、近くの POI を取得するリクエストです。

**データペイロード定義**

| キー | 値タイプ | 必須 | デフォルト値 | 説明 |
| :--- | :--- | :--- | :--- | :--- |
| 緯度 | double | true | 該当なし | 近接する POI の検索の中心の緯度の値を保持します。 |
| 経度 | double | true | 該当なし | 近接する POI の検索の中心となる経度の値を保持します。 |
| 半径 | 整数 | 偽 | 該当なし | 近隣の POI の検索で使用される半径（メートル）。 |
| count | 整数 | 偽 | 10 | 結果の応答イベントで返される POI の最大数。 |

## ProcessRegionEvent

**イベントの詳細**

| タイプ | ソース | 名前 | ペア |
| :--- | :--- | :--- | :--- |
| PLACES | REQUEST_コンテンツ | `requestprocessregionevent` | False |

**イベントの説明**

このイベントにより、Places 拡張機能はジオフェンスのエントリまたは離脱イベントを処理します。

**データペイロード定義**

| キー | 値タイプ | 必須 | 説明 |
| :--- | :--- | :--- | :--- |
| regionid | 文字列 | true | イベントを生成する地域の ID。 |
| regioneventtype | int | true | 生成される地域イベントのタイプ。 入口の場合は 1、出口の場合は 2。 |

## Places 拡張機能によってディスパッチされたイベント

この情報は現在進行中です。
