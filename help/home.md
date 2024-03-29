---
title: Places Service
description: Places Service は、モバイルユーザーのエンゲージメントを理解するための重要なコンテキストです。 このコンテキストを使用すると、モバイルアプリ開発者はアプリのデザインを強化し、よりパーソナライズされた魅力的なエクスペリエンスにすることができます。
exl-id: 7369176f-c072-437a-9ee3-b463c5ff1d12
source-git-commit: e78e3c5ee6623d6cdf2a33c0582667a70283fdc6
workflow-type: tm+mt
source-wordcount: '663'
ht-degree: 9%

---

# Places Service {#home}

場所は、モバイルユーザーを理解し、関与させる上で重要なコンテキストです。 このコンテキストを使用すると、モバイルアプリ開発者はアプリのデザインを強化し、よりパーソナライズされた魅力的なエクスペリエンスにすることができます。

Places Service( 旧称Adobe Experience Platform Location Service) は、位置認識機能を持つモバイルアプリで、目標地点 (POI) の柔軟なデータベースを伴う豊富で使いやすい SDK インターフェイスを使用して、位置コンテキストを理解できる位置情報サービスです。

Places Service では、次のことを実現できます。

* 他のAdobe Experience Cloudソリューションで利用できる POI のデータベースを作成および管理します。
* カスタムメタデータを POI にアタッチして、追加の属性を指定することで、より豊かで意味のあるものにします。
* マップ上の POI を視覚化して、空間コンテキストを簡単に理解し、メタデータ属性を追加/編集します。
* Adobe Experience Platform Launchで SDK を設定し、ロケーショントリガールールとメタデータに基づく条件を定義します。
* デバイスの場所を監視し、Places 拡張機能を使用して場所固有のルールを自動的にトリガーするために、記述する必要があるコードを減らします。

これにより、場所のシグナルから、重要なタイミングと場所に応じてリアルタイムでアクションを実行できます。 適切なコンテキストを使用すると、モバイルエンゲージメントエクスペリエンスをより充実させることができます。

Places の使用方法の一部を次に示します。

* 誰かが POI に入ったときにリアルタイムで通知を送信し、 *「おい…スタジアムへようこそ」*
* 自社の店舗と競合他社の店舗の足のトラフィックを分析します。
* 場所のコンテキストでオーディエンスプロファイルを使用して、オフラインの行動に基づいてオーディエンスをセグメント化します。
* 必要に応じて、ストア内エクスペリエンスでユーザーをターゲット設定します。

## Places Service コンポーネント

Places Service は、次のコンポーネントで構成されます。

* **Web サービス**

  Places REST API を使用して、POI を作成および管理できます。 REST API について詳しくは、 [ライブラリの管理](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md) および [POI の管理](/help/web-service-api/api-usage/manage-pois/manage-pois.md).

* **POI 管理インターフェイス**

  マップ上の POI を視覚化して、空間コンテキストを理解し、POI とそのカスタムメタデータを追加/編集します。

* **Places 拡張機能**

  モバイルアプリでロケーションコンテキストを統合するマルチプラットフォームモバイル API インターフェイス。 SDK について詳しくは、 [Places 拡張機能](/help/places-ext-aep-sdks/places-extension/places-extension.md).

* **ルールを起動**

  入口イベントと出口イベントでアクションをトリガー化できる、地域インテリジェントな Launch ルールです。 また、条件で地域属性を使用してエクスペリエンスをパーソナライズすることもできます。

## 用語

このドキュメントで使用される一般的な用語を以下に示します。

* A **目標点 (POI)** は、組織が興味を持つ地域です。

  POI を名前、半径、住所、カテゴリ、メタデータタグなどの属性で定義できます。

* A **ジオフェンス** は POI の一種です。

  この POI タイプは、緯度と経度の座標で定義される仮想的な地理的境界です。

* A **beacon** は POI の一種です。

  この POI タイプは、低電力の Bluetooth 信号を発することによって位置を表す物理デバイスです。 ビーコンのサポートは、将来のリリースで提供される予定です。

* **ライブラリ** は POI の集まりで、1 つではなく POI のセットへ簡単にルールを付加できるようにグループ化されています。

* An **拡張** は、Places SDK をモバイルExperience Platform Launchに統合するために必要なアプリ拡張です。

  他のモバイル SDK と共に使用する拡張機能で、エクスペリエンスに場所のコンテキストを追加します。

* **組織**&#x200B;とは、Adobe Experience Cloud で会社を識別するアドビのエンティティです。

  通常、組織は会社名です。 ただし、1 つの会社に複数の組織を含めることができます。 組織の管理者は、グループとユーザーを設定し、シングルサインオン機能を設定できます。

* **orgID** は Adobe Experience Platform をまたいで組織を表す ID です。

  詳しくは、 [組織 ID の検索](https://forums.adobe.com/thread/2339895).

* The **Experience CloudID** サービスは、Experience Cloud内のすべてのソリューションにわたって訪問者を識別する、永続的な汎用 ID を提供します。

  詳しくは、[概要](https://experienceleague.adobe.com/docs/id-service/using/intro/overview.html?lang=ja)を参照してください。

