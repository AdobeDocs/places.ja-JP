---
title: Web サービス APIの概要
description: Places Serviceは、Adobeのお客様が、位置情報を利用して、適切な場所で適切なユーザーに適切なタイミングで適切な体験を提供することで、Adobe Experience CloudとAdobe Experience Platformのソリューションを簡単に組み合わせることができる一連のサービスです。
exl-id: 9e7358d1-3ba0-4304-aeb2-fed7162afb57
TQID: https://experienceleague.adobe.com/jP7iQH7X85UZROjsa3XzuN0bJZjjKffODFGGji7XZfQ
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2:
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 336
ht-degree: 1%

---

# Web サービス APIの概要 {#places-web-services-api}

Places サービスは、Adobeのお客様が、位置情報を利用して、適切なタイミングと場所で適切なユーザーに適切なエクスペリエンスを提供するAdobe Cloud PlatformとAdobe Experience Platform ソリューションを簡単に組み合わせることができる一連のサービスです。

Web サービス APIを使用すると、次の操作を実行できます。

* ジオフェンスの管理
* アプリがバックグラウンドでもユーザーの場所を測定
* 重要なタイミングでデータをリアルタイムに活用

この節では、組織のPOI データを含むREST APIとPOI データベースの使用方法について説明します。

## REST API

Places サービス REST APIを使用すると、組織のPOIをプログラムで処理できます。 これらのAPIを使用すると、ライブラリとそのライブラリ内のPOIを作成、更新、削除できます。 これらのAPIは、JavaScript Object Notation （JSON）標準を使用して、送受信されるデータをフォーマットします。 JSONの主な利点は、開発者やマシンがAPI クエリを簡単に書き込み、読み取り、解析できることです。

Web サービス APIを使用する前に、次の要件が満たされていることを確認してください。

* Places サービスは組織でプロビジョニングされ、ユーザーとして適切なアクセス権を持っています。

  詳しくは、[統合の概要と前提条件](/help/web-service-api/adobe-i-o-integration.md)の「*ユーザーアクセスの前提条件*」を参照してください。

* Places サービスが組織内でプロビジョニングされ、アクセス権が付与されたら、Places サービス用のAdobe統合を作成します。

  詳しくは、[統合の概要と前提条件](/help/web-service-api/adobe-i-o-integration.md)の&#x200B;*Places サービス統合の作成*&#x200B;を参照してください。

追加情報:

* 使用可能なAPIとその使用方法について詳しくは、[&#x200B; ライブラリの管理](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md)および[POIの管理](/help/web-service-api/api-usage/manage-pois/manage-pois.md)を参照してください。
* これらのAPIのヘッダーとパラメーターについて詳しくは、[&#x200B; ヘッダーとパラメーター](/help/web-service-api/api-usage/headers-and-parameters.md)を参照してください。
