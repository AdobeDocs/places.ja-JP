---
title: アプリ内通知
description: この節では、Places Serviceとアプリ内メッセージを使用する方法を示します。
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b

---


# アプリ内通知 {#places-push-messaging}

次の情報は、Places Serviceイベントからトリガーするアプリ内メッセージを設定する方法を示しています。

>[!IMPORTANT]
>
>メッセージは、Analyticsヒットに含まれている必要があります。

## アプリ内メッセージ

Mobile Servicesでは、Analyticsに送信される場所データを、アプリ内メッセージのトリガーイベントや条件として使用できます。 アプリ内メッセージがSDKから呼び出され、Analyticsでデータが処理されるのを待つ必要がない場合、トリガーが発生するとすぐにリアルタイムでメッセージが表示される可能性があります。

### ローカル通知

利用可能なアプリ内メッセージのタイプを以下に示します。

* フルスクリーン
* アラート
* ローカル通知

これらのタイプはSDKによってトリガーされるので、アプリ内メッセージです。 ローカル通知は、アプリがバックグラウンドにあるときに表示されるので、プッシュ通知のような外観と雰囲気がします。 また、アプリがバックグラウンドにある間、ユーザーがPOIに入るかPOIから出ると、これらの通知はリアルタイムで通知されます。 詳しくは、プレースモニター拡張 [機能を参照してください](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md)。

### 前提条件

始める前に、Mobile Servicesでのアプリ内メッセージの送信および作成方法とトリガーの動作を理解しておきます。 For more information, see [Create an in-app message.](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/inapp-messages/t-in-app-message.html)

##  Experience Platform Launch でのルール

アプリ内メッセージのトリガールールの一部としてAnalyticsに使用できるデータを送信するExperience Platform起動ルールを作成できます。 エクスペリエンスプラットフォーム起動ルール内の場所拡張のデータは、使用事例に応じて、イベントや条件として使用できます。

* トリガーイベントとしての場所データの使用。

   例えば、ユーザーがPOIに入ったときにAnalyticsにデータを送信できます。

* トリガーイベントに対する条件として位置データを使用する。

   例えば、異なるPOIの天候に対応するカスタムメタデータタグをPlaces Serviceに作成した場合、そのメタデータをルール条件のパラメーターとして使用できます。 前述のPOIエントリイベントでこの条件を使用することもできますが、この条件を任意のイベントのコンテキストとして使用することもできます。

適切なイベントおよび条件パラメーターを使用してルールを設定したら、Analyticsにデータを送信するアクションを設定して、ルールの設定を完了します。

## アクションの作成

アクションを作成するには：

1. **[!UICONTROL Adobe Analytics]**拡張機能を選択します。
1. ドロップダ **[!UICONTROL Action type]**ウンリストで、「**[!UICONTROL Track.]**
1. アクションの名前を入力します。
1. 右側のウィンドウので、キ **[!UICONTROL Context Data]**ーと値のペアを選択し、Analyticsに送信するコンテキストデータを設定します。

例えば、キーとしてを選択し、 `poiname` 値としてを選択する `{%%Last Entered POI Name}` ことができます。

>[!TIP]
>
>Analytics処理ルールを設定して、このコンテキストデータを取得できます。 詳しくは、「[処理ルール](https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-processing-rules.html)」を参照してください。「アクションの作 *成」の例では*、Analyticsに送信されるPOIエントリイベントを説明するコンテキストと `poiname` して、アクションがを送信します。

![アクションの作成](/help/assets/configure-action.png)

次に、完全なルールの例を示します。

![完了規則](/help/assets/create-a-rule.png)

## Mobile Servicesでのアプリ内メッセージの作成

Triggerパラメーターの一部として、次のいずれかの方法で、Places Serviceのデータを使用してメッセージのオーディエンスを作成できます。

* 入口や出口など、場所に固有のアクションを使用する。
* コンテキストデータとして送信されるPOIメタデータを使用して、オーディエンスのターゲットを絞り込みます。

   このオプションは、入口など場所に固有のアクションで使用したり、起動やボタンクリックなど、別のイベントへのコンテキストとして使用したりできます。

   名前にPOIを入力するユーザーを迎え入れるアプリ内メッセージを設定する方法の例を次に **[!UICONTROL Adobe]**示します。

   ![トリガパラメータ](/help/assets/trigger-parameters.png)

* Mobile Servicesのトリガーと特徴ページの「Places Service」見出し *のパラメーターは* 、Places Serviceのデータを使用できません。

   これらのパラメーターは、Mobile Servicesで作成された従来のPlaces Serviceデータベースに対してのみ使用されます。