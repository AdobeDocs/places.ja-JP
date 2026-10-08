---
title: POIでのメタデータの使用
description: この節では、POIでメタデータを使用する方法に関する情報と戦略について説明します。
exl-id: e669e560-a999-43ff-aeb4-06e6308b0d5c
TQID: https://experienceleague.adobe.com/wTzahAs7MMSv0q-cEhkNObBpALUJXqDXlOcqjitezwY
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
    internal-label: CX Enterprise
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
    internal-label: Target
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
    internal-label: Analytics
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
feature_v2:
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
    internal-label: Data collection
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
    internal-label: Places
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
    internal-label: Metadata
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
source-git-commit: d8704da9c84a066f72471421290d4b46c65f41e1
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%
---
# POIでメタデータを使用するための戦略 {#using-metadata-pois}

Places サービスでは、新しいPOIを作成するときに、必要な要素は名前、半径、緯度、経度のみです。 POIの作成について詳しくは、[POIの作成](/help/poi-mgmt-ui/create-a-poi-ui.md)を参照してください。 しかし、最小限の情報しか入力できなければ、新たな価値を生み出す機会を逃すことになります。

POI メタデータは、様々な方法で使用できます。 POI管理の観点から、メタデータ値を追加すると、潜在的に何千ものPOIのリストを検索またはフィルタリングするのに役立ちます。 POIに関連する主要属性のメタデータを作成することで、下流のワークフローで価値を生み出すことができます。 たとえば、各宿泊施設のPOIを作成するホテルチェーンでは、ホテルの宿泊施設にプールがあるかどうか、レストランやバーがあるかどうか、ジム施設があるかどうかなどのメタデータを含めることができます。 このメタデータは、Analyticsにコンテキストデータとして含めることができ、ターゲットを絞ったオファーやメッセージにも使用できます。

## Launchにサービスメタデータを配置する

Experience Platform Launchでは、トラッキングやメッセージの目的で重要なPlaces サービスのメタデータフィールドごとにデータ要素を作成できます。

![ ジム施設のデータ要素](/help/assets/gymfacility.png)

次に、Analytics拡張機能を使用して、コンテキストデータとして必要なメタデータを含む新しいヒットを作成するためのアクションを作成できます。

![ ジム施設のアクション ](/help/assets/Analytics-gym.png)

## Adobe Campaignでのアプリ内メッセージ

メタデータは、Adobe Campaign Standardで定義されたローカル通知やアプリ内メッセージのフィルターとして使用できます。 メタデータをフィルターとして使用することで、実際の場所に関連したより適切なメッセージを作成できます。

![ ローカル通知とアプリ内メッセージをACS](/help/assets/ACS_gym_metadata.png)でフィルタリング
