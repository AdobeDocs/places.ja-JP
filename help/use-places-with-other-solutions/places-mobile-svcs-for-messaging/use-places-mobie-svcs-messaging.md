---
title: Places サービスとMobile Servicesを使用したメッセージ
description: この節では、Places サービスをMobile Servicesと共に使用してメッセージを送信する方法について説明します。
exl-id: dfa6b8bb-6bf2-44eb-8bfc-87294807ec3b
TQID: https://experienceleague.adobe.com/-axuli6p-QHthMkucGLCcgyHCqrwudXmif-dZwpGli4
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2:
  - id: b069d60e-95f3-44d6-95a8-ddc862a4bc38
  - id: c20d46e7-1c7d-476c-a50e-3961d4dce35f
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 359
ht-degree: 3%

---

# Adobe Mobile Services {#places-mobile-services}

メッセージにMobile Services拡張機能を使用する前に、次の前提条件を確認してください。

* Places サービスでポイントが作成されました。 詳細については、[POIの作成](/help/poi-mgmt-ui/create-a-poi-ui.md)を参照してください。

  >[!IMPORTANT]
  >
  >Places サービスには、従来のMobile Services UIの外に存在する、組織用に新しく改善されたPOI データベースが含まれています。 モバイルサービス *場所の管理* ページナビゲーションにあるPOIは、SDKのバージョン 4でのみ機能します。

* 古いバージョンのSDKの従来のMobile Services UIの&#x200B;*Manage Places* POI管理ページを次に示します。

  ![&#x200B; レガシーUI](/help/assets/legacy-location-v4-ui.png)

* Places サービス UIを次に示します。

  ![Places サービス POI管理UI](/help/assets/places-ui.png)

* ACP SDKは、Places拡張機能で適切に設定されます。

  つまり、データは、モバイルアプリのExperience Platform Launch ルールエンジンでイベントや条件として使用できます。 詳しくは、[Places拡張機能](/help/places-ext-aep-sdks/places-extension/places-extension.md)を参照してください。

* Experience Platform Launch ルールの作成と、モバイルアプリ内のACP SDKへの公開について詳しく説明します。

  詳しくは、[&#x200B; ルールエンジン &#x200B;](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine)を参照してください。

* Experience Platform Launch データ要素は、ルールエンジンで使用されるPlaces拡張機能データから作成されます。

  詳しくは、[&#x200B; データ要素](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine#data-elements)を参照してください。

## レポート

レポートを使用する前に、次の前提条件を満たしてください。

* Places サービスデータをAdobe Analytics レポートスイートに正常に送信しました。

  詳しくは、[Adobe AnalyticsでのPlaces サービスの使用](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md)を参照してください。

* モバイルサービスのレポート機能。

  詳しくは、[&#x200B; レポート &#x200B;](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.html?lang=ja)を参照してください。

## レポートの可視化

Adobe Analyticsに送信されるPlaces サービスデータを使用して、モバイルサービスレポートを実行できます。 次の例では、ユーザーがいずれかのPOIにエントリを持っている場合にイベントが送信されます。 このレポートでは、POI エントリイベントのフィルターが、標準のユーザーレポートに追加されました。

![&#x200B; レポートの可視化](/help/assets/report-visualize.png)

Places サービスデータのビジュアライゼーションに関する柔軟性は、Adobe Analytics インターフェイスで追加できます。
