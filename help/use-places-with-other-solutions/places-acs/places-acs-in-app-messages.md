---
title: Placesサービスを使用したアプリ内メッセージ
description: ここでは、Campaign Standardのアプリ内メッセージとCampaign Standardのキャンペーン標準のプッシュメッセージを使用する方法について説明します。
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b

---


# Placesサービスを使用したアプリ内メッセージ {#in-app-messages-loc-service}

この情報は、Places Service情報を使用してアプリ内メッセージやローカル通知を送信する方法を理解するのに役立ちます。

## 前提条件

開始する前に、次のタスクを実行します。

* Adobe Campaign Standard拡張機能を含む、Adobe Experience Platform Mobile SDKを使用して設定したモバイルアプリ [ケーションがある](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)。

* Adobe Experience Platform Mobile SDK [をアプリに統合します](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) 。
* モバイルア [プリ設定に](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) Adobe Campaign Standard Extensionを追加します。

* [Places Service POI管理インターフェイスでPOI](/help/poi-mgmt-ui/create-a-poi-ui.md) を作成します。

* モバイルアプリケーションに [Places拡張機能と](/help/places-ext-aep-sdks/places-extension/places-extension.md) Places Monitor拡張機能をイ [ンストールして設定します](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md) 。

## ジオフェンスの入口または出口に基づくアプリ内メッセージの送信

1. Adobe Campaign Standardインスタンスで、をクリックしま **[!UICONTROL Create In-App message]**す。
1. メッセージタイプに対して、を選択しま **[!UICONTROL Target all users of a Mobile application]**す。
1. をクリ **[!UICONTROL Next]**ックし、一般的な詳細を入力します。
1. 左側のウィンドウで、Places Servicesに関連する様々なトリガーを使用できることを確認します。

   * ユーザーがPOIジオフェンスを入力した場合、アプリ内メッセージを表示するように選択できます。
   * また、Places Services UIで定義されたメタデータを使用して、オーディエンスをフィルターすることもできます。
   以下の例では、無料飲料プログラムに参加している休暇リゾートに入ったユーザーにのみ表示されるアプリ内メッセージをトリガーし、それらのユーザーが到着したらクーポンを送信することができます。

   ![「アプリ内メッセージ配置メタデータ」](/help/assets/last-entered-vacation.png)

1. Click the **[!UICONTROL Next]**to finish creating the In-app message for delivery.

   ![「イベントの作成」](/help/assets/prepare-ACS.png)

   アプリ内メッセージ配信をテストするには、XcodeまたはAndroid studioでアプリケーションを起動し、場所シミュレーターを使用して、メッセージング条件に合うPOIを選択します。

   ![「クーポンを飲む」](/help/assets/drink-coupon-on-app.png)

Places ServicesをAdobe Campaign Standardと共に使用すると、地域フェンスの入口と出口に基づいて、ユーザーに対するメッセージをセグメント化およびターゲット化する強力なツールが提供されます。 この統合により、よりパーソナライズされたコンテキスト的な使用例を構築できます。

>[!VIDEO](https://www.youtube.com/watch?v=ikiTTQw9c-o)