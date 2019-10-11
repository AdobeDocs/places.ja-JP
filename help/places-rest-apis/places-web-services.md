---
title: Places webサービス
seo-title: Places webサービス
description: 場所とは、アドビのお客様が、Adobe Experience cloudとAdobe Experience Platformの各ソリューションを場所データと適切なエクスペリエンスを適切なタイミングで適切な担当者に適切なエクスペリエンスと共に適切な場所に簡単に提供する一連のサービスです。
seo-description: 場所とは、アドビのお客様が、Adobe Experience cloudとAdobe Experience Platformの各ソリューションを場所データと適切なエクスペリエンスを適切なタイミングで適切な担当者に適切なエクスペリエンスと共に適切な場所に簡単に提供する一連のサービスです。
translation-type: tm+mt
source-git-commit: d7c5fe5d7a20a647240114d25307373b493ae2f5

---


# Webサービスを配置 {#places-web-services}

場所とは、アドビのお客様がAdobe Cloud PlatformとAdobe Experience Platformの各ソリューションを場所データと適切なエクスペリエンスを適切なタイミングで適切な担当者に提供できるようにする一連のサービスです。

場所では、次の操作を行うことができます。

* ジオフェンスの管理
* アプリがバックグラウンドにある場合でもユーザーの場所を測定する
* 重要な場合にリアルタイムでデータを使用

この節では、組織のPOIデータを含むREST APIとPlacesデータベースの使用方法に関する情報を提供します。

## REST APIを配置

Places REST APIを使用すると、組織のPOIをプログラムで操作できます。 これらのAPIを使用すると、ライブラリとそれらのライブラリ内のPOIを作成、更新、削除できます。 これらのAPIは、JavaScript Object Notation(JSON)規格を使用して、送受信されるデータの形式を設定します。 JSONの主な利点は、開発者やマシンがAPIクエリを簡単に書き込み、読み取り、解析できる点です。

Places APIを使用する前に、次の要件が満たされていることを確認します。

* 組織内の場所がプロビジョニングされ、ユーザーとして適切なアクセス権を持っている。

   詳しくは、組織の要件を参照し [てください](/help/places-rest-apis/organizational-requirements.md)。

* Placesが組織でプロビジョニングされ、アクセス権を持ったら、Places用のAdobe統合を作成します。

   詳しくは、「Adobe I/O統 [合の作成」を参照してください](/help/places-rest-apis/adobe-i-o-integration/create-a-places-integration.md)。

追加情報：

* 使用可能なAPIとその使用方法について詳しくは、 [APIの使用を参照してください](/help/places-rest-apis/api-usage/api-usage.md)。
* これらのAPIのヘッダーとパラメーターについて詳しくは、ヘッダーとパラメーターを [参照してくださ](/help/places-rest-apis/api-usage/headers-and-parameters.md)い。

