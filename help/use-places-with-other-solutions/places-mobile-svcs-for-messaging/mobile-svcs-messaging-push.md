---
title: プッシュメッセージ
seo-title: プッシュメッセージ
description: ここでは、プッシュメッセージングで場所を使用する方法について説明します。
seo-description: ここでは、プッシュメッセージングで場所を使用する方法について説明します。
translation-type: tm+mt
source-git-commit: accfa6ba009ad3419481d9bd3b498143228099fc

---


# プッシュ通知(#places-push-messaging)

プッシュ通知：AMSを使用すると、Adobe Analyticsセグメントにプッシュ通知を送信できます。 ロケーションサービスを使用すると、POIとの過去のインタラクションによって、プッシュメッセージのオーディエンスをセグメント化できます。 例えば、過去30日間にストアにいたユーザーにメッセージを送信できます。

開始する前に、次のタスクが完了していることを確認します。

* ロケーションサービスのデータがAdobe Analyticsで処理されました。

   つまり、モバイルアプリはロケーションサービスデータをReport suiteに正常に送信し、データをセグメント化できます。

* Mobile Servicesでプッシュ通知チャネルが設定されています。

   詳しくは、「[プッシュメッセージの作成](https://docs.adobe.com/content/help/en/mobile-services/using/manage-app-settings-ug/configuring-app/prerequisites-push-messaging.html)」を参照してください。

* Mobile ServicesのAnalyticsセグメントにプッシュ通知を送信する方法を理解します。

   * 詳しくは、「[プッシュメッセージの作成](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/push-messages/t-create-push-message.html)」を参照してください。

## 通知の送信

プッシュ通 **[!UICONTROL Audience]** 知を作成ワー *クフローのタブで* 、次のいずれかの方法でこのメッセージのオーディエンスを作成できます。

* 以前に作成したAdobe Analyticsセグメントを選択します。

* 使用可能なカスタムセグメントパラメーターを使用してオーディエンスを作成します。

![プッシュメッセージの設定](/help/assets/push-set-up.png)

