---
title: アプリ内通知
description: この節では、Places Serviceとアプリ内メッセージを使用する方法を示します。
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '660'
ht-degree: 3%

---


# アプリ内通知 {#places-push-messaging}

次の情報は、Places Serviceイベントからトリガーされるアプリ内メッセージを設定する方法を示しています。

>[!IMPORTANT]
>
>メッセージは、Analyticsヒットに含まれている必要があります。

## アプリ内メッセージ

Mobile Servicesでは、Analyticsに送信される場所データを、アプリ内メッセージのトリガーイベントや条件として使用できます。 アプリ内メッセージがSDKから呼び出され、Analyticsでデータが処理されるのを待つ必要がない場合、トリガーが発生するとすぐに、リアルタイムでメッセージが表示される可能性があります。

### ローカル通知

以下に、利用可能なアプリ内メッセージのタイプのリストを示します。

* フルスクリーン
* アラート
* ローカル通知

これらのタイプは、SDKによってトリガーされるアプリ内メッセージです。 ローカル通知は、アプリがバックグラウンドにあるときに表示されるので、プッシュ通知のように見えます。 また、これらの通知は、アプリがバックグラウンドにある間、ユーザーがPOIに入るかPOIから出るときに、リアルタイム通知を配信します。 詳しくは、「 [配置モニター拡張機能](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md)」を参照してください。

### 前提条件

開始する前に、Mobile Servicesでアプリ内メッセージを送信および作成する方法とトリガーの動作について理解しておきます。 For more information, see [Create an in-app message.](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/inapp-messages/t-in-app-message.html)

##  Experience Platform Launch でのルール

アプリ内Experience Platform Launchのトリガールールの一部として使用できるデータをAnalyticsに送信するメッセージルールを作成できます。 Experience Platform Launchルール内の「配置」拡張のデータは、使用事例に応じたイベントや条件として使用できます。

* トリガーイベントとしての位置データの使用。

   例えば、ユーザーがPOIに入るとAnalyticsにデータを送信できます。

* 位置データをトリガーするイベントに対する条件として使用する。

   例えば、異なるPOIの天気に対応するカスタムメタデータタグをPlaces Serviceに作成した場合、そのメタデータをルール条件のパラメーターとして使用できます。 前述のPOIエントリイベントでこの条件を使用できますが、イベントのコンテキストとしてこの条件を使用することもできます。

適切なイベントと条件のパラメーターを使用してルールを設定したら、Analyticsにデータを送信するようにアクションを設定して、ルールの設定を完了します。

## アクションの作成

アクションを作成するには：

1. **[!UICONTROL Adobe Analytics]** 拡張機能を選択します。
1. In the **[!UICONTROL Action type]** drop-down list, select **[!UICONTROL Track.]**
1. アクションの名前を入力します。
1. 右側のウィンドウので、キーと値のペアを選択 **[!UICONTROL Context Data]**&#x200B;し、Analyticsに送信されるコンテキストデータを設定します。

例えば、キーとしてを選択し、値 `poiname` としてを選択す `{%%Last Entered POI Name}` ることができます。

>[!TIP]
>
>Analytics処理ルールを設定して、このコンテキストデータを取得できます。 詳しくは、「[処理ルール](https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-processing-rules.html)」を参照してください。「アクションの *作成*」の例では、アクションは、Analyticsに送信されるPOIエントリイベント `poiname` を説明するコンテキストとしてを送信します。

![アクションの作成](/help/assets/configure-action.png)

次に、完全なルールの例を示します。

![完了規則](/help/assets/create-a-rule.png)

## Mobile Servicesでのアプリ内メッセージの作成

Triggerパラメーターの一部として、次のいずれかの方法で、Places Serviceのデータを含むメッセージのオーディエンスを作成できます。

* 入口や出口など、場所に固有のアクションの使用。
* コンテキストデータとして送信されるPOIメタデータを使用して、オーディエンスのターゲットを絞り込みます。

   このオプションは、エントリなど場所に固有のアクションで使用したり、起動やボタンクリックなど、別のイベントへのコンテキストとして使用したりできます。

   名前にPOIを入力するユーザーを歓迎するアプリ内メッセージを設定する方法の例を次に示 **[!UICONTROL Adobe]** します。

   ![トリガパラメータ](/help/assets/trigger-parameters.png)

* Mobile Servicesの *トリガーおよび特性* ページのPlaces Serviceの見出しにあるパラメーターは、Places Serviceのデータを使用できません。

   これらのパラメーターは、Mobile Servicesで作成された従来のPlaces Serviceデータベースに対してのみ使用されます。