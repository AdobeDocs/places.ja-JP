---
title: Mobile ServicesでのPlacesサービスのメッセージング用の使用
description: この節では、Places ServiceとMobile Servicesを使用したメッセージングの使用方法を示します。
translation-type: tm+mt
source-git-commit: 5a21e734c0ef56c815389a9f08b445bedaae557a

---


# Adobe Mobile Services {#places-mobile-services}

メッセージングにMobile Services Extensionを使用する前に、次の前提条件を確認します。

* 目標地点はPlaces Serviceで作成されました。 For more information, see [Create a POI](/help/poi-mgmt-ui/create-a-poi-ui.md).

   >[!IMPORTANT]
   >
   >Placesサービスには、従来のMobile Services UIの外部に存在する、組織用の新しい強化されたPOIデータベースが含まれています。 Mobile Service *Manage PlacessページナビゲーションにあるPOIは* 、SDKバージョン4でのみ機能します。

* 以前のバージ *ョンのSDK用のレガシーMobile Services UIの場所* POI管理ページを次に示します。

   ![レガシーUI](/help/assets/legacy-location-v4-ui.png)

* PlacesサービスのUIを次に示します。

   ![PlacesサービスPOI管理UI](/help/assets/places-ui.png)

* ACP SDKは、Places Service拡張またはPlaces Monitor拡張を使用して正しく設定されています。

   つまり、モバイルアプリのエクスペリエンスプラットフォーム起動ルールエンジンで、データをイベントや条件として使用できます。 詳しくは、「場所」拡張機能または「場所 [モニター](/help/places-ext-aep-sdks/places-extension/places-extension.md) 」拡張 [機能を参照してください](/help/places-ext-aep-sdks/places-monitor-extension/using-places-monitor-extension.md)。

* モバイルアプリのACP SDKに対するエクスペリエンスプラットフォーム起動ルールの作成と公開について説明します。

   For more information, see [Rules engine](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine).

* エクスペリエンスプラットフォーム起動データ要素は、ルールエンジンで使用される場所拡張データから作成されます。

   For more information, see [Data elements](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine#data-elements).

## レポート

レポートを使用する前に、次の前提条件を満たします。

* PlacesサービスのデータがAdobe Analyticsレポートスイートに正常に送信されました。

   詳しくは、「Adobe AnalyticsでのPlacesサ [ービスの使用」を参照してください](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md)。

* Mobile Servicesのレポートについて理解します。

   For more information, see [Reports](https://docs.adobe.com/content/help/en/mobile-services/using/reports-ug/usage.html).

## レポートの視覚化

Adobe Analyticsに送信されるPlaces Serviceデータを使用して、Mobile Serviceレポートを実行できます。 次の例では、ユーザーがPOIのいずれかにエントリを持つ場合にイベントが送信されます。 このレポートでは、POIエントリイベントのフィルターが追加され、すぐに使用できるユーザーレポートに表示されます。

![レポートの視覚化](/help/assets/report-visualize.png)

Places Serviceデータを視覚化する際の柔軟性がAdobe Analyticsインターフェイスでも向上しました。

