---
title: Places Service と Mobile Services を使用したメッセージング
description: この節では、Mobile Services で Places Service をメッセージングに使用する方法について説明します。
exl-id: dfa6b8bb-6bf2-44eb-8bfc-87294807ec3b
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 1%

---

# Adobe Mobile Services {#places-mobile-services}

メッセージングに Mobile Services 拡張機能を使用する前に、次の前提条件を確認してください。

* POI が Places Service に作成されました。 詳しくは、[POI の作成 ](/help/poi-mgmt-ui/create-a-poi-ui.md) を参照してください。

  >[!IMPORTANT]
  >
  >Places Service には、従来の Mobile Services UI 外に存在する組織用の新しく改善された POI データベースが含まれています。 Mobile Service *場所を管理* ページナビゲーション上の POI は、SDK のバージョン 4 でのみ機能します。

* 旧バージョンの SDK 用の、レガシー Mobile Services UI の *Manage Places* POI 管理ページを次に示します。

  ![ レガシー UI](/help/assets/legacy-location-v4-ui.png)

* 次に Places Service UI を示します。

  ![Places Service POI 管理 UI](/help/assets/places-ui.png)

* ACP SDK が Places 拡張機能で適切に設定されている。

  つまり、データは、モバイルアプリのExperience Platform Launchルールエンジンでイベントや条件として使用できます。 詳しくは、[Places 拡張機能 ](/help/places-ext-aep-sdks/places-extension/places-extension.md) を参照してください。

* モバイルアプリでExperience Platform Launchルールを作成し、ACP SDK に公開する方法を理解します。

  詳しくは、[ ルールエンジン ](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine) を参照してください。

* Experience Platform Launchデータ要素は、ルールエンジンで使用される Places 拡張機能データから作成されます。

  詳しくは、[ データ要素 ](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine#data-elements) を参照してください。

## レポート

レポートを使用する前に、次の前提条件を満たします。

* Places Service データをAdobe Analytics レポートスイートに正常に送信しました。

  詳しくは、[Adobe Analyticsで Places Service を使用する ](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md) を参照してください。

* Mobile Services のレポートについて理解します。

  詳しくは、[ レポート ](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.html?lang=ja) を参照してください。

## レポートビジュアライゼーション

Adobe Analyticsに送信される Places Service データを使用して、Mobile Service レポートを実行できます。 次の例では、ユーザーがいずれかの POI にエントリを持つと、イベントが送信されます。 このレポートでは、標準のユーザーレポートに POI エントリイベントのフィルターが追加されました。

![ レポートのビジュアライゼーション ](/help/assets/report-visualize.png)

Places Service データを柔軟に視覚化できる機能が、Adobe Analytics インターフェイスで利用できます。
