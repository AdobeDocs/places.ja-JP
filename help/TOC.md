---
audience: end-user
user-guide-title: Places Service ガイド
user-guide-description: Places Service は、場所を認識するモバイルアプリで場所のコンテキストを理解できるようにする位置情報サービスです。
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 22%

---


# Places Service {#using}

+ [Places Service の概要](home.md)
+ [リリースノート](release-notes.md)
+ [はじめに](getting-started.md)
+ [Places Service へのアクセス権を取得](places-gain-access.md)
+ Places Service UI {#poi-mgmt-ui}
   + [Places Service UI の概要](poi-mgmt-ui/poi-mgmt-ui-overview.md)
   + [POI の作成](poi-mgmt-ui/create-a-poi-ui.md)
   + [以前に作成した POI を管理](poi-mgmt-ui/managing-pois-in-the-places-ui.md)
   + [POI でのメタデータの使用戦略](poi-mgmt-ui/metadata-with-pois.md)
   + [POI のバルクアップロード](poi-mgmt-ui/bulk-upload-pois.md)
   + [複数のライブラリを管理](poi-mgmt-ui/manage-libraries-in-the-places-ui.md)
+ Web サービス API {#web-service-api}
   + [Web サービス API の概要](web-service-api/places-web-services.md)
   + [統合の前提条件](web-service-api/adobe-i-o-integration.md)
   + API の使用 {#api-usage}
      + [API 使用の概要](web-service-api/api-usage/api-usage-overview.md)
      + [ヘッダーとパラメーター](web-service-api/api-usage/headers-and-parameters.md)
      + ライブラリの管理 {#manage-libraries}
         + [ライブラリ管理の概要](web-service-api/api-usage/manage-libraries/manage-libraries.md)
         + [ライブラリの作成](web-service-api/api-usage/manage-libraries/create-a-library.md)
         + [ライブラリの読み取り](web-service-api/api-usage/manage-libraries/read-a-library.md)
         + [ライブラリの更新](web-service-api/api-usage/manage-libraries/update-a-library.md)
         + [ライブラリの削除](web-service-api/api-usage/manage-libraries/delete-a-library.md)
         + [組織内のすべてのライブラリを読み取る](web-service-api/api-usage/manage-libraries/read-all-libraries-in-your-organization.md)
         + [ライブラリにランクを設定する](web-service-api/api-usage/manage-libraries/set-a-ran-on-your-libraries.md)
         + [ライブラリのランクを取得する](web-service-api/api-usage/manage-libraries/get-a-librarys-rank.md)
      + 目標地点の設定 {#manage-pois}
         + [POI の管理の概要](web-service-api/api-usage/manage-pois/manage-pois.md)
         + [POI の作成](web-service-api/api-usage/manage-pois/create-a-poi.md)
         + [POI を読む](web-service-api/api-usage/manage-pois/read-a-poi.md)
         + [POI の更新](web-service-api/api-usage/manage-pois/update-a-poi.md)
         + [POI の削除](web-service-api/api-usage/manage-pois/delete-a-poi.md)
         + [ライブラリ内のすべての POI の読み取り](web-service-api/api-usage/manage-pois/read-all-pois-in-a-library.md)
         + [組織内のすべての POI を読み取る](web-service-api/api-usage/manage-pois/read-all-pois-in-your-organization.md)
         + バッチ API {#batch-apis}
            + [バッチ API の概要](web-service-api/api-usage/manage-pois/batch-apis/batch-apis.md)
            + [複数の POI を作成](web-service-api/api-usage/manage-pois/batch-apis/create-multiple-pois.md)
            + [複数の POI を更新](web-service-api/api-usage/manage-pois/batch-apis/update-multiple-pois.md)
            + [複数の POI を削除](web-service-api/api-usage/manage-pois/batch-apis/delete-multiple-pois.md)
      + [クエリ API](web-service-api/api-usage/query-apis.md)
+ モバイル SDK の拡張機能 {#places-ext-aep-sdks}
   + Places 拡張機能 {#places-extension}
      + [Places 拡張機能](places-ext-aep-sdks/places-extension/places-extension.md)
      + [Places API リファレンス](places-ext-aep-sdks/places-extension/places-api-reference.md)
      + [Places イベント参照](places-ext-aep-sdks/places-extension/places-event-ref.md)
      + [Custom Places オブジェクト](places-ext-aep-sdks/places-extension/cust-places-objects.md)
+ [独自の監視ソリューションで Places Service を使用](using-your-own-monitor.md)
+ [アクティブな地域の監視なしで Places Service を使用](use-places-without-active-monitoring.md)
+ Places Service をワークフローの一部としてExperience Platform Launch {#use-places-launch-workflow}
   + [Places Service をワークフローの一部としてExperience Platform Launch](use-places-launch-workflow/places-launch-workflow.md)
   + [データ要素の定義](use-places-launch-workflow/define-data-elements.md)
   + [入口ルールと出口ルールの作成](use-places-launch-workflow/create-rule-places-property.md)
+ Places Service を他のAdobeソリューションと共に使用 {#use-places-with-other-solutions}
   + Adobe Analytics {#places-adobe-analytics}
      + [Adobe Analyticsでの Places Service の使用](use-places-with-other-solutions/places-adobe-analytics/use-places-analytics-overview.md)
      + [POI 入口および出口データを Analytics に送信](use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md)
      + [Analytics リクエストに場所コンテキストを追加](use-places-with-other-solutions/places-adobe-analytics/run-reports-aa-places-data.md)
      + [Analytics Workspace での場所データのレポート](use-places-with-other-solutions/places-adobe-analytics/places-in-workspace.md)
   + Adobe Mobile Services {#places-mobile-svcs-messaging}
      + [Adobe Mobile Services](use-places-with-other-solutions/places-mobile-svcs-for-messaging/use-places-mobie-svcs-messaging.md)
      + [プッシュ通知](use-places-with-other-solutions/places-mobile-svcs-for-messaging/mobile-svcs-messaging-push.md)
      + [アプリ内通知](use-places-with-other-solutions/places-mobile-svcs-for-messaging/mobile-svcs-messaging-inapp.md)
   + Adobe Campaign Standard {#places-acs}
      + [Adobe Campaign Standardでの Places Service の使用](use-places-with-other-solutions/places-acs/places-acs-overview.md)
      + [プッシュ通知](use-places-with-other-solutions/places-acs/places-acs-push-notifications.md)
      + [アプリ内メッセージ](use-places-with-other-solutions/places-acs/places-acs-in-app-messages.md)
   + Adobe Target {#places-target}
      + [Adobe Targetでの Places Service の使用](use-places-with-other-solutions/places-target/places-target.md)
+ テストと検証 {#places-testing-validation}
   + [Places Service のテストと検証](places-testing-validation/test-validate-places.md)
+ [よくある質問](places-faqs.md)
