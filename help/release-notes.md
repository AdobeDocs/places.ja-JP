---
title: リリースノート
description: Places サービスのリリースノート。
exl-id: 76da9548-4e32-4b23-9a15-7012973915f3
TQID: https://experienceleague.adobe.com/yo1eXPl9cKbp-EVWQT8gZHcAbSDoIFJVD6xKbdoysMc
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
  - id: f002a92a-b99f-47a4-90c8-65e0e415bc7a
feature_v2:
  - id: b069d60e-95f3-44d6-95a8-ddc862a4bc38
  - id: bef6f891-2e8a-425e-8f99-7ddf22070daa
  - id: d833d0ef-8ed5-4cff-a5e7-9f12abd02a31
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
  - id: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: d3cdead0-685a-4489-9250-4bb709942f66
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 1612
ht-degree: 4%

---

# リリースノート {#release-notes}

## 2020 年 7 月 9 日

* **Places and Places Monitor Extensions**

   * [React Native アプリケーション &#x200B;](https://aep-sdks.gitbook.io/docs/resources/upgrading-to-aep/current-sdk-versions#react-native)のPlacesおよびPlaces Monitor拡張機能が追加されました
   * [Cordova アプリケーション &#x200B;](https://aep-sdks.gitbook.io/docs/resources/upgrading-to-aep/current-sdk-versions#cordova)の場所と場所のモニター拡張機能が追加されました
   * 詳細については、[Places拡張機能の使用](https://experienceleague.adobe.com/docs/places/using/places-ext-aep-sdks/places-extension/places-extension.html)を参照してください。


## 2020年5月12日（PT）

* **Places サービス**

   * 「POIのインポート」ボタンを使用して、CSV ファイルからPOIを一括読み込み
   * 複数のPOIを選択し、メタデータ値を一括編集または追加します

## 2020年5月6日（PT）

* **PlacesMonitor 2.2.1**

   * **Android**

      * ログ記録の改善

## 2020年5月5日（PT）


* **PlacesMonitor 2.1.3**

   * **iOS**

      * ログ記録の改善

## 2020年2月20日（PT）

* **ACPPlaces 1.3.1 （iOS）**

   * Places拡張機能が、コア SDKのイベントハブにバージョン情報をレポートするようになりました。
   * デバイス POI メンバーシップ情報には、収集された時点から1時間のデフォルトの有効期間が設定されるようになりました。 詳しくは、[Places メンバーシップの有効期間の変更](places-ext-aep-sdks/places-extension/places-extension.md#places-ttl)を参照してください


* **Places 1.4.1 （Android）**

   * Places拡張機能が、コア SDKのイベントハブにバージョン情報をレポートするようになりました。
   * デバイス POI メンバーシップ情報には、収集された時点から1時間のデフォルトの有効期間が設定されるようになりました。 詳しくは、[Places メンバーシップの有効期間の変更](places-ext-aep-sdks/places-extension/places-extension.md#places-ttl)を参照してください

## 2020年1月27日（PT）

* **PlacesMonitor 2.2.0**

   * **Android**

      * 新しいPlaces APIを呼び出して、アプリの起動時や、アプリの実行中に認証が変更された際に、位置情報の認証ステータスを収集します。
      * setRequestLocationPermission APIと非推奨のsetLocationPermission APIを追加しました。

## 2020 年 1 月 10 日

* **場所1.4.0**

   * **Android**

      * Places サービスのデバイス認証ステータスを設定するための新しいAPI `setAuthorizationStatus`を追加しました。 値は保存され、Places共有状態で使用されます。

## 2019年12月4日（PT）

* **PlacesMonitor 2.1.2**

   * **iOS**

      * Places APIを呼び出して、デバイスが変更されたときにCLAuthorizationStatusを収集します。

## 2019年12月3日（PT）

* **ACPlaces 1.3.0**

   * **iOS**

      * Places サービスのデバイス認証ステータスを設定するための新しいAPI `setAuthorizationStatus`を追加しました。 値は保存され、Places共有状態で使用されます。

## 2019年11月25日（PT）

* **PlacesMonitor 2.1.1**

   * **iOS**

      * 複数のポッドプロジェクトオプションを使用したCocoapods プロジェクトの固定読み込みステートメント。

## 2019年11月22日（PT）

* **PlacesMonitor 2.1.1**

   * **Android**

      * モニターは、Android デバイスのブートを認識し、必要に応じて、デバイスの現在位置に基づいてOSにジオフェンスを再度登録します。
      * 入退出イベントが破棄されることがあるレース条件を修正しました。

## 2019年10月9日（PT）

* **PlacesMonitor 2.1.0**

   * **iOS**

      * ユーザーに対するプロンプトが表示される場所の承認要求のタイプを設定するために、新しいAPI `setRequestAuthorizationLevel`を追加しました。


   * **Android**

      * ユーザーが求める場所の権限リクエストのタイプを設定するために、新しいAPI `setLocationPermission`を追加しました。
      * Places MonitorでAndroid 10がサポートされるようになりました。

## 2019 年 8 月 8 日（PT）

このリリースでは、次の更新が行われました。

### UI アップデート

Places UIに対する更新のリストを次に示します。

#### 新機能

* マップのないPOIを表示する新しいリストビューを追加しました。
* 都市、状態、国、メタデータのPOI フィルタリングオプションを追加しました。
* 組織内の最初のライブラリが自動的に作成されます。
* リスト表示にPOI ソート機能を追加しました。

#### UI アップデート

* リストと詳細パネルをUIの右側に移動しました。
* UIの上部に新しい検索パネルを追加しました。
* ライブラリが1つしかない場合、POIを作成するときに、このライブラリが自動的に選択されます。
* ライブラリ管理をポップアップウィンドウに移動しました。
* フィルターの横にPOI カウントを追加しました。

## 2019 年 8 月 6 日（PT）

このリリースでは、次の更新が行われました。

### Monitor Launch Extension 2.0.0

* Places Monitor 2.0のAndroidおよびiOSのインストール手順を更新しました。

## 2019年7月31日（PT）

このリリースでは、次の更新が行われました。

### Places Monitor 2.0.0

* 監視ステータスが起動間で保持されるようになりました。
* 場所の権限リクエストに起因するコールバックの処理で、PlacesActivityを拡張する必要がなくなりました。
* 既存のAPIを変更し、開発者がデバイスからすべてのPlaces データを消去できるようにしました。

  古いAPI: `public static void stop();`

  新しいAPI: `public static void stop (final boolean clearData);`

* エラーシナリオをより効果的に処理するために、`getNearbyPointsOfInterest` APIの使用を更新しました。

## 2019年7月25日（PT）

このリリースでは、次の更新が行われました。

### ACPPlacesMonitor 2.0.0

* デバイスからすべてのPlaces データを消去するには、次の手順を実行します。

  acplacesMonitorで、既存のAPI `+ (void) stop;`を`+ (void) stop: (BOOL) clearData;`に置き換えました。

* エラーシナリオをより効果的に処理するために、ACPPlaces `getNearbyPointsOfInterest` APIの使用を更新しました。

## 2019年7月22日（PT）

このリリースでは、次の更新が行われました。

### Android Places 1.3.0

* 共有状態、アプリ内メモリ、および共有設定からすべてのPlaces関連データを消去する新しいAPIを追加しました。
* アプリケーションの起動中に共有状態が更新されない問題を修正しました。
* `getNearbyPointsOfInterest` コールバックがインターネットなしのエラーコード `SERVER_RESPONSE_ERROR instead of CONNECTIVITY_ERROR`を返していたバグを修正しました。
* `getNearbyPointsOfInterest` API （errorCallbackを使用しない）は、近くのポイントの取得でエラーが発生した場合、空のpoi リストで`successCallback`が呼び出されます。

## 2019年7月19日（PT）

このリリースでは、次の更新が行われました。

**iOS Places 1.2.0**

共有状態、アプリ内メモリ、および`NSUserDefaults`からすべてのPlaces関連データを消去する新しいAPIを追加しました。

## 2019年6月25日（PT）

このリリースでは、次の更新が行われました。

**iOS Places Monitor 1.0.2**

* コード内ドキュメントとログ記録の改善など、生活の質の向上。

## 2019年6月17日（PT）

このリリースでは、次の更新が行われました。

**iOS Places 1.1.0**

* 近くの場所の取得に失敗した場合にエラーコードを返す新しいAPIを追加しました。
* プライバシーステータスがオプトアウトに変更されると、Places関連のすべてのデータがデバイスから消去されるようになりました。
* 最初の起動後に、ネットワークの状態が悪いため、Places イベントが失われることがある問題を修正しました。
* POI エントリイベントを迅速に処理する際に、ルールエンジンを介したトークンの置換で誤ったPOIが参照される場合がある問題を修正しました。

## 2019 年 5 月 31 日

**Android Places Monitor 1.0.1**

* Places モニタリングの開始時にPOIのエントリイベントが発生しない問題を修正しました。

## 2019 年 5 月 28 日

場所UIの次の問題を修正しました。

* Placesのソリューションスイッチャーを更新して、Experience Cloudの他の部分に合わせました。
* ランクの変更が行われなかったインスタンスでランクが保存されていた問題を修正しました。
* UIの最小半径を10 メートルに変更しました。
* フィールド内のすべての数値を削除すると、半径フィールドが20 メートルにリセットされる問題を修正しました。

## 2019年5月17日（PT）

このリリースでは、次の更新が行われました。

**Android Places 1.2.0**

* 個々のジオフェンスを処理するための新しいAPIを追加しました。
* 複数の連続したエントリイベントを防ぐバグ修正。

**Android Places Monitor 1.0.0**

Places Monitor for Androidの初期リリース。

Places Monitorは、OS レベルのLocation APIを管理し、Places拡張機能と直接通信します。 両方の拡張機能がインストールされている場合、お客様はアプリケーションで領域を監視できます。
場所モニターの詳細については、ここをクリックしてください。


## 2019年5月2日（PT）

**Android Places 1.1.0**

* getNearByPlacesの新しいAPIを導入しました。このAPIにはerrorCallbackがあり、エラーの理由を示すerrorCodeで呼び出されます。
* Places拡張機能は、設定が取得されるまでイベントをキューに入れるようになりました。
* 環境対応設定のサポートを追加しました。
* バグ修正：地域のエントリ/終了イベントのキーを修正しました
* 最後の既知の場所を保存すると、ユーザーのプライバシーステータスが適切に尊重されるようになりました


## 2019年4月9日（PT）

このリリースでは、次の更新が行われました。

**iOS Places Monitor 1.0.1**

* フルユニットテストのカバレッジを追加しました。
* CI統合（CircleCI）
* コードカバレッジ統合（codecov）

## 2019年3月25日（PT）

iOS Places Monitor 1.0.0

Places Monitor for iOSの初期リリース。

Places Monitorは、OS レベルのLocation APIを管理し、Places拡張機能と直接通信します。 両方の拡張機能がインストールされている場合、お客様はアプリケーションで領域を監視できます。

## 2019 年 3 月 1 日

### Beta リリース

これは、Places サービスの最初のリリースであり、顧客が実際の位置情報を使用してユーザー体験を充実させることを可能にする一連のツールです。 最初のリリースの主なユースケースは、モバイルアプリがAdobe Experience Platform Launchを通じてカスタム位置データを取得し、そのデータに基づいてアクションを実行できるようにすることです。

### 主な特長

このリリースの主な機能は次のとおりです。

#### Places サービス UI

POI （Point Of Interest）を表示および管理できる管理UIをリリースしました。 POIをライブラリに整理することもできます。 都市、州、カテゴリーなどの標準メタデータに加えて、カスタムメタデータをPOIに追加する機能もサポートしています。

* UIを表示するには、[https://places.adobe.com](https://places.adobe.com)に移動します。
* UIの使用を開始するには、[はじめに](/help/getting-started.md)を参照してください。

#### Places拡張機能

Places拡張機能を使用すると、Places サービスライブラリをモバイルアプリに追加し、POIに基づいてアクションを実行できます。 Adobe Experience Platform Launchのルールビルダーを使用すると、トリガーアクションを実行して、利用者がPOIに出入りしたときに実行できます。

Places拡張機能で、次の操作を行います。

* アプリに含めるPOI ライブラリを選択できます。
* POIの出入りにトリガーするルールイベント。
* ユーザーの現在のPOIを指すデータ要素を作成します。

Places拡張機能について詳しくは、[Places拡張機能](/help/places-ext-aep-sdks/places-extension/places-extension.md)を参照してください。

#### Places API

Places APIを使用して、次の操作を行うことができます。

* 開発者がPOIのリストを入力し、更新できるようにします。
* 独自のUIを構築するか、既存のPOI データベースと統合できます。
* Places API バッチエンドポイントを使用して、POIを一括インポートします。

  提供されているPython ユーティリティを使用して、一括読み込みを完了できます。

Places APIについて詳しくは、[Web サービス API](/help/web-service-api/places-web-services.md)を参照してください。

### まもなくリリース

#### Analytics の統合

Analytics拡張機能が更新され、ユーザーがPOI （パッシブ呼び出し）に入ったときに、Places サービス データベースから送信されるすべてのAnalytics呼び出しに位置情報データが自動的に追加されます。 また、このアップデートにより、ルール作成でAnalyticsのトラック呼び出しをPOIのエントリまたは終了時（アクティブな呼び出し）に直接実行できるようになりました。
