---
title: Web サービス API の概要
description: Places Service は、Adobeのお客様がAdobe Experience CloudおよびAdobe Experience Platformのソリューションに、適切な場所の位置情報と適切なエクスペリエンスを、適切なタイミングで適切な対象者に提供しやすくする一連のサービスです。
exl-id: 9e7358d1-3ba0-4304-aeb2-fed7162afb57
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 1%

---

# Web サービス API の概要 {#places-web-services-api}

Places Service は、Adobeのお客様がAdobe Cloud PlatformおよびAdobe Experience Platformのソリューションに、適切な場所の位置情報と適切なエクスペリエンスを、適切なタイミングで適切な対象者に提供しやすくする一連のサービスです。

Web サービス API を使用すると、次の操作を実行できます。

* ジオフェンスの管理
* アプリがバックグラウンドにある場合でも、ユーザーの場所を測定
* 必要に応じてリアルタイムでデータを使用

ここでは、REST API と、組織の POI データを含んだ POI データベースの使用方法について説明します。

## REST API

Places Service REST API を使用すると、組織の POI をプログラムで操作できます。 これらの API を使用すると、ライブラリおよびライブラリ内の POI を作成、更新、削除できます。 これらの API は、JavaScript Object Notation （JSON）標準を使用して、送受信されるデータをフォーマットします。 JSON の主な利点は、API クエリを使用して、開発者やマシンでの書き込み、読み取り、解析が容易になることです。

Web サービス API を使用する前に、次の要件が満たされていることを確認してください。

* Places Service が組織でプロビジョニングされており、ユーザーとして適切なアクセス権を持っています。

  詳しくは、*統合の概要と前提条件* の [&#x200B; ユーザーアクセスの前提条件 &#x200B;](/help/web-service-api/adobe-i-o-integration.md) を参照してください。

* Places Service がプロビジョニングされ、アクセス権を持ったら、Places Service のAdobe統合を作成します。

  詳しくは、*統合の概要と前提条件* の [Places Service 統合の作成 &#x200B;](/help/web-service-api/adobe-i-o-integration.md) を参照してください。

追加情報:

* 使用可能な API とその使用方法について詳しくは、[&#x200B; ライブラリの管理 &#x200B;](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md) および [POI の管理 &#x200B;](/help/web-service-api/api-usage/manage-pois/manage-pois.md) を参照してください。
* これらの API のヘッダーとパラメーターについて詳しくは、[&#x200B; ヘッダーとパラメーター &#x200B;](/help/web-service-api/api-usage/headers-and-parameters.md) を参照してください。
