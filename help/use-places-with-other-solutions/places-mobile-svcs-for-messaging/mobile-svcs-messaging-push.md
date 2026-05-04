---
title: プッシュ通知
description: この節では、プッシュ通知でPlaces サービスを使用する方法について説明します。
exl-id: c094fe9c-6148-45ba-850a-f4c520d3362c
TQID: https://experienceleague.adobe.com/aaTMSoOkVUfbPDpPiRm7P3-8d8JSO9N0Ga12Hlmf-go
product_v2: id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: e55547f1-a1ff-40c6-8978-026e40ab7fa4id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2: id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2: id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2: id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 229
ht-degree: 14%

---

# プッシュ通知

Mobile Servicesでは、Adobe Analytics セグメントにプッシュ通知を送信できます。 Places サービスでは、POIとの過去のやり取りを使用して、プッシュメッセージのオーディエンスをセグメント化できます。 例えば、過去30日以内に店舗にアクセスしたことがあるユーザーにメッセージを送信できます。

開始する前に、次のタスクを完了していることを確認してください。

* Places サービス データはAdobe Analyticsによって処理されました。

  つまり、モバイルアプリがPlaces サービスデータをレポートスイートに正常に送信し、そのデータをセグメント化に利用できるようになりました。

* Mobile Servicesのプッシュ通知チャネルが設定されます。

  詳しくは、「[プッシュメッセージの作成](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.html?lang=ja)」を参照してください。

* Mobile ServicesのAnalytics セグメントにプッシュ通知を送信する方法について説明します。

  詳しくは、「[プッシュメッセージの作成](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.html?lang=ja)」を参照してください。

## 通知を送信

「*プッシュ通知を作成*」ワークフローの「**[!UICONTROL オーディエンス]**」タブでは、次のいずれかの方法でこのメッセージのオーディエンスを作成できます。

* 「**[!UICONTROL Analytics セグメント]**」ドロップダウンリストで、以前に作成したAdobe Analytics セグメントを選択します。

* **[!UICONTROL カスタムセグメント]** セクションで、使用可能なカスタムセグメントパラメーターを使用してオーディエンスを構築します。

![ プッシュメッセージの設定](/help/assets/push-set-up.png)
