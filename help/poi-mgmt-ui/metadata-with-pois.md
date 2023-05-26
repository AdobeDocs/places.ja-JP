---
title: POI でのメタデータの使用
description: この節では、POI でのメタデータの使用方法に関する情報と戦略を説明します。
exl-id: e669e560-a999-43ff-aeb4-06e6308b0d5c
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# POI でのメタデータの使用戦略 {#using-metadata-pois}

Places Service では、新しい POI を作成する際に必要な要素は、名前、半径、緯度、経度のみです。 POI の作成について詳しくは、 [POI の作成](/help/poi-mgmt-ui/create-a-poi-ui.md). ただし、最小値のみを入力している場合は、追加の値を作成する機会を逃します。

POI メタデータは様々な方法で使用できます。 POI 管理の観点から、メタデータ値を追加すると、潜在的に数千の POI のリストを検索またはフィルタリングするのに役立ちます。 POI に関連する主要属性のメタデータを作成すると、ダウンストリームワークフローで値を生み出すことができます。 例えば、各プロパティの POI を作成するホテルチェーンには、ホテルのプロパティにプールがあるかどうか、レストランとバー、ジムの施設がある場合などのメタデータを含めることができます。 このメタデータは、Analytics のコンテキストデータとして含めることができ、ターゲットオファーやメッセージにも使用できます。

## Launch での Places Service メタデータ

Experience Platform Launchでは、トラッキングやメッセージングの目的で重要な Places Service メタデータフィールドごとに、データ要素を作成できます。

![ジム施設のデータ要素](/help/assets/gymfacility.png)

その後、Analytics 拡張機能を使用して、コンテキストデータとして必要なメタデータを含む新しいヒットを作成するアクションを作成できます。

![体育館の施設に対する行動](/help/assets/Analytics-gym.png)

## Adobe Campaignのアプリ内メッセージ

メタデータは、Adobe Campaign Standardで定義されたローカル通知およびアプリ内メッセージのフィルターとして使用できます。 メタデータをフィルターとして使用すると、実際の場所に応じて、より関連性の高いメッセージを作成できます。

![ACS でのローカル通知とアプリ内メッセージのフィルタリング](/help/assets/ACS_gym_metadata.png)
