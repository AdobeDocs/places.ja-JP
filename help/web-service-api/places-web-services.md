---
title: 'Web Services APIの概要 '
seo-title: 'Web Services APIの概要 '
description: 場所とは、アドビのお客様が、Adobe Experience cloudとAdobe Experience Platformの各ソリューションを場所データと適切なエクスペリエンスを適切なタイミングで適切な担当者に適切なエクスペリエンスと共に適切な場所に簡単に提供する一連のサービスです。
seo-description: 場所とは、アドビのお客様が、Adobe Experience cloudとAdobe Experience Platformの各ソリューションを場所データと適切なエクスペリエンスを適切なタイミングで適切な担当者に適切なエクスペリエンスと共に適切な場所に簡単に提供する一連のサービスです。
translation-type: tm+mt
source-git-commit: e204958ac3acbf5fb45d2347987f35557be70e43

---


# Web Services APIの概要 {#places-web-services-api}

場所とは、アドビのお客様がAdobe Cloud PlatformとAdobe Experience Platformの各ソリューションを場所データと適切なエクスペリエンスを適切なタイミングで適切な担当者に提供できるようにする一連のサービスです。

WebサービスAPIを使用すると、次のことができます。

* ジオフェンスの管理
* アプリがバックグラウンドにある場合でもユーザーの場所を測定する
* 重要な場合にリアルタイムでデータを使用

この節では、組織のPOIデータを含むREST APIとPOIデータベースの使用方法に関する情報を提供します。

## REST API

Places REST APIを使用すると、組織のPOIをプログラムで操作できます。 これらのAPIを使用すると、ライブラリとそれらのライブラリ内のPOIを作成、更新、削除できます。 これらのAPIは、JavaScript Object Notation(JSON)規格を使用して、送受信されるデータの形式を設定します。 JSONの主な利点は、開発者やマシンがAPIクエリを簡単に書き込み、読み取り、解析できる点です。

WebサービスAPIを使用する前に、次の要件が満たされていることを確認します。

* 組織内の場所がプロビジョニングされ、ユーザーとして適切なアクセス権を持っている。

   詳しくは、以下の「組織の要件 *」の節を参* 照してください。

* Placesが組織でプロビジョニングされ、アクセス権を持ったら、Places用のAdobe統合を作成します。

   詳しくは、「 *Adobe I/O統合の概要での場所* 統合の作成 [」を参](/help/web-service-api/adobe-i-o-integration.md)照してください。

追加情報:

* 使用可能なAPIとその使用方法について詳しくは、ライブラリの管理とPOIの管理を [参照し](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md)[てください](/help/web-service-api/api-usage/manage-pois/manage-pois.md)。
* これらのAPIのヘッダーとパラメーターについて詳しくは、ヘッダーとパラメーターを [参照してくださ](/help/web-service-api/api-usage/headers-and-parameters.md)い。

## 組織の要件 {#org-requirements}

WebサービスのREST APIにアクセスするには、システム管理者に次のタスクが完了していることを確認します。

* 場所がプロビジョニングされ、組織に表示されます。
* 組織に追加されました。
* 組織内の場所に追加されました。

   詳しくは、よくある質問の「場所 *とエクスペリエンスプラットフォームの起動* 」へのユー [ザーの追加を参照してください](/help/places-faqs.md)。

* 組織にPlaces開発者として追加されました。

   開発者ロールについて詳しくは、開発者の管理を参照 [してください](https://helpx.adobe.com/enterprise/using/manage-developers.html)。