---
title: リリースノート
description: Places Serviceのリリースノートです。
translation-type: tm+mt
source-git-commit: 3f986697179eb9c0af1d9b54daf67793a99b8491
workflow-type: tm+mt
source-wordcount: '1503'
ht-degree: 3%

---


# リリースノート {#release-notes}

## 2020 年 7 月 9 日

* **場所と場所のモニター拡張**

   * Places and Places Monitor拡張が追加され、 [React Nativeアプリケーションに対応](https://aep-sdks.gitbook.io/docs/resources/upgrading-to-aep/current-sdk-versions#react-native)
   * Cordovaアプリケーション用に、場所と場所のモニターの拡張機能が追加され [ました。](https://aep-sdks.gitbook.io/docs/resources/upgrading-to-aep/current-sdk-versions#cordova)
   * 詳しくは、次を参照してください。 [Places拡張子の使用](https://docs.adobe.com/content/help/en/places/using/places-ext-aep-sdks/places-extension/places-extension.html)


## 2020年5月12日

* **Places Service**

   * 「POIを読み込み」ボタンを使用して、CSVファイルからPOIを一括読み込み
   * 複数のPOIを選択し、メタデータ値をバルク編集または追加する

## 2020 年 5 月 6 日

* **PlacesMonitor 2.2.1**

   * **Android**

      * ログ機能の向上

## 2020年5月5日


* **PlacesMonitor 2.1.3**

   * **iOS**

      * ログ機能の向上

## 2020 年 2 月 21 日

* **ACPPlaces 1.3.1(iOS)**

   * Places extensionは、コアSDKのイベントハブにバージョン情報をレポートするようになりました。
   * デバイスのPOIメンバーシップ情報のデフォルトの有効期間は、収集された時点から1時間になります。 詳しくは、「Placesメンバーシップの有効期間の [変更」を参照してください。](places-ext-aep-sdks/places-extension/places-extension.md#places-ttl)


* **Places 1.4.1(Android)**

   * Places extensionは、コアSDKのイベントハブにバージョン情報をレポートするようになりました。
   * デバイスのPOIメンバーシップ情報のデフォルトの有効期間は、収集された時点から1時間になります。 詳しくは、「Placesメンバーシップの有効期間の [変更」を参照してください。](places-ext-aep-sdks/places-extension/places-extension.md#places-ttl)

## 2020 年 1 月 27 日

* **PlacesMonitor 2.2.0**

   * **Android**

      * 新しい場所APIを呼び出して、アプリの起動時およびアプリの実行中に認証が変更された場合の位置の認証ステータスを収集します。
      * setRequestLocationPermission APIと非推奨のsetLocationPermission APIが追加されました。

## 2020 年 1 月 10 日

* **場所1.4.0**

   * **Android**

      * Places Servicesのデバイス認証状態を設定する新しいAPI `setAuthorizationStatus`が追加されました。 この値は保存され、Places共有状態で使用されます。

## 2019年12月5日

* **PlacesMonitor 2.1.2**

   * **iOS**

      * Places APIを呼び出して、デバイスが変更された場合にCLAuthorizationStatusをデバイスから収集します。

## 2019年12月4日

* **ACPPlaces 1.3.0**

   * **iOS**

      * Places Servicesのデバイス認証状態を設定する新しいAPI `setAuthorizationStatus`が追加されました。 この値は保存され、Places共有状態で使用されます。

## 2019 年 11 月 26 日

* **PlacesMonitor 2.1.1**

   * **iOS**

      * 複数のポッドプロジェクトオプションを使用するCocoapodsプロジェクトのインポートステートメントを修正しました。

## 2019年11月23日

* **PlacesMonitor 2.1.1**

   * **Android**

      * モニターはAndroidデバイスの起動を認識し、必要に応じて、デバイスの現在の場所に基づいてジオフェンスをOSに再登録します。
      * 入口/出口イベントが破棄されることがある競合状態を修正しました。

## 2019 年 9 月 11 日

* **PlacesMonitor 2.1.0**

   * **iOS**

      * ユーザーに要求する場所の認証要求のタイプを設定する新しいAPI `setRequestAuthorizationLevel`を追加しました。
   * **Android**

      * ユーザーに促す場所権限リクエストのタイプ `setLocationPermission`を設定する新しいAPIを追加しました。
      * プレースモニターでAndroid 10がサポートされるようになりました。



## 2019 年 8 月 9 日

このリリースでは、次の更新が行われました。

### UIの更新

以下に、場所UIの更新のリストを示します。

#### 新機能

* マップを使用せずにPOIを表示する新しいリスト表示を追加しました。
* 市区町村、州、国、メタデータにPOIフィルターオプションを追加しました。
* 組織の最初のライブラリが自動的に作成されます。
* リスト表示にPOI並べ替えを追加しました。

#### UIの更新

* リストと詳細パネルをUIの右側に移動しました。
* UIの上部に新しい検索パネルが追加されました。
* ライブラリが1つだけ存在する場合、POIの作成時に、このライブラリが自動的に選択されます。
* ライブラリ管理をポップアップウィンドウに移動しました。
* フィルターの横にPOI数が追加されました。

## 2019 年 8 月 7 日

このリリースでは、次の更新が行われました。

### Monitor Launch Extension 2.0.0

* プレースモニター2.0のAndroidおよびiOSのインストール手順を更新しました。

## 2019 年 8 月 1 日

このリリースでは、次の更新が行われました。

### プレースモニタ2.0.0

* 起動間も監視ステータスが維持されるようになりました。
* 場所の権限の要求によるコールバックの処理で、PlacesActivityを拡張する必要がなくなりました。
* 既存のAPIが変更され、開発者はデバイスからすべてのPlacesデータを消去できるようになりました。

   古いAPI: `public static void stop();`

   New API: `public static void stop (final boolean clearData);`

* APIの使用を更新し、エラーシナリオをより効率的に処理できるようにしました。 `getNearbyPointsOfInterest`

## 2019 年 7 月 25 日

このリリースでは、次の更新が行われました。

### ACPPlacesMonitor 2.0.0

* デバイスからすべての場所のデータを消去するには、

   を使用して、既存のAPIをに置き換え `+ (void) stop;` ます`+ (void) stop: (BOOL) clearData;`。

* ACPPlaces `getNearbyPointsOfInterest` APIの使用を更新し、エラーシナリオをより効率的に処理できるようにしました。

## 2019 年 7 月 22 日

このリリースでは、次の更新が行われました。

### Android Places 1.3.0

* 共有状態、アプリ内メモリ、共有環境設定からすべての場所関連データを消去する新しいAPIが追加されました。
* アプリケーションの開始中に共有状態が更新されない問題を修正しました。
* コールバックがインターネット上でエラーコードを返し `getNearbyPointsOfInterest` ていたバグ `SERVER_RESPONSE_ERROR instead of CONNECTIVITY_ERROR` を修正しました。
* `getNearbyPointsOfInterest` API （errorCallbackなし）は、近くの目標地点を取得中にエラーが発生した場合に、空のpoiリストで `successCallback` 呼び出されます。

## 2019 年 7 月 19 日

このリリースでは、次の更新が行われました。

**iOS Places 1.2.0**

共有状態、アプリ内メモリ、およびPlaces関連のすべてのデータを消去する新しいAPIが追加されました `NSUserDefaults`。

## 2019 年 6 月 26 日

このリリースでは、次の更新が行われました。

**iOS Places Monitor 1.0.2**

* 優れたインコードドキュメントやログを含む、ライフサイクルの質の向上。

## 2019 年 17 月 7 日

このリリースでは、次の更新が行われました。

**iOS Places 1.1.0**

* 近くの場所の取得でエラーが発生した場合にエラーコードを返す新しいAPIを追加しました。
* プライバシーの状態がオプトアウトに変わると、場所に関連するすべてのデータがデバイスから消去されるようになりました。
* 最初の起動後、ネットワークの状態が悪いためにPlacesイベントが失われる場合がある問題を修正しました。
* POIエントリイベントをすばやく連続して処理する場合に、ルールエンジンによるトークン置き換えが誤ったPOIを参照することがある問題を修正しました。

## 2019 年 5 月 31 日

**Android Places Monitor 1.0.1**

* 場所の監視を開始したときに、POIのエントリイベントが表示されない問題を修正しました。

## 2019 年 5 月 28 日

Places UIでの次の問題を修正しました。

* 場所のソリューション切り替えボタンが更新され、Experience Cloudの残りの部分と連携するようになりました。
* ランクが変更されない場合にランクが保存される問題を修正しました。
* UIの最小許容半径を10メートルに増やしました。
* フィールド内の数値をすべて削除すると、半径フィールドが20メートルにリセットされる問題を修正しました。

## 2019 年 5 月 17 日

このリリースでは、次の更新が行われました。

**Android Places 1.2.0**

* 個々のジオフェンスを処理する新しいAPIを追加しました。
* 複数の連続エントリイベントを回避するバグ修正。

**Android Places Monitor 1.0.0**

Android用プレースモニターの初回リリース。

プレースモニターは、OSレベルのロケーションAPIを管理し、Places拡張と直接通信します。 両方の拡張機能がインストールされている場合は、お客様はアプリケーションで標準搭載の地域を監視できます。
プレースモニターの詳細については、ここをクリックしてください。


## 2019 年 5 月 2 日

**Android Places 1.1.0**

* getNearByPlacesに新しいAPIが導入されました。このAPIは、errorCallbackを持ち、エラーの理由を示すerrorCodeで呼び出されます。
* Places拡張は、設定が取得されるまでイベントをキューに入れます。
* 環境対応設定のサポートを追加しました。
* バグ修正： 地域の入口/出口イベントのキーを修正。
* 前回の既知の場所のストレージに、ユーザーのプライバシーステータスが適切に反映されるようになりました。


## 2019 年 4 月 10 日

このリリースでは、次の更新が行われました。

**iOS Places Monitor 1.0.1**

* 単体テストの機能を完全に追加しました。
* CI統合(CircleCI)
* コードカバレッジ統合(codecov)

## 2019 年 3 月 26 日

iOS Places Monitor 1.0.0

iOS用Places Monitorの最初のリリース。

プレースモニターは、OSレベルのロケーションAPIを管理し、Places拡張と直接通信します。 両方の拡張機能がインストールされている場合は、お客様はアプリケーションで標準搭載の地域を監視できます。 プレースモニターの詳細については、「プレースモニター拡張 [機能](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md)」を参照してください。

## 2019 年 3 月 1 日

### ベータリリース

これは、顧客が実際の場所データに対してユーザーの体験を豊かにするツールのセットであるPlaces Serviceの最初のリリースです。 最初のリリースでは、主にモバイルアプリで、Adobe Experience Platformの起動を通じてカスタム位置データを取得し、そのデータに基づいて動作できるようにする使用例が挙げられます。

### 主な特長

このリリースの主な機能は次のとおりです。

#### PlacesサービスUI

目標地点(POI)の表示と管理を行える管理用UIをリリースしました。 POIをライブラリに整理することもできます。 市、州、カテゴリなどの標準メタデータに加え、POIにカスタムメタデータを追加する機能もサポートしています。

* UIを確認するには、https://places.adobe.comにアクセスし [ます](https://places.adobe.com)。
* UIの使い始めには、はじめにを参照して [ください](/help/getting-started.md)。

#### 拡張子を配置

Places Extensionを使用すると、Places Serviceライブラリをモバイルアプリに追加して、POIに基づいて動作させることができます。 Experience Platform Launchでルールビルダーを使用すると、ユーザーがPOIにアクセスしてPOIを終了したときに実行するアクションをトリガーできます。

Places拡張子で次の操作を行います。

* アプリに含めるPOIライブラリを選択できます。
* POIの入口または出口でトリガーされるルールイベント。
* ユーザーの現在のPOIを指すデータ要素を作成します。

For more information about the Places extension, see [Places extension](/help/places-ext-aep-sdks/places-extension/places-extension.md).

#### Places API

Places APIを使用して、次の操作を行うことができます。

* 開発者はPOIのリストを入力および更新できます。
* 独自のUIを構築するか、既存のPOIデータベースと統合します。
* Places APIバッチエンドポイントを使用して、POIの一括インポートを行います。

   付属のPythonユーティリティを使用して、バルクインポートを完了できます。

Places APIについて詳しくは、 [WebサービスAPIを参照してください](/help/web-service-api/places-web-services.md)。

### 準備中

#### Analytics の統合

Analytics拡張機能は、ユーザーがPOI（パッシブコール）を使用している場合に、Places Serviceデータベースの場所コンテキストデータを、送信されるすべてのAnalytics呼び出しに自動的に追加するように更新中です。 また、この更新により、POIの入口または出口（アクティブな呼び出し）で直接Analyticsトラッキングの呼び出しを実行するルールの作成も可能になります。
