---
title: リリースノート
description: Places Service のリリースノートです。
exl-id: 76da9548-4e32-4b23-9a15-7012973915f3
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '1490'
ht-degree: 2%

---

# リリースノート {#release-notes}

## 2020 年 7 月 9 日

* **Places and Places Monitor の拡張機能**

   * Places と Places 監視の拡張機能がに追加されました。 [React ネイティブアプリケーション](https://aep-sdks.gitbook.io/docs/resources/upgrading-to-aep/current-sdk-versions#react-native)
   * Places と Places 監視の拡張機能がに追加されました。 [Cordova アプリケーション](https://aep-sdks.gitbook.io/docs/resources/upgrading-to-aep/current-sdk-versions#cordova)
   * 詳しくは、以下を参照してください。 [Places 拡張機能の使用](https://experienceleague.adobe.com/docs/places/using/places-ext-aep-sdks/places-extension/places-extension.html)


## 2020 年 5 月 13 日

* **Places Service**

   * 「POI をインポート」ボタンを使用して CSV ファイルから POI を一括インポート
   * 複数の POI を選択して一括編集またはメタデータ値の追加

## 2020 年 5 月 7 日

* **PlacesMonitor 2.2.1**

   * **Android**

      * ログの改善

## 2020 年 5 月 6 日


* **PlacesMonitor 2.1.3**

   * **iOS**

      * ログの改善

## 2020年2月20日

* **ACPPlaces 1.3.1(iOS)**

   * Places 拡張機能で、コア SDK のイベントハブにバージョン情報がレポートされるようになりました。
   * デバイス POI メンバーシップ情報の、収集時から 1 時間のデフォルトの有効期間が設定されるようになりました。 詳しくは、 [Places メンバーシップの有効期間の変更](places-ext-aep-sdks/places-extension/places-extension.md#places-ttl)


* **Places 1.4.1(Android)**

   * Places 拡張機能で、コア SDK のイベントハブにバージョン情報がレポートされるようになりました。
   * デバイス POI メンバーシップ情報の、収集時から 1 時間のデフォルトの有効期間が設定されるようになりました。 詳しくは、 [Places メンバーシップの有効期間の変更](places-ext-aep-sdks/places-extension/places-extension.md#places-ttl)

## 2020 年 1 月 27 日（PT）

* **PlacesMonitor 2.2.0**

   * **Android**

      * 新しい Places API を呼び出して、アプリの起動時と、アプリの実行中に認証が変更された場合の場所の認証ステータスを収集します。
      * setRequestLocationPermission API と廃止された setLocationPermission API が追加されました。

## 2020 年 1 月 10 日

* **Places 1.4.0**

   * **Android**

      * 新しい API、 `setAuthorizationStatus`、Places Services のデバイス認証ステータスを設定します。 この値は保存され、Places 共有状態で使用されます。

## 2019 年 12 月 5 日

* **PlacesMonitor 2.1.2**

   * **iOS**

      * Places API を呼び出して、変更時にデバイスから CLAuthorizationStatus を収集します。

## 2019 年 12 月 4 日

* **ACPPlaces 1.3.0**

   * **iOS**

      * 新しい API、 `setAuthorizationStatus`、Places Services のデバイス認証ステータスを設定します。 この値は保存され、Places 共有状態で使用されます。

## 2019 年 11 月 26 日

* **PlacesMonitor 2.1.1**

   * **iOS**

      * 複数のポッドプロジェクトオプションを使用する Cocoapods プロジェクトのインポート文を修正しました。

## 2019年11月22日

* **PlacesMonitor 2.1.1**

   * **Android**

      * モニターは、Android デバイスの起動を認識し、必要に応じて、デバイスの現在の場所に基づいてジオフェンスを OS に再登録するようになりました。
      * エントリ/終了イベントが破棄されることがある競合状態を修正しました。

## 2019年9月10日（PT）

* **PlacesMonitor 2.1.0**

   * **iOS**

      * 新しい API、 `setRequestAuthorizationLevel`：ユーザーに対して要求される場所の認証要求のタイプを設定します。


   * **Android**

      * 新しい API、 `setLocationPermission`：ユーザーに表示される場所権限リクエストのタイプを設定します。
      * Places モニターで Android 10 がサポートされるようになりました。

## 2019 年 8 月 9 日

このリリースでは、次の更新がおこなわれました。

### UI の更新

Places UI の更新の一覧を次に示します。

#### 新機能

* マップを使用せずに POI を表示する新しいリスト表示を追加しました。
* 市区町村、都道府県、国およびメタデータに対する POI フィルタリングオプションを追加しました。
* 組織の最初のライブラリが自動的に作成されます。
* リスト表示に POI の並べ替えを追加しました。

#### UI の更新

* リストと詳細パネルを UI の右側に移動しました。
* UI の上部に新しい検索パネルが追加されました。
* ライブラリが 1 つだけ存在する場合、POI の作成時にこのライブラリが自動的に選択されます。
* ライブラリ管理をポップアップウィンドウに移動しました。
* フィルターの横に POI カウントを追加しました。

## 2019 年 6 月 9 日

このリリースでは、次の更新がおこなわれました。

### Launch 拡張機能 2.0.0 の監視

* Places モニター 2.0 の Android およびiOSのインストール手順を更新しました。

## 2019年7月31日（PT）

このリリースでは、次の更新がおこなわれました。

### Places 監視 2.0.0

* 監視ステータスが起動間で保持されるようになりました。
* 場所権限のリクエストによって生成されたコールバックの処理では、PlacesActivity を拡張する必要がなくなりました。
* 既存の API が変更され、デベロッパーは、デバイスからすべての Places データをクリアできるようになりました。

  古い API: `public static void stop();`

  新しい API: `public static void stop (final boolean clearData);`

* の使用を更新しました。 `getNearbyPointsOfInterest` エラーシナリオをより効果的に処理する API。

## 2019年7月25日（PT）

このリリースでは、次の更新がおこなわれました。

### ACPPlacesMonitor 2.0.0

* デバイスからすべての Places データをクリアするには、次の手順を実行します。

  ACPPlacesMonitor で、既存の API を置き換える `+ (void) stop;` 次を使用`+ (void) stop: (BOOL) clearData;`.

* ACPPlaces の使用を更新しました。 `getNearbyPointsOfInterest` エラーシナリオをより効果的に処理する API。

## 2019年7月22日

このリリースでは、次の更新がおこなわれました。

### Android Places 1.3.0

* 共有状態、アプリ内メモリ、共有環境設定からすべての Places 関連データを消去する新しい API が追加されました。
* アプリケーションの起動中に共有状態が更新されない問題を修正しました。
* の問題を修正しました。 `getNearbyPointsOfInterest` コールバックがエラーコードを返していました `SERVER_RESPONSE_ERROR instead of CONNECTIVITY_ERROR` インターネットに接続されていません。
* `getNearbyPointsOfInterest` API（errorCallback を除く）は、 `successCallback` 近くの目標地点を取得中にエラーが発生した場合に、空の poi リストで呼び出されます。

## 2019年7月19日（PT）

このリリースでは、次の更新がおこなわれました。

**iOS Places 1.2.0**

共有状態、アプリ内メモリ、および `NSUserDefaults`.

## 2019 年 6 月 26 日

このリリースでは、次の更新がおこなわれました。

**iOS Places Monitor 1.0.2**

* コード内ドキュメントやログの改善など、QOL の改善がおこなわれました。

## 2019 年 6 月 18 日

このリリースでは、次の更新がおこなわれました。

**iOS Places 1.1.0**

* 近くの場所の取得中にエラーが発生した場合にエラーコードを返す新しい API が追加されました。
* プライバシーステータスがオプトアウトに変わると、Places 関連のすべてのデータがデバイスから消去されるようになりました。
* 初回起動後、ネットワーク状態が悪いために Places イベントが失われることがある問題を修正しました。
* POI エントリイベントをすばやく連続して処理する際に、ルールエンジンを介したトークン置換が誤った POI を参照することがある問題を修正しました。

## 2019年5月31日

**Android Places Monitor 1.0.1**

* Places 監視が開始されたときに POI のエントリイベントが発生しない問題を修正しました。

## 2019 年 5 月 28 日

Places UI での次の問題を修正しました。

* Places のソリューション切り替えボタンが更新され、残りのExperience Cloudと連携するようになりました。
* ランクが変更されない場合にランクが保存される問題を修正しました。
* UI で許容される最小半径を 10 m に増やしました。
* フィールド内のすべての数値を削除すると、半径フィールドが 20 m にリセットされる問題を修正しました。

## 2019 年 5 月 18 日

このリリースでは、次の更新がおこなわれました。

**Android Places 1.2.0**

* 個々のジオフェンスを処理する新しい API が追加されました。
* 複数の連続したエントリイベントが発生しないバグを修正しました。

**Android Places Monitor 1.0.0**

Android 向け Places モニターの初期リリースです。

Places モニターは、OS レベルのロケーション API を管理し、Places 拡張機能と直接通信します。 両方の拡張機能がインストールされている場合、お客様は、アプリケーションで標準の地域監視を使用できます。
Places モニタの詳細については、ここをクリックしてください。


## 2019 年 5 月 3 日

**Android Places 1.1.0**

* getNearByPlaces の新しい API が導入されました。この API は errorCallback を持ち、エラーの理由を示す errorCode と共に呼び出されます。
* Places 拡張機能は、設定が取得されるまでイベントをキューに追加するようになりました。
* 環境対応設定のサポートを追加しました。
* バグ修正：地域の入口/出口イベントのキーを修正しました。
* 最新の既知の場所のストレージが、ユーザーのプライバシーステータスを適切に順守するようになりました。


## 2019年4月9日（PT）

このリリースでは、次の更新がおこなわれました。

**iOS Places Monitor 1.0.1**

* 単体テストの対象を完全に追加しました。
* CI 統合 (CircleCI)
* コードカバレッジの統合 (codecov)

## 2019 年 3 月 26 日

iOS Places Monitor 1.0.0

iOSの Places 監視の初期リリースです。

Places モニターは、OS レベルのロケーション API を管理し、Places 拡張機能と直接通信します。 両方の拡張機能がインストールされている場合、お客様は、アプリケーションで標準の地域監視を使用できます。

## 2019 年 3 月 1 日

### ベータリリース

これは、顧客が実際の場所のデータを使用してユーザーエクスペリエンスを強化できる一連のツールである、Places Service の最初のリリースです。 最初のリリースでは、モバイルアプリがカスタムの場所データを取得し、Adobe Experience Platform Launchを通じてそのデータに基づいて動作できるようにすることが主な使用例です。

### 主な特長

このリリースの主な機能を次に示します。

#### Places Service UI

目標地点 (POI) を表示および管理できる管理 UI がリリースされました。 POI をライブラリに整理することもできます。 アドビでは、市区町村、都道府県、カテゴリなどの標準メタデータに加えて、POI にカスタムメタデータを追加する機能もサポートしています。

* UI を確認するには、に移動します。 [https://places.adobe.com](https://places.adobe.com).
* UI の使用を開始するには、 [はじめに](/help/getting-started.md).

#### Places 拡張機能

Places 拡張機能を使用すると、Places サービスライブラリをモバイルアプリに追加し、POI に基づいて操作できます。 Experience Platform Launchのルールビルダーを使用すると、トリガーのアクションを実行して、ユーザーが POI を入って出るときに実行できます。

Places 拡張機能で、以下の操作をおこないます。

* アプリに含める POI ライブラリを選択できます。
* POI の入口または出口でトリガーするルールイベント。
* ユーザーの現在の POI を指すデータ要素を作成します。

Places 拡張機能について詳しくは、 [Places 拡張機能](/help/places-ext-aep-sdks/places-extension/places-extension.md).

#### Places API

Places API を使用して、次の操作を実行できます。

* 開発者が POI のリストを入力および更新できるようにします。
* 独自の UI を作成するか、既存の POI データベースと統合します。
* Places API バッチエンドポイントを使用して、POI を一括読み込みます。

  付属の Python ユーティリティを使用して一括インポートを完了できます。

Places API について詳しくは、 [Web サービス API](/help/web-service-api/places-web-services.md).

### 近日開始

#### Analytics の統合

Analytics 拡張機能は、ユーザーが POI（パッシブ呼び出し）に入っているときに、Places Service データベースの場所コンテキストデータを、送信されるすべての Analytics 呼び出しに自動的に追加するように更新されています。 また、この更新により、ルールの作成時に、POI 入口または出口（アクティブな呼び出し）で Analytics の追跡呼び出しを直接実行できるようになります。
