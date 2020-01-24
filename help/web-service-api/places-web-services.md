---
title: 'Web Services APIの概要 '
description: プレースサービスは、Adobe Experience cloudとAdobe Experience Platformの各ソリューションを、場所データと適切なエクスペリエンスを適切なタイミングで適切な担当者に適切なエクスペリエンスと共に、アドビのお客様が簡単に活用できる一連のサービスです。
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b

---


# Web Services APIの概要 {#places-web-services-api}

プレースサービスは、Adobe Cloud PlatformとAdobe Experience Platformの各ソリューションを、場所データと適切なエクスペリエンスを適切なタイミングで適切な個人に適切なエクスペリエンスと共に、アドビのお客様が簡単に活用できる一連のサービスです。

WebサービスAPIを使用すると、次のことができます。

* ジオフェンスの管理
* アプリがバックグラウンドにある場合でもユーザーの場所を測定する
* 重要な場合にリアルタイムでデータを使用

この節では、組織のPOIデータを含むREST APIとPOIデータベースの使用方法に関する情報を提供します。

## REST API

Places Service REST APIを使用すると、組織のPOIをプログラムで操作できます。 これらのAPIを使用すると、ライブラリとそれらのライブラリ内のPOIを作成、更新、削除できます。 これらのAPIは、JavaScript Object Notation(JSON)規格を使用して、送受信されるデータの形式を設定します。 JSONの主な利点は、開発者やマシンがAPIクエリを簡単に書き込み、読み取り、解析できる点です。

WebサービスAPIを使用する前に、次の要件が満たされていることを確認します。

* プレースサービスが組織内でプロビジョニングされ、ユーザーとして適切なアクセス権を持っている。

   詳しくは、統合の概要と前提 *条件の「ユーザーアクセスの* 前提条 [件」を参照してください](/help/web-service-api/adobe-i-o-integration.md)。

* Placesサービスが組織でプロビジョニングされ、アクセス権を持ったら、Places Service用のAdobe統合を作成します。

   詳しくは、「統合の概要と前提 *条件」の「場所サービス統合の作成* 」 [を参照してください](/help/web-service-api/adobe-i-o-integration.md)。

追加情報:

* 使用可能なAPIとその使用方法について詳しくは、ライブラリの管理とPOIの管理を [参照し](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md)[てください](/help/web-service-api/api-usage/manage-pois/manage-pois.md)。
* これらのAPIのヘッダーとパラメーターについて詳しくは、ヘッダーとパラメーターを [参照してくださ](/help/web-service-api/api-usage/headers-and-parameters.md)い。