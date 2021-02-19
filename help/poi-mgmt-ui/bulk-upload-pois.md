---
title: POIの一括アップロード
description: POIを一括アップロードする方法について説明します。
translation-type: tm+mt
source-git-commit: 462df20bb351795dc72009cc18d390cb45e262a8
workflow-type: tm+mt
source-wordcount: '861'
ht-degree: 0%

---


# POIのバルクアップロード{#bulk-upload-pois}

Places Serviceの「**POIを読み込み**」ボタンを使用して、CSVファイルを使用して新しいPOIを一括アップロードできます。 必要なデータ列を示し、オプションのカスタムメタデータを追加する方法を示すサンプルスプレッドシートテンプレートが用意されています。

![一括インポート画面](/help/assets/Bulk-import.png)

一括インポートおよび一括編集のプロセスを示す次のビデオを参照してください。

<!--I changed this embed to a link to pass validation. We should not link to youtube videos, so please upload this to MCP-->

[サービスの一括インポートとPOIの編集](https://www.youtube.com/watch?v=75qVtirsXhg)

## Python APIスクリプト

一連のPythonスクリプトが作成され、Web Service APIを使用して.csvファイルからPOIデータベースへのPOIのバッチインポートを簡略化しました。 これらのスクリプトは、このオープンソース[git repo](https://github.com/adobe/places-scripts)からダウンロードできます。

これらのスクリプトを実行する前に、WebサービスAPIにアクセスするための&#x200B;*ユーザーアクセスの前提条件*&#x200B;について、[統合の概要と前提条件](/help/web-service-api/adobe-i-o-integration.md)を参照してください。

スクリプトに関する情報を次に示します。

>[!TIP]
>
>この情報は、[git repo](https://github.com/adobe/places-scripts)のreadmeファイルにも含まれています。

## CSVファイル

サンプルの.csvファイル`places_sample.csv`は、このパッケージの一部で、必要なヘッダーとサンプルデータの行が含まれています。 これらのヘッダはすべて小文字で、Placesデータベースで使用される予約済みのメタデータキーに対応しています。 .csvファイルに追加した列は、POIごとにキー/値のペアとして別々のメタデータセクションにあるPOIデータベースに追加され、ヘッダー値がキーとして使用されます。

使用する必要がある列と値のリストを次に示します。

* `lib_id`

   POIデータベースから取得した有効なライブラリID。

* `type`

   現在、有効な値はポイントのみです。

* `longitude`

   -180 ～ 180の値です。

* `latitude`

   -85 ～ 85の値です。

* `radius`

   10 ～ 20,000の値です。

### 列の値

次の列の値は、Places Service UIで使用されます。

* 色。Places Service UIマップのPOIの位置を表すピンの色として使用されます。
   * 有効な値は、「」、「#3E76D0」、「#AA99E8」、「#DC2ABA」、「#FC685B」、「#FC962E」、「#F6C436」、「#BECE5D」、「#61B56」です。b、#3DC8DE、および&quot;&quot;を追加します。
   * 値を空白のままにすると、Places Service UIではデフォルトの色として青が使用されます。

      値は、青(#3E76D0)、紫(#AA99E8)、フスキア(#DC2ABA)、オレンジ(#FC685B)、淡いオレンジ(#FC962E)、黄(#F6C436)、明るい(#BECE5D)、緑(#61B56B)、ライトブルー(#3DC8DE)です。

* アイコン。Places Service UIマップ上のPOIの位置を表すピン上のアイコンとして使用されます。

   * 有効な値は、「」、ショップ、ホテルベッド、車、飛行機、飛行機、船、球場、アムセントパーク、アンカー、ビーカー、ベル、入札、書き込み、箱、ブラウズ、ブラシ、建物、カメラ、時計、教育、フラッシュライト、追随、ゲーム、女性、男性、ハンマー、ハート、ホーム、ホーム、電球、ピン、プロモート、ショッピン星形、ターゲット、ティーポット、thumbDown、thumbUp、トラップ、トロフィー、レンチ。

      アイコンの値は、次の図に示す順序で表示されます。

      ![UIのアイコン](/help/assets/UI_icons.png)

   * 値を空白のままにすると、UIはデフォルトのアイコンとして星形を使用します。

* 言及されていない列は空白にできます。

## スクリプトの実行

1. [git repo](https://github.com/adobe/places-scripts)からローカルディレクトリにファイルをダウンロードします。
1. テキストエディターで`config.py`ファイルを開き、次のタスクを実行します。

   a.次の変数値を文字列として編集します。

   * `csv_file_path`

      これは`.csv`ファイルへのパスです。

   * `access_code`

      これは、AdobeIMSへの呼び出しから取得されたアクセスコードです。 このアクセスコードの取得方法について詳しくは、[統合の概要と前提条件](/help/web-service-api/adobe-i-o-integration.md)の&#x200B;*ユーザーアクセスの前提条件*&#x200B;を参照してください。

   * `org_id`

      POIのインポート先となるExperience CloudorgID。 組織IDの取得方法について詳しくは、[統合の概要と前提条件](/help/web-service-api/adobe-i-o-integration.md)の&#x200B;*ユーザーアクセスの前提条件*&#x200B;を参照してください。

   * `api_key`

      これは、Places REST APIキーで、Adobe I/Oプレイス統合から取得します。 APIキーの取得方法について詳しくは、[統合の概要と前提条件](/help/web-service-api/adobe-i-o-integration.md)の&#x200B;*ユーザーアクセスの前提条件*&#x200B;を参照してください。
   b.変更を保存します。

1. ターミナルウィンドウで`…/places-scripts/import/`ディレクトリに移動します。
1. `python ./places_import.py`と入力し、**[!UICONTROL enter]** (**[!UICONTROL return]**)キーを押します。


## CSVチェックの事前インポート

スクリプトは、最初に.csvファイルに対して次のチェックを完了します。

* `.csv`ファイルが指定されたかどうか。
* ファイルパスが有効かどうか。
* 予約済みのメタデータヘッダを含めるかどうか。

   予約済みのメタデータヘッダは、lib_id、名前、説明、種類、経度、緯度、半径、国、都道府県、市、市、街、カテゴリ、アイコン、色です。

   >[!TIP]
   >
   >ヘッダーはすべて小文字で、任意の順序で表示できます。

* 「CSVファイル」セクションで指定した列の値を検証します。

エラーが見つかった場合、スクリプトはエラーを出力し、中止します。 エラーが見つからない場合、スクリプトは1000のバッチでPOIを読み込もうとします。 バッチが正常に読み込まれた場合、スクリプトはステータスコード200を報告します。 バッチが正常にインポートされない場合は、エラーが報告されます。

## 単体テスト

ユニットテストは`tests.py`ファイル内にあり、各プル要求の前に実行し、すべての処理を完了する必要があります。 新しいコードを使用して、テストを追加する必要があります。 テストを実行するには、`…/places-scripts/import/`ディレクトリに移動し、ターミナルに`python ./places_import.py`と入力します。
