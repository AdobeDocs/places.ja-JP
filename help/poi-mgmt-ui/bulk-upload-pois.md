---
title: バルクアップロード POI
description: この節では、POIを一括アップロードする方法について説明します。
exl-id: 72704bfc-5837-4439-bdb2-e77ddf935639
TQID: https://experienceleague.adobe.com/FVZzn3FwSAFgnRBjkiFwHG8Zl2I-I4fPrqax-zGNclk
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
    internal-label: CX Enterprise
  - id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
    internal-label: Target
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
  - id: f002a92a-b99f-47a4-90c8-65e0e415bc7a
    internal-label: Pass
feature_v2:
  - id: bef6f891-2e8a-425e-8f99-7ddf22070daa
    internal-label: APIs
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
    internal-label: Data collection
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
    internal-label: Places
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
    internal-label: Metadata
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
source-git-commit: d8704da9c84a066f72471421290d4b46c65f41e1
workflow-type: tm+mt
source-wordcount: '854'
ht-degree: 0%
---
# POIのバルクアップロード {#bulk-upload-pois}

Places サービスの&#x200B;**POIsの読み込み** ボタンを使用すると、CSV ファイルを使用して新しいPOIを一括アップロードできます。 必要なデータ列と、オプションのカスタムメタデータを追加する方法を示すサンプルスプレッドシートテンプレートが提供されます。

![一括インポート画面](/help/assets/Bulk-import.png)

一括読み込みと一括編集のプロセスを示す次のビデオを参照してください。

<!--I changed this embed to a link to pass validation. We should not link to youtube videos, so please upload this to MCP-->

