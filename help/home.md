---
title: Places Service
description: Places Service は、モバイルユーザーのエンゲージメントを理解するための重要なコンテキストです。 このコンテキストを使用することで、モバイルアプリ開発者はアプリのデザインを強化し、よりパーソナライズされた魅力的なエクスペリエンスにすることができます。
exl-id: 7369176f-c072-437a-9ee3-b463c5ff1d12
source-git-commit: e78e3c5ee6623d6cdf2a33c0582667a70283fdc6
workflow-type: tm+mt
source-wordcount: '663'
ht-degree: 9%

---

# Places Service {#home}

場所は、モバイルユーザーを理解し、関与するための重要なコンテキストです。 このコンテキストを使用することで、モバイルアプリ開発者はアプリのデザインを強化し、よりパーソナライズされた魅力的なエクスペリエンスにすることができます。

Places Service （旧称：Adobe Experience Platform Location Service）は、柔軟な目標地点（POI）データベースを備えた、機能が豊富で使いやすい SDK インターフェイスを使用して、位置認識機能を備えたモバイルアプリが場所のコンテキストを理解できるようにする位置情報サービスです。

Places Service を使用すると、次のことができます。

* 他のAdobe Experience Cloud ソリューションで活用できる POI のデータベースを作成および管理します。
* カスタムメタデータを POI に添付して、追加の属性を指定することで、POI を豊かで有意義なものにします。
* マップ上の POI を視覚化して、空間コンテキストを簡単に理解し、メタデータ属性を追加/編集します。
* Adobe Experience Platform Launchで SDK を設定して、場所トリガールールとメタデータベースの条件を定義します。
* デバイスの場所を監視するために記述する必要があるコードを減らし、場所トリガーを使用して場所固有のルールを自動拡張します。

これにより、場所の信号から、重要なタイミングと場所でリアルタイムにアクションを実行できます。 適切なコンテキストにより、より充実したモバイルエンゲージメントエクスペリエンスが提供されます。

次に、場所の使用方法をいくつか示します。

* 誰かが POI にエントリしたときにリアルタイム通知を送信する *「ねえ…スタジアムへようこそ」*
* 自社ストアと競合他社ストアの足のトラフィックを分析します。
* 場所のコンテキストを含んだオーディエンスプロファイルを使用して、オフライン行動に基づいてオーディエンスをセグメント化します。
* 該当する場合は、店舗内エクスペリエンスを持つユーザーをターゲットに設定します。

## Places Service コンポーネント

Places Service は、次のコンポーネントで構成されています。

* **Web サービス**

  POI は、Places REST API を使用して作成および管理できます。 REST API について詳しくは、[ ライブラリの管理 ](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md) および [POI の管理 ](/help/web-service-api/api-usage/manage-pois/manage-pois.md) を参照してください。

* **POI 管理インターフェイス**

  マップ上で POI を視覚化して、空間コンテキストを理解し、POI とそのカスタムメタデータを追加/編集します。

* **Places 拡張機能**

  モバイルアプリに場所のコンテキストを統合するためのマルチプラットフォームモバイル API インターフェイス。 SDK について詳しくは、[Places 拡張機能 ](/help/places-ext-aep-sdks/places-extension/places-extension.md) を参照してください。

* **ローンチルール**

  地域インテリジェントなローンチルールにより、入口イベントと出口イベントでアクションをトリガーにすることができます。 また、ルールでは、条件で地域属性を使用して、エクスペリエンスをパーソナライズすることもできます。

## 用語

このドキュメントで使用される一般的な用語を次に示します。

* **目標点（POI）** は、組織が関心を持つ地域ロケーションです。

  名前、半径、アドレス、カテゴリ、メタデータタグなどの属性を使用して、POI を定義できます。

* **ジオフェンス** は POI の一種です。

  この POI タイプは、緯度と経度の座標で定義される仮想的な地理的境界です。

* **ビーコン** は POI の一種です。

  この POI タイプは、低電力の Bluetooth 信号を発することで場所を表す物理デバイスです。 ビーコンのサポートは、今後のリリースで提供される予定です。

* **ライブラリ** は POI の集まりで、1 つではなく POI のセットへ簡単にルールを付加できるようにグループ化されています。

* **拡張機能** は、モバイルアプリに Places SDK を統合するために必要なExperience Platform Launch拡張機能です。

  エクスペリエンスに場所のコンテキストを追加するために、他のモバイル SDK で使用される拡張機能。

* **組織**&#x200B;とは、Adobe Experience Cloud で会社を識別するアドビのエンティティです。

  通常、組織は会社名です。 ただし、会社は複数の組織を持つことができます。 組織管理者は、グループとユーザーを設定し、シングルサインオン機能を設定できます。

* **orgID** は Adobe Experience Platform をまたいで組織を表す ID です。

  詳しくは、[orgID の検索 ](https://forums.adobe.com/thread/2339895) を参照してください。

* **Experience CloudID** サービスは、Experience Cloud内のすべてのソリューションで訪問者を特定する永続的な汎用 ID を提供します。

  詳しくは、[概要](https://experienceleague.adobe.com/docs/id-service/using/intro/overview.html?lang=ja)を参照してください。

