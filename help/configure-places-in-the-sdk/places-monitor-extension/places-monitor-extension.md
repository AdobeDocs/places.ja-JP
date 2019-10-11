---
title: プレースモニタ拡張機能
seo-title: プレースモニタ拡張機能
description: プレースモニター拡張機能は、オペレーティングシステムとのやりとりを処理して、ユーザーに最も近いPOIを登録および監視します。
seo-description: 'プレースモニター拡張機能は、オペレーティングシステムとのやりとりを処理して、ユーザーに最も近いPOIを登録および監視します。 '
translation-type: tm+mt
source-git-commit: a785b75ccbed2a62d0e9f77b5c17dae9447b0629

---


# プレースモニタ拡張機能 {#places-monitor-extension}

プレースモニター拡張機能は、オペレーティングシステムとのやりとりを処理して、ユーザーに最も近いPOIを登録および監視します。 この拡張機能は、Places拡張から登録する必要があるPOIを取得し、入口および出口通知をPlaces拡張に渡します。 これらの通知は、エクスペリエンスプラットフォーム起動ルールでイベントとして使用できます。

一部のお客様は、オペレーティングシステムの地域を既に監視している場合があるので、Monitor拡張はオプションです。 この場合、Places拡張APIを追加して、Placesデータベースから最も近いPOIを受け取り、エントリイベントと終了イベントも渡して、適切なアクションを実行できるようにします。