---
title: 配置モニタ拡張
description: プレースモニター拡張機能は、オペレーティングシステムとのやり取りを処理し、ユーザーに最も近いPOIを登録および監視します。
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 0%

---


# モニターの拡張{#places-monitor-extension}を配置

プレースモニター拡張機能は、オペレーティングシステムとのやり取りを処理し、ユーザーに最も近いPOIを登録および監視します。 この拡張機能は、Places拡張から登録する必要があるPOIを取得し、入口および出口の通知をPlaces拡張に渡します。 これらの通知は、Experience Platform Launchルールでイベントとして使用できます。

一部のお客様は、オペレーティングシステムで既に地域を監視している可能性があるので、Monitor拡張はオプションです。 この場合、Places Serviceデータベースから最も近いPOIを受け取るPlaces拡張APIを追加し、エントリと終了イベントも渡して、適切なアクションを実行できるようにします。
