---
title: Web サービス API の概要
description: Places Service は、Adobeのお客様が、適切なタイミングと場所で、適切な人に対し、適切な場所で、場所のデータと適切なエクスペリエンスを使用して、Adobe Experience CloudとAdobe Experience Platformのソリューションを簡単にハイドレートできるサービスのセットです。
exl-id: 9e7358d1-3ba0-4304-aeb2-fed7162afb57
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 1%

---

# Web サービス API の概要 {#places-web-services-api}

Places Service は、Adobeのお客様が、適切なタイミングと場所で、適切な人に対し、適切な場所で、場所のデータと適切なエクスペリエンスを使用して、Adobe Cloud PlatformとAdobe Experience Platformのソリューションを簡単にハイドレートできるサービスのセットです。

Web サービス API を使用すると、次の操作を実行できます。

* ジオフェンスを管理
* アプリがバックグラウンドになっている場合でもユーザーの場所を測定します
* 重要な場合にリアルタイムでデータを使用

この節では、組織の POI データを含む REST API と POI データベースの使用方法に関する情報を提供します。

## REST API

Places Service REST API を使用すると、組織の POI をプログラムで操作できます。 これらの API を使用すると、ライブラリとそれらのライブラリの POI を作成、更新、削除できます。 これらの API では、 JavaScript Object Notation(JSON) 標準を使用して、送受信するデータの形式を設定します。 JSON の主なメリットは、API クエリを開発者やマシンで書き込み、読み取り、解析が容易になる点です。

Web サービス API を使用する前に、次の要件が満たされていることを確認してください。

* Places Service が組織内でプロビジョニングされ、ユーザーとして適切なアクセス権を持っている。

   詳しくは、 *ユーザーアクセスの前提条件* in [統合の概要と前提条件](/help/web-service-api/adobe-i-o-integration.md).

* 組織で Places Service がプロビジョニングされ、アクセス権が付与されたら、Places Service のAdobe統合を作成します。

   詳しくは、 *Places Service 統合の作成* in [統合の概要と前提条件](/help/web-service-api/adobe-i-o-integration.md).

追加情報:

* 利用可能な API とその使用方法について詳しくは、 [ライブラリの管理](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md) および [POI の管理](/help/web-service-api/api-usage/manage-pois/manage-pois.md).
* これらの API のヘッダーとパラメーターについて詳しくは、 [ヘッダーとパラメーター](/help/web-service-api/api-usage/headers-and-parameters.md).
