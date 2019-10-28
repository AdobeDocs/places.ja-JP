---
title: ロケーションサービスを使用したアプリ内メッセージ
seo-title: ロケーションサービスを使用したアプリ内メッセージ
description: ここでは、Campaign Standardのアプリ内メッセージとCampaign Standardのキャンペーン標準のプッシュメッセージを使用する方法について説明します。
seo-description: 'ここでは、Campaign Standardのアプリ内メッセージで「Campaign Standardのプッシュメッセージ」を使用する方法について説明します。 '
translation-type: tm+mt
source-git-commit: fd98249c01fba93250dc7111798c76f3c96c6e20

---


# ロケーションサービスを使用したアプリ内メッセージ {#in-app-messages-loc-service}

この情報は、Adobe Experience Platform Location Service情報を使用して、アプリ内メッセージまたはローカル通知を送信する方法を理解するのに役立ちます。

>[!IMPORTANT]
>
>開始する前に、次のタスクを実行します。
>
>* Adobe Campaign Standard拡張機能を含む、Adobe Experience Platform Mobile SDKを使用して設定したモバイルアプリ [ケーションがある](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)。
   >
   >
* Adobe Experience Platform Mobile SDK [をアプリに統合します](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) 。
>* モバイルア [プリ設定に](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) Adobe Campaign Standard Extensionを追加します。
   >
   >
* [場所POI管理インターフェイスで](/help/poi-mgmt-ui/create-a-poi-ui.md) 、POIを作成します。
   >
   >
* モバイルアプリケーションに [Places拡張機能と](/help/places-ext-aep-sdks/places-extension/places-extension.md) Places Monitor拡張機能をイ [ンストールして設定します](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md) 。


## ジオフェンスの入口または出口に基づくアプリ内メッセージの送信

1. Adobe Campaign Standardインスタンスで、をクリックしま **[!UICONTROL Create In-App message]**&#x200B;す。
2. メッセージタイプに対して、を選択しま **[!UICONTROL Target all users of a Mobile application]**&#x200B;す。
3. をクリ **[!UICONTROL Next]** ックし、一般的な詳細を入力します。
4. 左側のウィンドウで、ロケーションサービスに関連する様々なトリガーを使用できることを確認します。

   * ユーザーがPOIジオフェンスを入力した場合、アプリ内メッセージを表示するように選択できます。
   * また、ロケーションサービスUIで定義されたメタデータを使用して、オーディエンスをフィルターすることもできます。
   次の図の例では、無料飲料プログラムに参加している休暇リゾートに入ったユーザーにのみ表示されるアプリ内メッセージをトリガーし、ユーザーが到着したらクーポンを送信することができます。

   ![「アプリ内メッセージ配置メタデータ」](/help/assets/last-entered-vacation.png)

5. をクリックし **[!UICONTROL Next]** て、配信するアプリ内メッセージの作成を終了します。

   ![「イベントの作成」](/help/assets/prepare-ACS.png)

   アプリ内メッセージ配信をテストするには、XcodeまたはAndroid studioでアプリケーションを起動し、場所シミュレーターを使用して、メッセージング条件に合うPOIを選択します。

   ![「クーポンを飲む」](/help/assets/drink-coupon-on-app.png)


Location ServicesをAdobe Campaign Standardと共に使用すると、地域フェンスの入口と出口に基づいて、ユーザーに対するメッセージをセグメント化およびターゲット化する強力なツールが提供されます。 このシンプルな統合により、よりパーソナライズされた状況に応じた使用例を構築できます。

## 場所メタデータに基づいてCampaign Standardで異なるトリガーを作成する

（この情報は今後表示されますか？）