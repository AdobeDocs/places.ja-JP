---
title: プッシュ通知
description: この節では、Places Service でプッシュ通知を使用する方法について説明します。
exl-id: c094fe9c-6148-45ba-850a-f4c520d3362c
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 8%

---

# プッシュ通知

Mobile Services を使用すると、Adobe Analyticsセグメントにプッシュ通知を送信できます。 Places Service では、POI との過去のインタラクションを使用して、プッシュメッセージのオーディエンスをセグメント化できます。 例えば、過去 30 日間にいずれかの店舗にいたユーザーにメッセージを送信できます。

開始する前に、次の作業を完了していることを確認します。

* Places Service のデータがAdobe Analyticsで処理されました。

  つまり、モバイルアプリは Places Service のデータをレポートスイートに正常に送信し、そのデータをセグメント化に使用できることを意味します。

* Mobile Services でプッシュ通知チャネルが設定されています。

  詳しくは、「[プッシュメッセージの作成](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.html)」を参照してください。

* Mobile Services で Analytics セグメントにプッシュ通知を送信する方法を説明します。

  詳しくは、「[プッシュメッセージの作成](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.html)」を参照してください。

## 通知を送信

次の日： **[!UICONTROL 対象ユーザ]** タブ *プッシュ通知の作成* ワークフローでは、次のいずれかの方法で、このメッセージのオーディエンスを作成できます。

* Adobe Analytics の **[!UICONTROL Analytics セグメント]** ドロップダウンリストから、以前に作成したAdobe Analyticsセグメントを選択します。

* Adobe Analytics の **[!UICONTROL カスタムセグメント]** の節では、使用可能なカスタムセグメントパラメーターを使用してオーディエンスを作成します。

![プッシュメッセージの設定](/help/assets/push-set-up.png)
