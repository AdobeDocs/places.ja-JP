---
title: Places Service と Mobile Services を使用したメッセージの送信
description: ここでは、Places Service を Mobile Services と共に使用してメッセージを送信する方法について説明します。
exl-id: dfa6b8bb-6bf2-44eb-8bfc-87294807ec3b
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 1%

---

# Adobe Mobile Services {#places-mobile-services}

Mobile Services 拡張機能をメッセージに使用する前に、次の前提条件を確認します。

* Places Service に目標地点が作成されました。 詳しくは、 [POI の作成](/help/poi-mgmt-ui/create-a-poi-ui.md).

  >[!IMPORTANT]
  >
  >Places Service には、従来の Mobile Services UI 以外に存在する、組織のための新しく改善された POI データベースが含まれています。 Mobile Service にある POI *配置の管理* ページナビゲーションは、SDK バージョン 4 でのみ機能します。

* こちらが *場所を管理* 以前のバージョンの SDK 用のレガシー Mobile Services UI の POI 管理ページ：

  ![レガシー UI](/help/assets/legacy-location-v4-ui.png)

* 次に、Places Service UI を示します。

  ![Places Service POI 管理 UI](/help/assets/places-ui.png)

* ACP SDK は、Places 拡張機能で適切に構成されています。

  つまり、データは、モバイルアプリのイベントルールエンジンで、Experience Platform Launchや条件として使用できます。 詳しくは、 [Places 拡張機能](/help/places-ext-aep-sdks/places-extension/places-extension.md).

* モバイルアプリで ACP SDK に対するExperience Platform Launch・ルールを作成し、公開する方法を説明します。

  詳しくは、 [ルールエンジン](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine).

* Experience Platform Launchデータ要素は、ルールエンジンで使用される Places 拡張機能データから作成されます。

  詳しくは、 [データ要素](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine#data-elements).

## レポート

レポートを使用する前に、次の前提条件を満たします。

* Places Service のデータがAdobe Analytics Report Suite に正常に送信されました。

  詳しくは、 [Adobe Analyticsでの Places Service の使用](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md).

* Mobile Services のレポートについて説明します。

  詳しくは、 [レポート](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.html).

## レポートのビジュアライゼーション

Adobe Analyticsに送信される Places Service データを使用して、Mobile Services レポートを実行できます。 次の例では、ユーザーがいずれかの POI にエントリを持つ場合にイベントが送信されます。 このレポートでは、標準のユーザーレポートに POI エントリイベントのフィルターが追加されています。

![レポートのビジュアライゼーション](/help/assets/report-visualize.png)

Places Service データを視覚化する柔軟性が向上したのは、Adobe Analyticsインターフェイスです。
