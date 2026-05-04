---
title: アプリ内通知
description: この節では、アプリ内メッセージでPlaces サービスを使用する方法について説明します。
exl-id: c655e64b-0737-44d5-b453-2ac02fb9cbcc
TQID: https://experienceleague.adobe.com/Z39ybIytDRlCbkMthWjvk5F-oexy0C9gtqgK1mmyMxM
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
  - id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2:
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 689
ht-degree: 2%

---

# アプリ内通知 {#places-push-messaging}

次の情報では、Places Service イベントからトリガーするようにアプリ内メッセージを設定する方法を示します。

>[!IMPORTANT]
>
>メッセージはAnalytics ヒット上にある必要があります。

## アプリ内メッセージ

Mobile Servicesでは、Analyticsに送信されている位置情報を、アプリ内メッセージのトリガーイベントや条件として使用できます。 アプリ内メッセージがSDKから送信され、Analyticsでデータが処理されるのを待つ必要がない場合、トリガーが発生するとすぐにメッセージがリアルタイムで表示されます。

### ローカル通知

使用可能なアプリ内メッセージの種類のリストを次に示します。

* フルスクリーン
* アラート
* ローカル通知

これらはSDKによってトリガーされるため、アプリ内メッセージです。 ローカル通知は、アプリがバックグラウンドで表示されるため、プッシュ通知のように見えます。 また、アプリがバックグラウンドで動作しているときに、ユーザーがPOIに出入りするたびに、リアルタイムで通知が届きます。

### 前提条件

開始する前に、Mobile Servicesでアプリ内メッセージを送信および作成する方法と、トリガーの仕組みについて理解します。 詳しくは、[&#x200B; アプリ内メッセージの作成を参照してください。](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.html?lang=ja)

## Experience Platform Launchのルール

アプリ内メッセージトリガールールの一部として使用できるデータをAnalyticsに送信するExperience Platform Launch ルールを作成できます。 Experience Platform Launch ルールの場所の拡張機能のデータは、ユースケースに応じて、イベントまたは条件として使用できます。

* 位置情報をトリガーイベントとして使用し。

  例えば、ユーザーがPOIを入力したときにデータをAnalyticsに送信できます。

* 位置情報を条件として使用してイベントをトリガーします。

  例えば、異なるPOIの天気予報のPlaces サービスでカスタムメタデータタグを作成した場合、そのメタデータをルール条件のパラメーターとして使用できます。 この条件は、前述のPOI エントリイベントで使用できますが、条件を任意のイベントのコンテキストとして使用することもできます。

適切なイベントパラメーターと条件パラメーターを使用してルールを設定した後、Analyticsにデータを送信するアクションを設定してルール設定を完了します。

## アクションの作成

アクションを作成するには：

1. **[!UICONTROL Adobe Analytics]**&#x200B;拡張機能を選択します。
1. **[!UICONTROL アクションタイプ]** ドロップダウンリストで、**[!UICONTROL トラック]**&#x200B;を選択します。
1. アクションの名前を入力します。
1. 右側のペインで、**[!UICONTROL コンテキストデータ]**&#x200B;で、キーと値のペアを選択して、Analyticsに送信されるコンテキストデータを設定します。

例えば、キーとして`poiname`、値として`{%%Last Entered POI Name}`を選択できます。

>[!TIP]
>
>分析処理ルールを設定して、このコンテキストデータを取得できます。 詳しくは、[処理ルール &#x200B;](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/c-processing-rules/processing-rules.html)を参照してください。 *アクションの作成*&#x200B;の例では、アクションは、Analyticsに送信されるPOI エントリイベントを説明するコンテキストとして`poiname`を送信します。

![&#x200B; アクションの作成](/help/assets/configure-action.png)

完全なルールの例を次に示します。

![&#x200B; ルールを完了しました](/help/assets/create-a-rule.png)

## Mobile Servicesでのアプリ内メッセージの作成

トリガーパラメーターの一部として、次のいずれかの方法で、Places サービスのデータを使用してメッセージのオーディエンスを作成できます。

* エントリや離脱などの位置固有のアクションを使用します。
* コンテキストデータとして送信されるPOI メタデータを使用して、オーディエンスのターゲットを絞り込みます。

  このオプションは、エントリなどの位置固有のアクションで使用したり、ローンチやボタンのクリックなどの別のイベントのコンテキストとして使用したりできます。

  次に、名前に&#x200B;**[!UICONTROL Adobe]**&#x200B;が含まれるPOIを入力したユーザーを歓迎するようにアプリ内メッセージを設定する方法の例を示します。

  ![トリガーパラメーター](/help/assets/trigger-parameters.png)

* Mobile Servicesの&#x200B;*トリガーと特性* ページのPlaces サービス見出しのパラメーターは、Places サービスのデータでは機能しません。

  これらのパラメーターは、Mobile Servicesで作成された従来のPlaces Service データベースに対してのみ使用されます。
