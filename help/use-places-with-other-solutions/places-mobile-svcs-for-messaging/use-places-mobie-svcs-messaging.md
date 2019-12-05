---
title: Mobile Servicesでの場所のメッセージングでの使用
description: ここでは、Mobile Servicesでメッセージング用に場所を使用する方法について説明します。
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# Adobe Mobile Services {#places-mobile-services}

メッセージングにMobile Services Extensionを使用する前に、次の前提条件を確認します。

* 目標地点がロケーションサービスに作成されました。 必要に応じて、「ドキュメント」を参照してください。 （POI作成へのリンク）注意：ロケーションサービスには、レガシーAMSインターフェイス以外に存在する組織の目標地点データベースが新たに強化されました。 AMSの「場所を管理」ナビゲーションにあるPOIは、SDKのバージョン4でのみ機能します。
   * 以前のバージョンのSDK用のAMS内の従来のPlaces POI管理インターフェイスを次に示します。

      ![レガシーUI](/help/assets/legacy-location-v4-ui.png)

   * 以下に、ロケーションサービスのPOI管理インターフェイスを示します。

      ![ロケーションサービスPOI管理UI](/help/assets/places-ui.png)

* ACP SDKは、場所および/または場所モニターの拡張を使用して適切に設定されます。 つまり、モバイルアプリの起動ルールエンジンで、データをイベントや条件として使用できます。 必要に応じて、ドキュメントを参照してください。 (https://aep-sdks.gitbook.io/docs/beta/adobe-places)

* 起動ルールを作成し、モバイルアプリのACP SDKに公開する方法に詳しく説明します。 必要に応じて、ドキュメントを参照してください。 (https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine)

* 起動データ要素は、ルールで使用される場所SDK拡張データから作成されます。 ドキュメント(https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine#data-elements)を参照してください。

## レポート

レポートを使用する前に、次の前提条件を満たします。

* ロケーションサービスデータがAdobe Analyticsレポートスイートに正常に送信されました。 必要に応じて、Adobe Analyticsのドキュメントを参照してください（Steveのドキュメントへのリンク）。
* AMSのレポートに詳しい。 必要に応じて、ドキュメント(https://docs.adobe.com/content/help/en/mobile-services/using/reports-ug/usage.html)をご覧ください。

## レポートの視覚化

Adobe Analyticsに送信されるロケーションサービスデータを使用してAMSレポートを実行できます。 例えば、ユーザーがPOIにエントリを持つ場合にイベントを送信したとします。 このレポートでは、すぐに使用できるユーザーレポートの上に、POIエントリイベントのフィルターを追加しました。

![レポートの視覚化](/help/assets/report-visualize.png)

Adobe Analyticsインターフェイス内で、ロケーションサービスデータの視覚化に関する柔軟性が向上しました。

