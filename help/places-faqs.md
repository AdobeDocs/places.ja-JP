---
title: よくある質問
description: このトピックでは、よくある質問に関する追加情報を提供します。
exl-id: cee9f447-5e50-4ed8-b37b-baecbc0e9b7b
TQID: https://experienceleague.adobe.com/LL9eLMDJaq8ZmeiZxv28QZoqXL1A0QKZ-DvTDUx4Gnw
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
    internal-label: CX Enterprise
  - id: dc5cf79d-43c4-4731-bffa-1df5d7549cb1
    internal-label: Adobe Sign
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
feature_v2:
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
    internal-label: Data collection
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
    internal-label: Places
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
source-git-commit: d8704da9c84a066f72471421290d4b46c65f41e1
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 1%
---
# よくある質問

Places サービスに関するよくある質問と情報を次に示します。

## v4 SDKでのtrackLocationからの移行

v4 SDKから移行する場合に`trackLocation` APIへの置き換えを探している場合は、「[&#x200B; アクティブなリージョンモニタリングなしでPlaces サービスを使用する](use-places-without-active-monitoring.md)」を参照してください。

## サイズと信頼性

Adobeやその他のサービスを使用しているかどうかに関係なく、モバイルアプリからリージョンモニタリングで使用されているすべてのジオフェンスについて注意することが重要です。 オペレーティングシステムでは、ジオフェンスを作成する際に考慮すべきパラメーターを推奨しています。 最大限の信頼性を確保するために、ジオフェンスの半径は少なくとも100 メートルにする必要があります。 小さなジオフェンスでも構いませんが、入口と出口のイベントは生成されないか、ユーザーが一定期間動かなくなった後に生成されることがあります。

また、wi-fiがオフまたは利用できないハードウェアの状態、およびGPS信号の妨害に関連するデバイスの位置に基づいて、精度と信頼性が低下する場合があります。 たとえば、山間部、都市部、屋内部では、iOSとAndroidのオペレーティングシステムから位置情報の精度を低下させることができます。

## 離脱イベントのトリガー方法

実装されたリージョンモニターは、近くのPOIのリストを要求する必要があります。 受け取った領域は、POIごとにオペレーティングシステムに登録する必要があります。 デバイスが監視対象地域の1つに対して境界線（出入り）を越えた場合、オペレーティングシステムはSDKに通知する責任を負うようになりました。 SDKは、イベントが発生したことをオペレーティングシステムがSDKに通知する場合にのみ、終了イベントをトリガーします。 この通知の主な理由は、位置情報の時間的機密性です。

デバイスがリージョンを離れたときにオペレーティングシステムが終了イベントを配信できない場合は、SDKが終了イベントを省略するほうが安全です。 SDKがオペレーティングシステムによってトリガーされない離脱イベントを作成した場合、その離脱イベントは、デバイスがPOIに近い時間外に処理されるリスクがあります。

## POIの数

Places サービスのPOI管理インターフェイスでは、顧客は特定のライブラリに最大15万ポイントの関心を追加できます。 顧客は、必要に応じて、POIのグループ化をセグメント化するために複数のライブラリを定義できます。

## 場所の変更とアクティブな地域の監視に関する注意事項

地域のモニタリングは、許可されたアプリの登録直後から開始されます。 ただし、境界の交差点のみがイベントを生成するため、すぐにイベントを受け取ることは期待しないでください。 特に、登録時にユーザーの場所が既に領域内にある場合、位置情報マネージャーは自動的にイベントを生成しません。 代わりに、ユーザーが地域の境界を越えるのを待ってから、イベントが生成され、デリゲートに送信される必要があります。

監視する領域のセットを指定する場合は、慎重に行ってください。 リージョンは共有システムリソースであり、システム全体で使用可能なリージョンの合計数は制限されます。 このため、Core Locationは、1つのアプリで同時に監視できるリージョンの数を20に制限しています。 この制限を回避するには、ユーザーのすぐ近くにある領域のみを登録することを検討してください。

[Appleの開発者向けサイト ]に関する詳細情報を参照してください（https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/LocationAwarenessPG/RegionMonitoring/RegionMonitoring.html#//apple_ref/doc/uid/TP40009497-CH9-SW11）
