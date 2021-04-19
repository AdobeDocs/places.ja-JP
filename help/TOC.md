---
audience: end-user
user-guide-title: Places Service ガイド
user-guide-description: Places Service は、場所を認識するモバイルアプリで場所のコンテキストを理解できるようにする位置情報サービスです。
translation-type: tm+mt
source-git-commit: 12283d11829ee70a808bc11d2bc1241cb1770ac3
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 19%

---


# Places Service {#using}

+ [Placesサービスの概要](home.md)
+ [リリースノート](release-notes.md)
+ [はじめに](getting-started.md)
+ [Placesサービスへのアクセス権を取得](places-gain-access.md)
+ Places Service UI {#poi-mgmt-ui}
   + [PlacesサービスUIの概要](poi-mgmt-ui/poi-mgmt-ui-overview.md)
   + [POIの作成](poi-mgmt-ui/create-a-poi-ui.md)
   + [以前に作成したPOIの管理](poi-mgmt-ui/managing-pois-in-the-places-ui.md)
   + [POIでのメタデータの使用方法](poi-mgmt-ui/metadata-with-pois.md)
   + [POIの一括アップロード](poi-mgmt-ui/bulk-upload-pois.md)
   + [複数のライブラリの管理](poi-mgmt-ui/manage-libraries-in-the-places-ui.md)
+ WebサービスAPI {#web-service-api}
   + [WebサービスAPIの概要](web-service-api/places-web-services.md)
   + [統合の前提条件](web-service-api/adobe-i-o-integration.md)
   + APIの使用{#api-usage}
      + [APIの使用の概要](web-service-api/api-usage/api-usage-overview.md)
      + [ヘッダーとパラメーター](web-service-api/api-usage/headers-and-parameters.md)
      + ライブラリの管理{#manage-libraries}
         + [ライブラリの管理の概要](web-service-api/api-usage/manage-libraries/manage-libraries.md)
         + [ライブラリの作成](web-service-api/api-usage/manage-libraries/create-a-library.md)
         + [ライブラリの読み取り](web-service-api/api-usage/manage-libraries/read-a-library.md)
         + [ライブラリの更新](web-service-api/api-usage/manage-libraries/update-a-library.md)
         + [ライブラリの削除](web-service-api/api-usage/manage-libraries/delete-a-library.md)
         + [組織内のすべてのライブラリを読み取る](web-service-api/api-usage/manage-libraries/read-all-libraries-in-your-organization.md)
         + [ライブラリにランクを設定する](web-service-api/api-usage/manage-libraries/set-a-ran-on-your-libraries.md)
         + [ライブラリのランクを取得する](web-service-api/api-usage/manage-libraries/get-a-librarys-rank.md)
      + 目標地点の設定 {#manage-pois}
         + [POIの管理の概要](web-service-api/api-usage/manage-pois/manage-pois.md)
         + [POIの作成](web-service-api/api-usage/manage-pois/create-a-poi.md)
         + [POIの読み取り](web-service-api/api-usage/manage-pois/read-a-poi.md)
         + [POIの更新](web-service-api/api-usage/manage-pois/update-a-poi.md)
         + [POIの削除](web-service-api/api-usage/manage-pois/delete-a-poi.md)
         + [ライブラリのすべてのPOIを読み取る](web-service-api/api-usage/manage-pois/read-all-pois-in-a-library.md)
         + [組織内のすべてのPOIを読み取る](web-service-api/api-usage/manage-pois/read-all-pois-in-your-organization.md)
         + バッチAPI {#batch-apis}
            + [バッチAPIの概要](web-service-api/api-usage/manage-pois/batch-apis/batch-apis.md)
            + [複数のPOIの作成](web-service-api/api-usage/manage-pois/batch-apis/create-multiple-pois.md)
            + [複数のPOIの更新](web-service-api/api-usage/manage-pois/batch-apis/update-multiple-pois.md)
            + [複数のPOIの削除](web-service-api/api-usage/manage-pois/batch-apis/delete-multiple-pois.md)
      + [クエリAPI](web-service-api/api-usage/query-apis.md)
+ モバイルSDKの拡張{#places-ext-aep-sdks}
   + Places 拡張機能 {#places-extension}
      + [Places 拡張機能](places-ext-aep-sdks/places-extension/places-extension.md)
      + [Places APIリファレンス](places-ext-aep-sdks/places-extension/places-api-reference.md)
      + [配置イベント参照](places-ext-aep-sdks/places-extension/places-event-ref.md)
      + [カスタム配置オブジェクト](places-ext-aep-sdks/places-extension/cust-places-objects.md)
   + モニターの拡張{#places-monitor-extension}を配置
      + [配置モニタ拡張](places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md)
      + [「Places Monitor」拡張機能の使用](places-ext-aep-sdks/places-monitor-extension/using-places-monitor-extension.md)
      + [Places Monitor APIリファレンス](places-ext-aep-sdks/places-monitor-extension/places-monitor-api-reference.md)
+ [独自の監視ソリューションでPlaces Serviceを使用](using-your-own-monitor.md)
+ [Places Serviceを地域の監視なしで使用](use-places-without-active-monitoring.md)
+ Experience Platform Launchワークフロー{#use-places-launch-workflow}の一部としてPlaces Serviceを使用
   + [Experience Platform Launchワークフローの一部としてPlaces Serviceを使用](use-places-launch-workflow/places-launch-workflow.md)
   + [データ要素の定義](use-places-launch-workflow/define-data-elements.md)
   + [入口ルールと出口ルールの作成](use-places-launch-workflow/create-rule-places-property.md)
+ 他のAdobeソリューションと共にPlacesサービスを使用{#use-places-with-other-solutions}
   + Adobe Analytics {#places-adobe-analytics}
      + [Adobe Analyticsでプレイスサービスを使用](use-places-with-other-solutions/places-adobe-analytics/use-places-analytics-overview.md)
      + [POIの入口データと出口データをAnalyticsに送信](use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md)
      + [Analytics追加リクエストの場所のコンテキスト](use-places-with-other-solutions/places-adobe-analytics/run-reports-aa-places-data.md)
      + [Analytics Workspaceの場所データに関するレポート](use-places-with-other-solutions/places-adobe-analytics/places-in-workspace.md)
   + Adobe Mobile Services {#places-mobile-svcs-messaging}
      + [Adobe Mobile Services](use-places-with-other-solutions/places-mobile-svcs-for-messaging/use-places-mobie-svcs-messaging.md)
      + [プッシュ通知](use-places-with-other-solutions/places-mobile-svcs-for-messaging/mobile-svcs-messaging-push.md)
      + [アプリ内通知](use-places-with-other-solutions/places-mobile-svcs-for-messaging/mobile-svcs-messaging-inapp.md)
   + Adobe Campaign Standard {#places-acs}
      + [Adobe Campaign Standardでプレイスサービスを使用](use-places-with-other-solutions/places-acs/places-acs-overview.md)
      + [プッシュ通知](use-places-with-other-solutions/places-acs/places-acs-push-notifications.md)
      + [アプリ内メッセージ](use-places-with-other-solutions/places-acs/places-acs-in-app-messages.md)
   + Adobe Target {#places-target}
      + [Adobe Targetでプレイスサービスを使用](use-places-with-other-solutions/places-target/places-target.md)
+ テストと検証 {#places-testing-validation}
   + [Placesサービスのテストと検証](places-testing-validation/test-validate-places.md)
+ [よくある質問](places-faqs.md)
