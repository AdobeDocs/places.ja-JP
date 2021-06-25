---
title: Places監視拡張機能
description: Places監視拡張機能は、オペレーティングシステムとのやり取りを処理して、ユーザーに最も近いPOIを登録および監視します。
exl-id: 254b33a0-79c4-4d51-8835-16e60f5c055e
source-git-commit: 8dcd777acf5d578b748afae9aa609c2349ea94a9
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 0%

---

# Places監視拡張機能 {#places-monitor-extension}

Places監視拡張機能は、オペレーティングシステムとのやり取りを処理して、ユーザーに最も近いPOIを登録および監視します。 この拡張機能は、Places拡張機能から登録する必要があるPOIを取得し、入口通知と出口通知をPlaces拡張機能に渡します。 これらの通知は、イベントルールでExperience Platform Launchとして使用できます。

一部のお客様は既にオペレーティングシステムの地域を監視している可能性があるので、監視拡張機能はオプションです。 その場合は、Places拡張機能APIを追加して、Placesサービスデータベースから最も近いPOIを受け取り、エントリイベントとexitイベントも渡して適切なアクションを実行できるようにしてください。

## Places Monitorの廃止

2021年8月31日に、Adobe Experience Platform Mobile SDKのPlaces Monitor拡張機能は非推奨となります。 Places監視拡張機能は、8月31日以降は更新やサポートを受けません。

現在Places Monitor拡張機能を使用しているお客様は、Adobeを通じて追加の更新やサポートが提供されないことを理解したうえで、この拡張機能を引き続き使用できます。

Places Monitor拡張機能の廃止は、Places Service拡張機能に影響を与えることも、悪影響を与えることもありません。拡張機能と更新機能は引き続きサポートされます。

Places監視拡張機能から独自の監視ソリューションへの移行を検討しているお客様は、以下のドキュメントを確認してください。[独自の監視ソリューション](https://experienceleague.adobe.com/docs/places/using/using-your-own-monitor.html?lang=en)と共にPlaces Serviceを使用します。 このドキュメントでは、iOSまたはGoogle Playから[コアロケーションサービス](https://developer.apple.com/documentation/corelocation)または[ロケーションサービス](https://developers.google.com/android/reference/com/google/android/gms/location/package-summary)を実装して、Places Serviceとやり取りする方法を説明します。
