---
title: POI のバルクアップロード
description: ここでは、POI を一括アップロードする方法について説明します。
exl-id: 72704bfc-5837-4439-bdb2-e77ddf935639
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '837'
ht-degree: 0%

---

# POI のバルクアップロード {#bulk-upload-pois}

Places Service の **POI を読み込み** ボタンを使用すると、CSV ファイルを使用して新しい POI を一括アップロードできます。 必要なデータ列と、オプションのカスタムメタデータを追加する方法を示す、サンプルのスプレッドシートテンプレートが用意されています。

![ 一括読み込み画面 ](/help/assets/Bulk-import.png)

一括読み込みと一括編集のプロセスを示す次のビデオを参照してください。

<!--I changed this embed to a link to pass validation. We should not link to youtube videos, so please upload this to MCP-->

[Places Service の一括 POI 読み込みと編集 ](https://www.youtube.com/watch?v=75qVtirsXhg)

## Python API スクリプト

Web サービス API を使用して、.csv ファイルから POI データベースへの POI のバッチインポートを簡素化するために、一連の Python スクリプトが作成されました。 これらのスクリプトは、このオープンソース [git リポジトリ ](https://github.com/adobe/places-scripts) からダウンロードできます。

これらのスクリプトを実行する前に、Web サービス API にアクセスするには、*統合の概要と前提条件* の [ ユーザーアクセスの前提条件 ](/help/web-service-api/adobe-i-o-integration.md) を参照してください。

スクリプトの詳細を次に示します。

>[!TIP]
>
>この情報は、[git リポジトリ ](https://github.com/adobe/places-scripts) の Readme ファイルにも記載されています。

## CSV ファイル

サンプルの.csv ファイル `places_sample.csv` は、このパッケージの一部で、必要なヘッダーとサンプルデータの行が含まれています。 これらのヘッダーはすべて小文字で、Places データベースで使用される予約済みのメタデータキーに対応しています。 .csv ファイルに追加する列は、POI ごとに個別のメタデータセクションで、キーと値のペアとして POI データベースに追加され、ヘッダー値がキーとして使用されます。

次に、使用する必要がある列と値のリストを示します。

* `lib_id`

  POI データベースから取得された有効なライブラリ ID。

* `type`

  ポイントは現在唯一の有効な値です。

* `longitude`

  -180 ～ 180 の範囲の値。

* `latitude`

  -85 ～ 85 の値。

* `radius`

  10 ～ 20,000 の範囲の値。

### 列の値

次の列の値は、Places Service UI で使用されます。

* 色。場所サービス UI マップの POI の場所を表すピンの色として使用されます。
   * 有効な値は、「」、「#3E76D0」、「#AA99E8」、「#DC2ABA」、「#FC685B」、「#FC962E」、「#F6C436」、「#BECE5D」、「#61B56B」、「#3DC8DE」です。
   * この値が空白の場合、Places Service UI はデフォルトのカラーとして青を使用します。

     値はそれぞれ、青（#3E76D0）、紫（#AA99E8）、fuschia （#DC2ABA）、オレンジ（#FC685B）、淡オレンジ（#FC962E）、黄（#F6C436）、淡緑（#BECE5D）、緑（#61B56B）、淡青（#3DC8DE）に対応します。

* アイコン。Places Service UI マップ上の POI の場所を表すピンのアイコンとして使用されます。

   * 有効な値は、「」、shop、hotelbed、車、飛行機、列車、船、スタジアム、amusementpark、アンカー、ビーカー、ベル、入札、本、箱、ブリーフケース、参照、ブラシ、建物、計算機、カメラ、時計、教育、懐中電灯、フォロー、ゲーム、女性、男性、ギフト、ハンマー、心臓、ホーム、キー、起動、電球、メールボックス、お金、ピン、昇格、リボン、shoppingCart、star、target、teapot、thumbDown、thumbUp、トラップ、トロフィー、レンチです。

     アイコンの値は、次の図に表示される順序で一覧表示されます。

     ![UI のアイコン ](/help/assets/UI_icons.png)

   * 値が空白の場合、UI ではデフォルトのアイコンとして星が使用されます。

* 説明のない列は空白のままで構いません。

## スクリプトの実行

1. [git リポジトリー ](https://github.com/adobe/places-scripts) からローカルディレクトリにファイルをダウンロードします。
1. テキストエディターで、`config.py` ファイルを開き、次のタスクを実行します。

   a.次の変数値を文字列として編集します。

   * `csv_file_path`

     これは、`.csv` ファイルへのパスです。

   * `access_code`

     これは、コールトゥAdobe IMSから取得されたアクセスコードです。 このアクセスコードの取得方法について詳しくは、*統合の概要および前提条件* の [ ユーザーアクセスの前提条件 ](/help/web-service-api/adobe-i-o-integration.md) を参照してください。

   * `org_id`

     POI の読み込み先のExperience Cloud orgID。 組織 ID の取得方法について詳しくは、*統合の概要と前提条件* の [ ユーザーアクセスの前提条件 ](/help/web-service-api/adobe-i-o-integration.md) を参照してください。

   * `api_key`

     これは、Adobe I/Oの Places Integration から取得した Places REST API キーです。 API キーの取得方法について詳しくは、*統合の概要と前提条件* の [ ユーザーアクセスの前提条件 ](/help/web-service-api/adobe-i-o-integration.md) を参照してください。

   b.変更を保存します。

1. ターミナルウィンドウで、`…/places-scripts/import/` ディレクトリに移動します。
1. `python ./places_import.py` と入力し、**[!UICONTROL enter]** （**[!UICONTROL return]**）キーを押します。


## CSV チェックを事前に読み込む

スクリプトは最初に.csv ファイルに対して次のチェックを完了します。

* `.csv` ファイルが指定されたかどうか。
* ファイルパスが有効かどうか。
* 予約済みのメタデータヘッダーを含めるかどうか。

  予約済みのメタデータヘッダーは、lib_id、名前、説明、タイプ、経度、緯度、半径、国、状態、市区町村、通り、カテゴリ、アイコンおよび色です。

  >[!TIP]
  >
  >ヘッダーはすべて小文字で、任意の順序でリストできます。

* CSV ファイルセクションで指定された列の値を検証します。

エラーが見つかった場合、スクリプトはエラーを出力して中止します。 エラーが見つからない場合、スクリプトは 1000 個のバッチで POI を読み込もうとします。 バッチが正常に読み込まれると、スクリプトはステータスコード 200 をレポートします。 バッチが正常に読み込まれない場合は、エラーがレポートされます。

## 単体テスト

単体テストは `tests.py` ファイルにあり、各プルリクエストの前に実行する必要があり、すべて成功する必要があります。 新しいコードで追加のテストを追加する必要があります。 テストを実行するには、`…/places-scripts/import/` ディレクトリに移動し、ターミナルに `python ./places_import.py` と入力します。
