---
title: リリースノート
description: Places Service のリリースノート。
exl-id: 76da9548-4e32-4b23-9a15-7012973915f3
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '1525'
ht-degree: 2%

---

# リリースノート {#release-notes}

## 2020 年 7 月 9 日

* **Places and Places Monitor 拡張機能**

   * Places and Places Monitor 拡張機能が [React Native アプリケーションに追加されました &#x200B;](https://aep-sdks.gitbook.io/docs/resources/upgrading-to-aep/current-sdk-versions#react-native)
   * [Cordova アプリケーション &#x200B;](https://aep-sdks.gitbook.io/docs/resources/upgrading-to-aep/current-sdk-versions#cordova) 用の場所および場所モニター拡張機能が追加されました
   * 詳しくは、[Places 拡張機能の使用 &#x200B;](https://experienceleague.adobe.com/docs/places/using/places-ext-aep-sdks/places-extension/places-extension.html) を参照してください。


## 2020 年 5 月 12 日（Pt）

* **Places Service**

   * 「POI を読み込み」ボタンを使用して、CSV ファイルから POI を一括読み込みする
   * 複数の POI を選択し、メタデータ値を一括編集または追加する

## 2020 年 5 月 6 日（Pt）

* **PlacesMonitor 2.2.1**

   * **Android**

      * ログの改善

## 2020 年 5 月 5 日（Pt）


* **PlacesMonitor 2.1.3**

   * **iOS**

      * ログの改善

## 2020 年 2 月 20 日（Pt）

* **ACPPlaces 1.3.1 （iOS）**

   * Places 拡張機能で、Core SDK のイベントハブにバージョン情報がレポートされるようになりました。
   * デバイス POI メンバーシップ情報のデフォルトの有効期間は、収集時から 1 時間になりました。 詳細は、「[Modifying Places membership time to-live](places-ext-aep-sdks/places-extension/places-extension.md#places-ttl)」を参照してください


* **場所 1.4.1 （Android）**

   * Places 拡張機能で、Core SDK のイベントハブにバージョン情報がレポートされるようになりました。
   * デバイス POI メンバーシップ情報のデフォルトの有効期間は、収集時から 1 時間になりました。 詳細は、「[Modifying Places membership time to-live](places-ext-aep-sdks/places-extension/places-extension.md#places-ttl)」を参照してください

## 2020 年 1 月 27 日（Pt）

* **PlacesMonitor 2.2.0**

   * **Android**

      * 新しい Places API を呼び出して、アプリの起動時と、アプリの実行中に認証が変更された際の場所の認証ステータスを収集します。
      * setRequestLocationPermission API と非推奨の setLocationPermission API を追加しました。

## 2020 年 1 月 10 日

* **場所 1.4.0**

   * **Android**

      * 場所サービスのデバイス認証ステータスを設定する新しい API、`setAuthorizationStatus` を追加しました。 値が保存され、「場所」共有状態で使用されます。

## 2019 年 12 月 4 日（Pt）

* **PlacesMonitor 2.1.2**

   * **iOS**

      * Places API を呼び出して、変更時にデバイスから CLAuthorizationStatus を収集します。

## 2019 年 12 月 3 日（Pt）

* **ACPPlaces 1.3.0**

   * **iOS**

      * 場所サービスのデバイス認証ステータスを設定する新しい API、`setAuthorizationStatus` を追加しました。 値が保存され、「場所」共有状態で使用されます。

## 2019 年 11 月 26 日

* **PlacesMonitor 2.1.1**

   * **iOS**

      * 複数ポッドプロジェクトオプションを使用した Cocoapods プロジェクトのインポート文を修正しました。

## 2019年11月22日（PT）

* **PlacesMonitor 2.1.1**

   * **Android**

      * これで、モニタがAndroid デバイスのブートを認識し、必要に応じて、デバイスの現在の場所に基づいて OS に再度ジオフェンスを登録します。
      * Entry/Exit イベントが破棄されることがある競合状態を修正しました。

## 2019 年 10 月 9 日（Pt）

* **PlacesMonitor 2.1.0**

   * **iOS**

      * ユーザーにプロンプトが表示される場所の認証リクエストのタイプを設定する新しい API、`setRequestAuthorizationLevel` を追加しました。


   * **Android**

      * ユーザーにプロンプトを表示する場所の権限リクエストのタイプを設定する新しい API、`setLocationPermission` を追加しました。
      * Places Monitor でAndroid 10 がサポートされるようになりました。

## 2019 年 8 月 8 日（PT）

このリリースでは、次の更新が行われました。

### UI アップデート

以下に、場所 UI の更新のリストを示します。

#### 新機能

* マップのない POI を表示する新しいリスト表示を追加しました。
* 市区町村、州、国、メタデータに POI フィルタリングオプションを追加しました。
* 組織の最初のライブラリが自動的に作成されます。
* リスト表示に POI ソートを追加しました。

#### UI アップデート

* リストと詳細パネルを UI の右側に移動しました。
* UI の上部に新しい検索パネルを追加しました。
* ライブラリが 1 つしか存在しない場合、POI を作成すると、このライブラリが自動的に選択されます。
* ライブラリ管理がポップアップウィンドウに移動されました。
* フィルターの横に POI 数を追加しました。

## 2019 年 8 月 6 日（PT）

このリリースでは、次の更新が行われました。

### Launch 拡張機能 2.0.0 の監視

* Places Monitor 2.0 のAndroidとiOSのインストール手順を更新しました。

## 2019年7月31日（PT）

このリリースでは、次の更新が行われました。

### Places Monitor 2.0.0

* 監視ステータスがローンチ間で保持されるようになりました。
* 場所の権限リクエストによるコールバックの処理で、PlacesActivity を拡張する必要がなくなりました。
* 既存の API が変更され、開発者がデバイスからすべての場所データをクリアできるようになりました。

  古い API: `public static void stop();`

  新しい API: `public static void stop (final boolean clearData);`

* エラーシナリオをより効果的に処理するために、`getNearbyPointsOfInterest` API の使用を更新しました。

## 2019年7月25日（PT）

このリリースでは、次の更新が行われました。

### ACPPlacesMonitor 2.0.0

* デバイスからすべての Places データを消去するには、

  acpclacesmonitor で、既存の API `+ (void) stop;` を `+ (void) stop: (BOOL) clearData;` に置き換えました。

* エラーシナリオをより効果的に処理するために、ACPPlaces `getNearbyPointsOfInterest` API の使用を更新しました。

## 2019 年 7 月 22 日（Pt）

このリリースでは、次の更新が行われました。

### Android Places 1.3.0

* 共有状態、アプリ内メモリ、共有環境設定からすべての場所関連データをクリアする新しい API が追加されました。
* アプリケーションの開始時に共有状態が更新されない問題を修正しました。
* コールバックがインターネット上 `getNearbyPointsOfInterest` エラーコード `SERVER_RESPONSE_ERROR instead of CONNECTIVITY_ERROR` を返していたバグを修正しました。
* （errorCallback を除く） `getNearbyPointsOfInterest`API は、近くの目標地点の取得でエラーが発生した場合、空の poi リストで `successCallback` を呼び出します。

## 2019 年 7 月 19 日（Pt）

このリリースでは、次の更新が行われました。

**iOS Places 1.2.0**

共有状態、アプリ内メモリおよび `NSUserDefaults` から場所に関連するすべてのデータをクリアする新しい API が追加されました。

## 2019 年 6 月 25 日（Pt）

このリリースでは、次の更新が行われました。

**iOS Places Monitor 1.0.2**

* コード内ドキュメントとログの改善を含む、QOL の向上。

## 2019 年 6 月 17 日（Pt）

このリリースでは、次の更新が行われました。

**iOSの場所 1.1.0**

* 近くの場所の取得に失敗した場合にエラーコードを返す新しい API を追加しました。
* プライバシーステータスがオプトアウトに変更された場合、すべての Places 関連のデータがデバイスから消去されるようになりました。
* 最初の起動後、ネットワークの状態が悪いために Places イベントが失われることがある問題を修正しました。
* POI エントリイベントを迅速に順次処理する際に、ルールエンジンを介したトークン置換で誤った POI が参照されることがある問題を修正しました。

## 2019 年 5 月 30 日（Pt）

**Android Places Monitor 1.0.1**

* 場所の監視が開始されたときに POI のエントリイベントが発生しない問題を修正しました。

## 2019 年 5 月 28 日（Pt）

場所 UI の次の問題を修正しました。

* 場所のソリューション切り替えボタンを更新して、Experience Cloudの残りの部分と整合させます。
* ランクが変更されなかったインスタンスでランクが保存される問題を修正しました。
* UI で許可される最小半径を 10 メートルに増やしました。
* フィールド内のすべての数値を削除すると、半径フィールドが 20 メートルにリセットされる問題を修正しました。

## 2019 年 5 月 17 日（Pt）

このリリースでは、次の更新が行われました。

**Android Places 1.2.0**

* 個々のジオフェンスを処理する新しい API を追加しました。
* 複数の連続したエントリイベントを防ぐためのバグ修正。

**Android Places Monitor 1.0.0**

Android用 Places Monitor の初回リリースです。

Places Monitor は OS レベルの Location API を管理し、Places 拡張機能と直接通信します。 両方の拡張機能がインストールされていれば、お客様はアプリケーションで標準の地域監視を行うことができます。
Places Monitor の詳細については、ここをクリックしてください。


## 2019 年 5 月 2 日（Pt）

**Androidの場所 1.1.0**

* getNearByPlaces に新しい API が導入されました。この API は errorCallback を持ち、エラーの理由を示す errorCode を使用して呼び出されます。
* Places 拡張機能は、設定が取得されるまでイベントをキューに入れるようになりました。
* 環境対応設定のサポートを追加しました。
* バグ修正：地域入口/出口イベントのキーを修正しました
* 最後の既知の場所のストレージは、ユーザーのプライバシーステータスに従うようになりました


## 2019年4月9日（PT）

このリリースでは、次の更新が行われました。

**iOS Places Monitor 1.0.1**

* 完全な単体テストカバレッジを追加しました。
* CI 統合（CircleCI）
* コードカバレッジ統合（codecov）

## 2019 年 3 月 25 日（Pt）

iOS Places Monitor 1.0.0

iOS用 Places Monitor の初回リリースです。

Places Monitor は OS レベルの Location API を管理し、Places 拡張機能と直接通信します。 両方の拡張機能がインストールされていれば、お客様はアプリケーションで標準の地域監視を行うことができます。

## 2019 年 3 月 1 日

### Beta リリース

これは、ユーザーが実際の場所のデータを使用してユーザーのエクスペリエンスを強化できるツールセットである Places Service の最初のリリースです。 最初のリリースの主なユースケースは、モバイルアプリがカスタムの場所データを取得し、Adobe Experience Platform Launchを通じてそのデータに基づいて動作できるようにすることです。

### 主な特長

このリリースの主な機能は次のとおりです。

#### Places Service UI

目標地点（POI）を表示および管理できる管理 UI がリリースされました。 また、POI をライブラリに整理することもできます。 市区町村、状態、カテゴリなどの標準のメタデータに加えて、POI にカスタムメタデータを追加する機能もサポートしています。

* UI を表示するには、[https://places.adobe.com](https://places.adobe.com) に移動します。
* UI を使い始めるには、[&#x200B; はじめに &#x200B;](/help/getting-started.md) を参照してください。

#### Places 拡張機能

Places 拡張機能を使用すると、Places サービスライブラリをモバイルアプリに追加し、その POI に基づいて行動できます。 Experience Platform Launchのルールビルダーを使用すると、ユーザーが POI に入って出たときに実行されるトリガーアクションを設定できます。

Places 拡張機能で次の操作を行います。

* アプリに含める POI ライブラリを選択できます。
* POI のエントリまたは終了時にトリガーとなるルールイベント。
* ユーザーの現在の POI を指すデータ要素を作成します。

Places 拡張機能について詳しくは、[Places 拡張機能 &#x200B;](/help/places-ext-aep-sdks/places-extension/places-extension.md) を参照してください。

#### Places API

Places API を使用して、次の操作を実行できます。

* 開発者が POI のリストにデータを入力し、更新できるようにします。
* 独自の UI を作成するか、既存の POI データベースと統合します。
* POI の一括読み込みを行うには、Places API バッチエンドポイントを使用します。

  提供された Python ユーティリティを使用して、一括読み込みを完了できます。

Places API について詳しくは、「[Web サービス API](/help/web-service-api/places-web-services.md)」を参照してください。

### まもなくリリース

#### Analytics の統合

Analytics 拡張機能は、ユーザーが POI （パッシブ呼び出し）にいる場合に、Places Service データベースから送信されるすべての Analytics 呼び出しに場所コンテキストデータを自動的に追加するように更新されています。 このアップデートにより、ルールを作成して、POI の入口または出口（アクティブな呼び出し）で直接 Analytics トラッキングコールを実行することもできます。