[Places サービスの一括読み込みとPOIの編集](https://www.youtube.com/watch?v=75qVtirsXhg)

## Python API スクリプト

Web サービス APIを使用して、.csv ファイルからPOIをPOI データベースにバッチインポートする作業を簡略化するための一連のPython スクリプトが作成されました。 これらのスクリプトは、このオープンソース [git リポジトリ &#x200B;](https://github.com/adobe/places-scripts)からダウンロードできます。

これらのスクリプトを実行する前に、web サービス APIにアクセスするには、[統合の概要と前提条件](/help/web-service-api/adobe-i-o-integration.md)の「*ユーザーアクセスの前提条件*」を参照してください。

以下に、スクリプトに関する情報をいくつか示します。

>[!TIP]
>
>この情報は、[Git リポジトリ &#x200B;](https://github.com/adobe/places-scripts)のreadme ファイルにも含まれています。

## CSV ファイル

サンプル .csv ファイル `places_sample.csv`は、このパッケージの一部であり、必要なヘッダーとサンプルデータの行が含まれています。 これらのヘッダーはすべて小文字で、Places データベースで使用される予約メタデータキーに対応します。 .csv ファイルに追加した列は、各POIの個別のメタデータセクションのPOI データベースにキーと値のペアとして追加され、ヘッダー値がキーとして使用されます。

以下に、使用する必要がある列と値のリストを示します。

* `lib_id`

  POI データベースから取得された有効なライブラリ ID。

* `type`

  ポイントは現在唯一の有効な値です。

* `longitude`

  -180 ～ 180の値。

* `latitude`

  -85 ～ 85の値。

* `radius`

  10 ～ 20,000の値。

### 列の値

Places サービス UIでは、次の列の値が使用されます。

* color:Places サービス UI マップ内のPOIの場所を表すピンの色として使用されます。
  * 有効な値は、「」、#3E76D0、#AA99E8、#DC2ABA、#FC685B、#FC962E、#F6C436、#BECE5D、#61B56B、#3DC8DEおよび「」です。
  * 値が空白のままの場合、Places サービス UIではデフォルトの色として青が使用されます。

    値は、それぞれ青（#3E76D0）、紫（#AA99E8）、フスキア（#DC2ABA）、オレンジ（#FC685B）、明るいオレンジ（#FC962E）、黄色（#F6C436）、明るい緑（#BECE5D）、緑（#61B56B）、明るい青（#3DC8DE）に対応します。

* アイコン：Places サービス UI マップ上のPOIの場所を表すピンのアイコンとして使用されます。

  * 有効な値は&quot;、ショップ、hotelbed、車、飛行機、列車、船、スタジアム、amusementpark、アンカー、ビーカー、入札、本、ブリーフケース、参照、ブラシ、建物、計算機、カメラ、時計、教育、懐中電灯、フォロー、ゲーム、女性、ギフト、ハンマー、ハート、ホーム、キー、起動、電球、メールボックス、お金、ピン、プロモーション、リボン、ショッピングカート、星、ターゲット、teapot、thumbDown、thumbUp、トラップ、トロフィー、レンチです。

    アイコンの値は、次の図に示す順序で一覧表示されます。

    UIの![&#x200B; アイコン &#x200B;](/help/assets/UI_icons.png)

  * 値が空白のままの場合、UIはデフォルトのアイコンとしてstarを使用します。

* 記載されていない列は空白のままにできます。

## スクリプトの実行

1. [git リポジトリ &#x200B;](https://github.com/adobe/places-scripts)からローカルディレクトリにファイルをダウンロードします。
1. テキストエディターで`config.py` ファイルを開き、次のタスクを実行します。

   a. 次の変数値を文字列として編集します。

   * `csv_file_path`

     これは`.csv` ファイルへのパスです。

   * `access_code`

     これは、Adobe IMSへの呼び出しから取得したアクセスコードです。 このアクセスコードの取得方法について詳しくは、[統合の概要と前提条件](/help/web-service-api/adobe-i-o-integration.md)の「*ユーザーアクセスの前提条件*」を参照してください。

   * `org_id`

     POIをインポートするExperience Cloud組織ID。 組織IDの取得方法について詳しくは、[統合の概要と前提条件](/help/web-service-api/adobe-i-o-integration.md)の「*ユーザーアクセスの前提条件*」を参照してください。

   * `api_key`

     これは、Adobe I/O Places統合から取得したPlaces REST API キーです。 API キーの取得方法について詳しくは、[統合の概要と前提条件](/help/web-service-api/adobe-i-o-integration.md)の「*ユーザーアクセスの前提条件*」を参照してください。

   b. 変更を保存します。

1. ターミナルウィンドウで、`…/places-scripts/import/` ディレクトリに移動します。
1. `python ./places_import.py`と入力し、**[!UICONTROL enter]** （**[!UICONTROL return]**）キーを押します。


## CSV チェックの事前インポート

スクリプトは、最初に.csv ファイルに対して次のチェックを完了します。

* `.csv` ファイルが指定されたかどうか。
* ファイルパスが有効かどうかを確認します。
* 予約されたメタデータヘッダーが含まれているかどうか。

  予約されているメタデータヘッダーは、lib_id、名前、説明、タイプ、経度、緯度、半径、国、都道府県、都市、通り、カテゴリ、アイコン、および色です。

  >[!TIP]
  >
  >ヘッダーはすべて小文字で、任意の順序で一覧表示できます。

* CSV ファイルセクションで指定された列の値を検証します。

エラーが見つかった場合、スクリプトはエラーを出力して中止します。 エラーが見つからない場合、スクリプトはPOIを1000のバッチでインポートしようとします。 バッチが正常にインポートされた場合、スクリプトはステータスコード 200を報告します。 バッチが正常にインポートされない場合、エラーが報告されます。

## ユニットテスト

単体テストは`tests.py` ファイル内にあり、各プルリクエストの前に実行する必要があり、すべて合格する必要があります。 新しいコードで追加のテストを追加する必要があります。 テストを実行するには、`…/places-scripts/import/` ディレクトリに移動し、ターミナルに`python ./places_import.py`と入力します。
