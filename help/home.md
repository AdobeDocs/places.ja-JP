---
title: Adobe Experience Platform Location Service
seo-title: Adobe Experience Platform Location Service
description: 'ロケーションサービスは、モバイルユーザーのエンゲージメントを理解するための重要なコンテキストです。 このコンテキストを使用すると、モバイルアプリ開発者はアプリのデザインを強化し、よりパーソナライズされた魅力的なエクスペリエンスを実現できます。 '
seo-description: 'ロケーションサービスは、モバイルユーザーのエンゲージメントを理解するための重要なコンテキストです。 このコンテキストを使用すると、モバイルアプリ開発者はアプリのデザインを強化し、よりパーソナライズされた魅力的なエクスペリエンスを実現できます。 '
translation-type: tm+mt
source-git-commit: 9fd6c1fdd740a021d7612aa33693c392bff53994

---


# Adobe Experience Platform Location Serviceの概要 {#home}

場所は、モバイルユーザーを理解し、関与させるための重要なコンテキストです。 このコンテキストを使用すると、モバイルアプリ開発者はアプリのデザインを強化し、よりパーソナライズされた魅力的なエクスペリエンスを実現できます。

Adobe Experience Platform Location Service(Location Service)は、場所を認識するモバイルアプリで、柔軟な目標地点(POI)データベースを含む豊富で使いやすいSDKインターフェイスを使用して、場所のコンテキストを理解できるようにする地域サービスです。

ロケーションサービスを使用すると、次のことを実現できます。

* 他のAdobe Experience cloudソリューションで利用できるPOIのデータベースを作成し、管理します。
* カスタムメタデータをPOIに添付し、追加の属性を指定して、より豊かで意味のある情報を提供します。
* マップ上のPOIを視覚化して、空間的なコンテキストを理解し、メタデータ属性を追加/編集します。
* Adobe Experience Platform LaunchでSDKを設定し、場所でトリガーされるルールとメタデータに基づく条件を定義します。
* デバイスの場所を監視するために書き込む必要があるコードを減らし、場所拡張を使用して場所固有のルールを自動的にトリガーします。

これにより、位置信号が重要な場合や場所からリアルタイムにアクションを実行できます。 適切なコンテキストを使用すると、モバイルエンゲージメントのエクスペリエンスがより豊かになります。

場所の使用方法のいくつかを次に示します。

* 誰かがPOIに入ったら、リアルタイムで通知を *送信します。スタジアムへようこそ」*
* 自社の店舗と競合他社の店舗の足のトラフィックを分析する。
* 場所のコンテキストを持つオーディエンスプロファイルを使用して、オフラインの行動に基づいてオーディエンスをセグメント化します。
* 関連する場合は、店頭での体験を持つユーザーをターゲットにします。

## Location Serviceコンポーネント

ロケーションサービスは、次のコンポーネントで構成されます。

* **Webサービス**

   POIの作成と管理は、Places REST APIを使用して行うことができます。 REST APIについて詳しくは、ライブラリの管理とPOI [の管理](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md) を参 [照してください](/help/web-service-api/api-usage/manage-pois/manage-pois.md)。

* **POI管理インターフェイス**

   マップ上のPOIを視覚化して、空間的な状況を把握し、POIとそのカスタムメタデータを追加/編集します。

* **[配置]拡張子**

   モバイルアプリに位置コンテキストを統合するためのマルチプラットフォームモバイルAPIインターフェイス。 SDKについて詳しくは、場所拡張を参照 [してください](/help/places-ext-aep-sdks/places-extension/places-extension.md)。

* **ルールの起動**

   入口イベントと出口イベントでアクションをトリガーできる、地域インテリジェント起動ルール。 また、条件で地域属性を使用して、エクスペリエンスをパーソナライズすることもできます。

* **プレースモニタ拡張機能**

   モバイルアプリに埋め込んで、ユーザーの場所の変更を自動的に監視し、場所ルールをトリガーできるマルチプラットフォームモバイルSDK。 詳しくは、プレースモニター拡張機能 [を参照してください](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md)。

## 用語

このドキュメントで使用される一般的な用語を以下に示します。

* 目 **標地点(POI)は** 、組織が関心を持つ地域です。

   POIは、名前、半径、住所、カテゴリ、メタデータタグなどの属性を使用して定義できます。

* ジオフ **ェンスは** 、POIの一種である。

   このPOIタイプは、緯度と経度の座標で定義される仮想的な地理的境界です。

* ビー **コンは** 、POIの一種です。

   このPOIタイプは、低電力のBluetooth信号を発することで位置を表す物理デバイスです。 ビーコンのサポートは、今後のリリースで提供される予定です。

* ライ **ブラリ** はPOIの集まりで、1つのPOIではなくセットに簡単にルールを付加できるようにグループ化されています。

* 拡張機 **能とは** 、Places SDKをモバイルアプリに統合するために必要なExperience Platform Launch拡張機能です。

   他のモバイルSDKと共に使用する拡張機能で、エクスペリエンスに場所のコンテキストを追加します。

* 組織 **とは** 、Adobe Experience cloudで会社を識別するアドビのエンティティです。

   通常、組織は会社名です。 ただし、1つの会社に複数の組織を持つことはできます。 組織管理者は、グループとユーザーを設定し、シングルサインオン機能を設定できます。

* orgIDは **** 、Adobe Experience Platform全体で組織を表すIDです。

   詳しくは、orgIDの検索を参 [照してください](https://forums.adobe.com/thread/2339895)。

* The **Experience Cloud ID** service provides a universal, persistent ID that identifies your visitors across all the solutions in the Experience Cloud.

   For more information, see [Overview](https://docs.adobe.com/content/help/en/id-service/using/intro/overview.html).