---
title: 'Web Services APIの概要 '
description: プレースサービスは、Adobeのお客様が、場所のデータや経験を含むAdobe Experience CloudとAdobe Experience Platformのソリューションを、適切なタイミングで適切な人に適切な場所に簡単に組み込むことができるサービスのセットです。
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 1%

---


# Web Services APIの概要 {#places-web-services-api}

プレースサービスは、Adobeのお客様が、場所のデータや経験を含むAdobe Cloud PlatformとAdobe Experience Platformのソリューションを、適切なタイミングで適切な人に適切な場所に簡単に組み込むことができるサービスのセットです。

WebサービスAPIを使用すると、次のことができます。

* ジオフェンスの管理
* アプリがバックグラウンドにある場合でもユーザーの場所を測定します
* 重要な場合にデータをリアルタイムで使用

この節では、組織のPOIデータを含むREST APIとPOIデータベースの使用方法について説明します。

## REST API

Places Service REST APIを使用すると、組織のPOIをプログラムで操作できます。 これらのAPIを使用すると、ライブラリとそれらのライブラリ内のPOIを作成、更新、削除できます。 これらのAPIは、JavaScript Object Notation(JSON)規格を使用して、送受信するデータの形式を設定します。 JSONの主な利点は、開発者やマシンがAPIクエリの書き込み、読み取り、解析を容易にできることです。

WebサービスAPIを使用する前に、以下の要件が満たされていることを確認してください。

* Places Serviceは組織でプロビジョニングされ、ユーザーとして適切なアクセス権を持っています。

   詳しくは、 *統合の概要と前提条件の「ユーザーアクセスの* 前提条件 [」を参照してください](/help/web-service-api/adobe-i-o-integration.md)。

* 組織でPlaces Serviceがプロビジョニングされ、アクセス権を持ったら、Places ServiceのAdobe統合を作成します。

   詳細については、「 *統合の概要と必要条件」の「Places Service統合の* 作成 [」を参照してください](/help/web-service-api/adobe-i-o-integration.md)。

追加情報:

* 使用可能なAPIとその使用方法について詳しくは、ライブラリの [管理](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md) およびPOIの [管理を参照してください](/help/web-service-api/api-usage/manage-pois/manage-pois.md)。
* これらのAPIのヘッダーとパラメーターについて詳しくは、 [ヘッダーとパラメーターを参照してください](/help/web-service-api/api-usage/headers-and-parameters.md)。