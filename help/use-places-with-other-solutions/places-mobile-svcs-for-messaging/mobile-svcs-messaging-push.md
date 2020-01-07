---
title: プッシュ通知
description: ここでは、プッシュ通知で場所を使用する方法について説明します。
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# プッシュ通知

Mobile Servicesを使用すると、Adobe Analyticsセグメントにプッシュ通知を送信できます。 ロケーションサービスでは、POIとの過去のインタラクションを使用して、プッシュメッセージのオーディエンスをセグメント化できます。 例えば、過去30日間にストアにいたユーザーにメッセージを送信できます。

開始する前に、次のタスクが完了していることを確認します。

* ロケーションサービスのデータがAdobe Analyticsで処理されました。

   これは、モバイルアプリがロケーションサービスのデータをReport suiteに正常に送信し、そのデータをセグメント化に使用できることを意味します。

* Mobile Servicesでプッシュ通知チャネルが設定されています。

   詳しくは、「[プッシュメッセージの作成](https://docs.adobe.com/content/help/en/mobile-services/using/manage-app-settings-ug/configuring-app/prerequisites-push-messaging.html)」を参照してください。

* Mobile ServicesのAnalyticsセグメントにプッシュ通知を送信する方法を説明します。

   詳しくは、「[プッシュメッセージの作成](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/push-messages/t-create-push-message.html)」を参照してください。

## 通知の送信

プッシュ通 **[!UICONTROL Audience]**知を作成ワー&#x200B;*クフローのタブで*、次のいずれかの方法でこのメッセージのオーディエンスを作成できます。

* ドロップダ **[!UICONTROL Analytics Segments]**ウンリストで、以前に作成したAdobe Analyticsセグメントを選択します。

* このセクション **[!UICONTROL Custom Segment]**では、利用可能なカスタムセグメントパラメーターを使用してオーディエンスを作成します。

![プッシュメッセージの設定](/help/assets/push-set-up.png)
