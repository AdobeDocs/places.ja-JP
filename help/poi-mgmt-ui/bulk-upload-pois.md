---
title: POI のバルクアップロード
description: この節では、POI を一括アップロードする方法に関する情報を提供します。
exl-id: 72704bfc-5837-4439-bdb2-e77ddf935639
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '861'
ht-degree: 0%

---

# POI のバルクアップロード {#bulk-upload-pois}

この **POI をインポート** 」ボタンを使用して、CSV ファイルを使用して新しい POI を一括アップロードできます。 必要なデータ列とオプションのカスタムメタデータの追加方法を示す、サンプルのスプレッドシートテンプレートが用意されています。

![一括読み込み画面](/help/assets/Bulk-import.png)

一括読み込みおよび一括編集のプロセスを示す次のビデオを参照してください。

<!--I changed this embed to a link to pass validation. We should not link to youtube videos, so please upload this to MCP-->

[Places Service の一括読み込みおよび POI の編集](https://www.youtube.com/watch?v=75qVtirsXhg)

## Python API スクリプト

Web サービス API を使用して.csv ファイルから POI データベースへの POI のバッチインポートを簡略化する Python スクリプトのセットが作成されました。 これらのスクリプトは、このオープンソースからダウンロードできます [git リポジトリ](https://github.com/adobe/places-scripts).

これらのスクリプトを実行する前に、Web サービス API にアクセスするには、 *ユーザーアクセスの前提条件* in [統合の概要と前提条件](/help/web-service-api/adobe-i-o-integration.md).

スクリプトの情報を以下に示します。

>[!TIP]
>
>この情報は、readme ファイルの [git リポジトリ](https://github.com/adobe/places-scripts).

## CSV ファイル

サンプルの.csv ファイル `places_sample.csv`は、このパッケージの一部で、必要なヘッダーとサンプルデータの行を含みます。 これらのヘッダーはすべて小文字で、Places データベースで使用される予約済みのメタデータキーに対応しています。 .csv ファイルに追加した列は、キーと値のペアとして POI ごとに別々のメタデータセクションに POI データベースに追加され、ヘッダー値がキーとして使用されます。

次に、使用する必要のある列と値のリストを示します。

* `lib_id`

   POI データベースから取得された有効なライブラリ ID。

* `type`

   現在有効な値は点のみです。

* `longitude`

   -180 ～ 180 の値です。

* `latitude`

   -85 ～ 85 の値。

* `radius`

   10 ～ 20,000 の範囲の値。

### 列の値

次の列の値は、Places Service UI で使用されます。

* 色：Places Service UI マップで POI の場所を表すピンの色として使用されます。
   * 有効な値は、&quot;&quot;、#3E76D0、#AA99E8、#DC2ABA、#FC685B、#FC962E、#F6C436、#BECE5D、#61B56B、#3DC8DE、&quot;、&quot;&quot;です。
   * この値を空白のままにした場合、Places Service UI のデフォルト色は青になります。

      値は、それぞれ、青 (#3E76D0)、紫 (#AA99E8)、扶桑 (#DC2ABA)、橙 (#FC685B)、淡い橙 (#FC962E)、黄 (#F6C436)、淡い緑 (#BECE5D)、緑 (#61B56B)、淡い青 (#3DC8DE) に対応します。

* アイコン。Places Service UI マップ上の POI の場所を表すピン上のアイコンとして使用されます。

   * 有効な値は、&quot;、ショップ、ホテルベッド、車、電車、船、スタジアム、遊具、アンカー、ビーカー、ベル、ベル、入札、箱、ブラウズ、ブラシ、建物、計算機、カメラ、時計、教育、懐中電灯、フォロー、ゲーム、女性、男性、ギフト、ハート、ホーム、起動、メールボックス、電源、リボン、ショッピング、星、ターゲット、ティーポット、thumbDown、thumbUp、トラップ、トロフィー、レンチ。

      アイコン値は、次の図に示す順序で一覧表示されます。

      ![UI のアイコン](/help/assets/UI_icons.png)

   * 値が空白の場合、UI ではデフォルトのアイコンとして星が使用されます。

* 指定されていない列は空白のままにすることができます。

## スクリプトの実行

1. からファイルをダウンロードする [git リポジトリ](https://github.com/adobe/places-scripts) をローカルディレクトリに追加します。
1. テキストエディターで、 `config.py` ファイルを作成し、次のタスクを実行します。

   a.次の変数値を文字列として編集します。

   * `csv_file_path`

      これは、 `.csv`  ファイル。

   * `access_code`

      これは、の呼び出しから取得されたアクセスコードです。Adobe IMS このアクセスコードの取得方法について詳しくは、 *ユーザーアクセスの前提条件* in [統合の概要と前提条件](/help/web-service-api/adobe-i-o-integration.md).

   * `org_id`

      POI のインポート先となるExperience CloudorgID。 組織 ID の取得方法について詳しくは、 *ユーザーアクセスの前提条件* in [統合の概要と前提条件](/help/web-service-api/adobe-i-o-integration.md).

   * `api_key`

      これは、Places 統合から取得した Places REST API キーです。Adobe I/OPlaces 統合。 API キーの取得方法について詳しくは、 *ユーザーアクセスの前提条件* in [統合の概要と前提条件](/help/web-service-api/adobe-i-o-integration.md).
   b.変更を保存します。

1. ターミナルウィンドウで、 `…/places-scripts/import/` ディレクトリ。
1. 入力 `python ./places_import.py` をクリックし、 **[!UICONTROL 入力]** (**[!UICONTROL 戻る]**) キーを押します。


## CSV チェックの事前インポート

スクリプトは、最初に.csv ファイルに対する次のチェックを完了します。

* Whether a `.csv` ファイルが指定されました。
* ファイルパスが有効かどうかを示します。
* 予約済みのメタデータヘッダーを含めるかどうか。

   予約されているメタデータヘッダーは、lib_id、名前、説明、タイプ、経度、緯度、半径、国、都道府県、市区町村、通り、カテゴリ、アイコン、色です。

   >[!TIP]
   >
   >ヘッダーはすべて小文字で、任意の順序で一覧表示できます。

* CSV ファイルセクションで指定された列の値を検証します。

エラーが見つかった場合、スクリプトはエラーを出力し、中止します。 エラーが見つからない場合、スクリプトは POI を 1000 個のバッチでインポートしようとします。 バッチが正常に読み込まれた場合、スクリプトはステータスコード 200 をレポートします。 バッチが正常にインポートされない場合は、エラーが報告されます。

## 単体テスト

単体テストは、 `tests.py` ファイルを抽出し、各プルリクエストの前に実行し、すべてを渡す必要があります。 新しいコードを使用して、追加のテストを追加する必要があります。 テストを実行するには、 `…/places-scripts/import/` ディレクトリに、 `python ./places_import.py` 端末内。
