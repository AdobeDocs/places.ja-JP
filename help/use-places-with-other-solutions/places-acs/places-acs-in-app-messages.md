---
title: Places Serviceを使用したアプリ内メッセージ
description: ここでは、Campaign Standard内のアプリ内メッセージとCampaign Standardしてプッシュメッセージを使用する方法について説明します。
translation-type: tm+mt
source-git-commit: 462df20bb351795dc72009cc18d390cb45e262a8
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 2%

---


# Places Serviceを使用したアプリ内メッセージ{#in-app-messages-loc-service}

この情報は、Places Service情報を使用して、アプリ内メッセージまたはローカル通知を送信する方法を理解するのに役立ちます。

## 前提条件

開始する前に、次のタスクを実行します。

* [Adobe Campaign Standard拡張子](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)を含む、Adobe Experience PlatformモバイルSDKを使用してモバイルアプリを設定します。

* [Adobe Experience PlatformモバイルSDK](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk)をアプリに統合します。
* モバ追加イルアプリ設定の[Adobe Campaign Standard拡張機能](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)。

* [Places Service POI管理インターフェイスで](/help/poi-mgmt-ui/create-a-poi-ui.md) POIを作成します。

* モバイルアプリケーションに[場所拡張子](/help/places-ext-aep-sdks/places-extension/places-extension.md)と[場所モニター拡張子](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md)をインストールして設定します。

## ジオフェンスの入口または出口に基づくアプリ内メッセージの送信

1. Adobe Campaign Standardインスタンスで、「**[!UICONTROL アプリ内メッセージを作成]**」をクリックします。
1. メッセージのタイプとして、「**[!UICONTROL モバイルアプリケーションのすべてのターゲット]**」を選択します。
1. 「**[!UICONTROL 次へ]**」をクリックし、一般的な詳細を入力します。
1. 左側のペインで、Places Servicesに関連する様々なトリガーを使用できることを確認します。

   * ユーザーがPOIジオフェンスを入力した場合、アプリ内メッセージを表示するように選択できます。
   * また、Places Services UIで定義されたメタデータを使用して、オーディエンスをフィルタリングすることもできます。

   以下の例では、無料飲料プログラムに参加している休暇中のリゾートに入ったユーザーのみに表示されるアプリ内メッセージをトリガーし、それらのユーザーが到着したらクーポンを送信することができます。

   ![「アプリ内メッセージ配置メタデータ」](/help/assets/last-entered-vacation.png)

1. 「**[!UICONTROL 次へ]**」をクリックして、配信用のアプリ内メッセージの作成を終了します。

   ![イベントの作成](/help/assets/prepare-ACS.png)

   アプリ内メッセージ配信をテストするには、XcodeまたはAndroid Studioでアプリケーションを起動し、場所シミュレーターを使用して、メッセージング条件に合うPOIを選択します。

   ![「クーポンを飲む」](/help/assets/drink-coupon-on-app.png)

Places ServicesをAdobe Campaign Standardと共に使用すると、地域フェンスの入口と出口に基づいてユーザーにメッセージを分類し、ターゲットするための強力なツールが提供されます。 この統合により、よりパーソナライズされた状況に応じた使用例を構築できます。

<!--I changed this embed to a link to pass validation. We should not link to youtube videos, so please upload this to MCP-->

[キャンペーンメッセージ付きAdobe Experience Platformロケーションサービス](https://www.youtube.com/watch?v=ikiTTQw9c-o)
