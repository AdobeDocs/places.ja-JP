---
title: POI でのメタデータの使用
description: この節では、POI でメタデータを使用する方法に関する情報と戦略について説明します。
exl-id: e669e560-a999-43ff-aeb4-06e6308b0d5c
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# POI でメタデータを使用するための戦略 {#using-metadata-pois}

Places Service で新しい POI を作成する場合、必要な要素は名前、半径、緯度、経度のみです。 POI の作成について詳しくは、[POI の作成 ](/help/poi-mgmt-ui/create-a-poi-ui.md) を参照してください。 ただし、最小情報のみを入力している場合は、追加の値を作成する機会を逃すことになります。

POI メタデータは様々な方法で使用できます。 POI 管理の観点からは、メタデータ値の追加は、何千もの可能性がある POI のリストの検索またはフィルタリングに役立ちます。 POI に関連するキー属性のメタデータを作成すると、ダウンストリームワークフローに価値を生み出すことができます。 例えば、各プロパティの POI を作成するホテルチェーンは、ホテルプロパティにプールがあるかどうか、レストランやバー、ジム施設があるかどうかなどのメタデータを含める必要がある場合があります。 このメタデータは、Analytics にコンテキストデータとして含めることができ、ターゲットオファーやメッセージングに使用することもできます。

## Launch へのサービスメタデータの配置

Experience Platform Launchでは、トラッキングやメッセージングの目的で重要な各 Places Service メタデータフィールドに対して、データ要素を作成できます。

![ 体育館のデータ要素 ](/help/assets/gymfacility.png)

その後、Analytics 拡張機能を使用してアクションを作成し、コンテキストデータとして希望するメタデータを含む新しいヒットを作成できます。

![ 体育館施設におけるアクション ](/help/assets/Analytics-gym.png)

## Adobe Campaignでのアプリ内メッセージ

メタデータは、Adobe Campaign Standardで定義されたローカル通知およびアプリ内メッセージのフィルターとして使用できます。 メタデータをフィルターとして使用すると、実際の場所に応じた、より関連性の高いメッセージを作成できます。

![ACS でのローカル通知およびアプリ内メッセージのフィルタリング ](/help/assets/ACS_gym_metadata.png)
