---
title: プッシュ通知
description: この節では、Places Serviceをプッシュ通知で使用する方法を示します。
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 8%

---


# プッシュ通知

Mobile Servicesを使用すると、プッシュ通知をAdobe Analyticsセグメントに送信できます。 Places Serviceでは、POIとの過去のインタラクションを使用して、プッシュメッセージのオーディエンスをセグメント化できます。 例えば、過去30日間にストアにいたユーザーにメッセージを送信できます。

開始する前に、次のタスクが完了していることを確認します。

* プレースサービスのデータはAdobe Analyticsで処理されています。

   これは、モバイルアプリがPlaces Serviceデータをレポートスイートに正常に送信し、そのデータをセグメント化に使用できることを意味します。

* Mobile Servicesのプッシュ通知チャネルが設定されています。

   詳しくは、「[プッシュメッセージの作成](https://docs.adobe.com/content/help/en/mobile-services/using/manage-app-settings-ug/configuring-app/prerequisites-push-messaging.html)」を参照してください。

* Mobile ServicesのAnalyticsセグメントにプッシュ通知を送信する方法を説明します。

   詳しくは、「[プッシュメッセージの作成](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/push-messages/t-create-push-message.html)」を参照してください。

## 通知の送信

「プッシュ通知を **[!UICONTROL Audience]** 作成 ** 」ワークフローのタブでは、次のいずれかの方法で、このメッセージのオーディエンスを作成できます。

* ドロップダウン **[!UICONTROL Analytics Segments]** リストで、以前に作成したAdobe Analyticsセグメントを選択します。

* この節では、利用可能なカスタムセグメントパラメーターを使用してオーディエンスを作成します。 **[!UICONTROL Custom Segment]**

![プッシュメッセージの設定](/help/assets/push-set-up.png)
