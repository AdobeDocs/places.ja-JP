---
title: アプリ内通知
description: この節では、アプリ内メッセージで Places Service を使用する方法について説明します。
exl-id: c655e64b-0737-44d5-b453-2ac02fb9cbcc
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 2%

---

# アプリ内通知 {#places-push-messaging}

次の情報は、Places Service イベントからトリガーするアプリ内メッセージを設定する方法を示しています。

>[!IMPORTANT]
>
>メッセージは、Analytics ヒット上にある必要があります。

## アプリ内メッセージ

Mobile Services では、Analytics に送信される場所データをアプリ内メッセージのトリガーイベントや条件として使用できます。 アプリ内メッセージが SDK から発生し、Analytics によってデータが処理されるのを待つ必要がない場合は、トリガーが発生するとすぐに、メッセージがリアルタイムで表示されます。

### ローカル通知

使用可能なアプリ内メッセージタイプのリストを以下に示します。

* フルスクリーン
* アラート
* ローカル通知

これらのタイプは、SDK によってトリガーされるので、アプリ内メッセージです。 ローカル通知は、アプリがバックグラウンドにある場合に表示されるため、プッシュ通知のように見えます。 また、これらの通知は、アプリがバックグラウンドにある間に、ユーザーが POI に入ったり出たりしたときにリアルタイムの通知も配信します。

### 前提条件

開始する前に、Mobile Services でアプリ内メッセージを送信および作成する方法と、トリガーの仕組みについて理解します。 詳しくは、[ アプリ内メッセージの作成 ](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.html?lang=ja) を参照してください。

## Experience Platform Launchのルール

アプリ内メッセージExperience Platform Launchルールの一部として使用できるデータを Analytics に送信するトリガールールを作成できます。 Experience Platform Launchルールの Places 拡張機能のデータは、使用例に応じてイベントまたは条件（あるいはその両方）として使用できます。

* 場所データをトリガーイベントとして使用する。

  例えば、ユーザーが POI に入ったときに Analytics にデータを送信できます。

* 場所データをトリガーイベントの条件として使用する。

  例えば、様々な POI の天気に関するカスタムメタデータタグを場所サービスで作成した場合、そのメタデータをルール条件のパラメーターとして使用できます。 この条件は、前述の POI エントリイベントで使用できますが、任意のイベントのコンテキストとして使用することもできます。

ルールに適切なイベントパラメーターと条件パラメーターが設定されたら、Analytics にデータを送信するようにアクションを設定して、ルールの設定を完了します。

## アクションの作成

アクションを作成するには：

1. **[!UICONTROL Adobe Analytics]** 拡張機能を選択します。
1. **[!UICONTROL アクションタイプ]** ドロップダウンリストで、「**[!UICONTROL トラック]**」を選択します。
1. アクションの名前を入力します。
1. 右側のパネルの **[!UICONTROL コンテキストデータ]** で、キーと値のペアを選択して、Analytics に送信されるコンテキストデータを設定します。

例えば、キーとして `poiname` を選択し、値として `{%%Last Entered POI Name}` を選択できます。

>[!TIP]
>
>Analytics の処理ルールを設定すると、このコンテキストデータを取得できます。 詳しくは、[ 処理ルール ](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/c-processing-rules/processing-rules.html) を参照してください。 *アクションを作成* の例では、アクションは、Analytics に送信される POI エントリイベントを記述するコンテキストとして `poiname` を送信します。

![ アクションの作成 ](/help/assets/configure-action.png)

完全なルールの例を次に示します。

![ 完了したルール ](/help/assets/create-a-rule.png)

## Mobile Services でのアプリ内メッセージの作成

トリガーパラメーターの一部として、次のいずれかの方法で Places サービスからのデータを使用してメッセージのオーディエンスを作成できます。

* 入口や出口などの場所固有のアクションを使用します。
* コンテキストデータとして送信される POI メタデータを使用して、オーディエンスのターゲットを絞り込みます。

  このオプションは、エントリなどの場所固有のアクションと組み合わせて使用することも、ローンチやボタンクリックなどの別のイベントのコンテキストとして使用することもできます。

  次に、**[!UICONTROL Adobe]** が名前に含まれる POI に入ったユーザーを歓迎するアプリ内メッセージの設定方法の例を示します。

  ![トリガーパラメーター ](/help/assets/trigger-parameters.png)

* Mobile Services の *トリガーと特性* ページの Places Service 見出しのパラメーターは、Places Service からのデータでは機能しません。

  これらのパラメーターは、Mobile Services で作成された従来の Places Service データベースに対してのみ使用します。
