---
title: Places Service
description: Places サービスは、モバイルユーザーのエンゲージメントを理解するための重要なコンテキストです。 このコンテキストを利用することで、モバイルアプリの開発者は、アプリのデザインを強化し、よりパーソナライズされた魅力的な体験にすることができます。
exl-id: 7369176f-c072-437a-9ee3-b463c5ff1d12
TQID: https://experienceleague.adobe.com/4kI1AuV2l-qfC3mOrcsoG9NDRcOPJBdkWPmKkQuDIJk
product_v2: id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: dc5cf79d-43c4-4731-bffa-1df5d7549cb1id: e43347a8-f2c5-4aa4-8623-6f13875d7e3aid: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2: id: c132d929-fa62-4271-803e-b823be07b914id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2: id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dcid: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 684
ht-degree: 9%

---

# Places Service {#home}

位置情報は、モバイルユーザーを把握し、エンゲージするための重要なコンテキストです。 このコンテキストを利用することで、モバイルアプリの開発者は、アプリのデザインを強化し、よりパーソナライズされた魅力的な体験にすることができます。

Places サービスは、以前はAdobe Experience Platform Location Serviceとして知られていました。位置情報を認識するモバイルアプリが、SDKの豊富で使いやすいインターフェイスと、柔軟なPOI （Point of Interest）データベースを利用して、位置情報を理解できるようにする位置情報サービスです。

Places サービスを使用すると、次の操作を実行できます。

* 他のAdobe Experience Cloudソリューションと活用できるPOIのデータベースを作成および管理します。
* カスタムのメタデータをPOIに添付し、属性を追加することで、より充実した有意義なPOIを作成できます。
* 地図上でPOIを視覚化することで、空間的なコンテキストを簡単に把握し、メタデータ属性を追加/編集できます。
* Adobe Experience Platform LaunchでSDKを設定して、ロケーショントリガーのルールとメタデータベースの条件を定義します。
* デバイスの位置情報をモニタリングするために記述する必要があるコードを減らし、Places拡張機能を使用して、位置情報に固有のルールを自動的にトリガーします。

これにより、重要なタイミングと場所で、位置情報にもとづくアクションをリアルタイムに実行できるようになります。 適切なコンテキストを提供することで、より豊かなモバイルエンゲージメント体験が可能になります。

Placesを使用する方法の一部を以下に示します。

* 誰かがPOIを入力したときにリアルタイム通知を送信します。*「スタジアムへようこそ。」*
* 自社ストアと競合他社ストアの来店者数を分析する。
* 位置情報のコンテキストでオーディエンスプロファイルを使用することで、オフラインの行動にもとづいてオーディエンスをセグメンテーションできます。
* 必要に応じて、店舗体験で利用者をターゲティングする。

## Places サービスコンポーネント

Places サービスは、次のコンポーネントで構成されます。

* **Web サービス**

  Places REST APIを使用して、POIを作成および管理できます。 REST APIについて詳しくは、[ ライブラリの管理](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md)および[POIの管理](/help/web-service-api/api-usage/manage-pois/manage-pois.md)を参照してください。

* **POI管理インターフェイス**

  マップ上のPOIを視覚化して、空間的なコンテキストを把握し、POIとそのカスタムメタデータを追加/編集します。

* **Places拡張機能**

  モバイルアプリに位置情報コンテキストを統合するためのマルチプラットフォームのモバイル API インターフェイス。 SDKについて詳しくは、[Places拡張機能](/help/places-ext-aep-sdks/places-extension/places-extension.md)を参照してください。

* **ルールを起動**

  入口イベントと出口イベントを使用してアクションをトリガーできるようにする、位置情報に基づくLaunch ルール。 また、このルールでは、条件で地理属性を使用して、エクスペリエンスをパーソナライズすることもできます。

## 用語

このドキュメントで使用される一般的な用語を次に示します。

* **POI （**）は、組織が関心を持つ地域です。

  名前、半径、住所、カテゴリ、メタデータタグなどの属性を使用してPOIを定義できます。

* **ジオフェンス**&#x200B;はPOIの一種です。

  この種類のPOIは、緯度と経度の座標で定義される仮想的な地理的境界です。

* **ビーコン**&#x200B;はPOIの一種です。

  このPOI型は、低電力のブルートゥース信号を発信することで場所を表す物理的なデバイスです。 Beaconsのサポートは今後リリースされる予定です。

* **ライブラリ** は POI の集まりで、1 つではなく POI のセットへ簡単にルールを付加できるようにグループ化されています。

* **拡張機能**&#x200B;は、Places SDKをモバイルアプリに統合するために必要なExperience Platform Launch拡張機能です。

  他のモバイル SDKで使用される拡張機能を使用して、エクスペリエンスに位置情報を追加します。

* **組織**&#x200B;とは、Adobe Experience Cloud で会社を識別するアドビのエンティティです。

  一般的に、組織名は会社名です。 ただし、1つの企業は複数の組織を持つことができます。 組織管理者は、グループとユーザーを設定し、シングルサインオン機能を設定できます。

* **orgID** は Adobe Experience Platform をまたいで組織を表す ID です。

  詳しくは、[組織IDの検索](https://forums.adobe.com/thread/2339895)を参照してください。

* **Experience Cloud ID** サービスは、Experience Cloud内のすべてのソリューションで訪問者を識別する、汎用的で永続的なIDを提供します。

  詳しくは、[概要](https://experienceleague.adobe.com/docs/id-service/using/intro/overview.html?lang=ja)を参照してください。

