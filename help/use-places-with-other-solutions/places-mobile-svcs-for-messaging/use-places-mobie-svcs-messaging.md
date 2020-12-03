---
title: Places ServiceとMobile Servicesのメッセージングの使用
description: この節では、Places ServiceとMobile Servicesを使用したメッセージングの使用方法を示します。
translation-type: tm+mt
source-git-commit: 5a21e734c0ef56c815389a9f08b445bedaae557a
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 1%

---


# Adobe Mobile Services {#places-mobile-services}

メッセージングにMobile Services Extensionを使用する前に、次の前提条件を確認します。

* 目標地点はPlaces Serviceで作成されました。 For more information, see [Create a POI](/help/poi-mgmt-ui/create-a-poi-ui.md).

   >[!IMPORTANT]
   >
   >Places Serviceには、従来のMobile Services UIの外部に存在する組織のPOIデータベースが新たに追加され、改善されました。 Mobile Service *Manage Placess* ページナビゲーションにあるPOIは、SDKバージョン4でのみ機能します。

* 以前のバージョンのSDK用のレガシーMobile Services UIの場所 *POI管理の* 管理ページを次に示します。

   ![レガシーUI](/help/assets/legacy-location-v4-ui.png)

* Places Service UIは次のとおりです。

   ![Places Service POI管理UI](/help/assets/places-ui.png)

* ACP SDKは、Places Service拡張および/またはPlaces Monitor拡張を使用して正しく設定されます。

   つまり、モバイルアプリのExperience Platform Launchルールエンジンで、イベントや条件としてデータを使用できます。 詳しくは、「 [Places拡張子](/help/places-ext-aep-sdks/places-extension/places-extension.md) 」または「 [Places Monitor拡張子](/help/places-ext-aep-sdks/places-monitor-extension/using-places-monitor-extension.md)」を参照してください。

* モバイルアプリのACP SDKに対するExperience Platform Launchルールの作成と公開について説明します。

   For more information, see [Rules engine](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine).

* Experience Platform Launchデータ要素は、ルールエンジンで使用されるPlaces拡張データから作成されます。

   For more information, see [Data elements](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine#data-elements).

## レポート

レポートを使用する前に、次の前提条件を満たします。

* PlacesサービスのデータがAdobe Analyticsレポートスイートに正常に送信されました。

   詳しくは、「Adobe Analyticsでプレースサービスを [使用する](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md)」を参照してください。

* Mobile Servicesのレポートについて理解します。

   For more information, see [Reports](https://docs.adobe.com/content/help/en/mobile-services/using/reports-ug/usage.html).

## レポート可視化

Adobe Analyticsに送信されるPlaces Serviceデータを使用して、Mobile Serviceレポートを実行できます。 次の例では、POIの1つにエントリがある場合にイベントが送信されます。 このレポートでは、POIエントリイベントのフィルターが追加され、すぐに使用できるユーザーレポートに表示されます。

![レポートの視覚化](/help/assets/report-visualize.png)

Places Serviceデータを視覚化する際の柔軟性は、Adobe Analyticsのインターフェースでも追加できます。

