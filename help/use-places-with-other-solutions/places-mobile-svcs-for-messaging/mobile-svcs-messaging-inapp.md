---
title: アプリ内通知
description: この節では、Places Service とアプリ内メッセージの使用方法について説明します。
exl-id: c655e64b-0737-44d5-b453-2ac02fb9cbcc
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 3%

---

# アプリ内通知 {#places-push-messaging}

次の情報は、Places Service イベントからイベントに対してアプリ内トリガーを設定する方法を示しています。

>[!IMPORTANT]
>
>メッセージは、Analytics ヒットに含まれている必要があります。

## アプリ内メッセージ

Mobile Services では、Analytics に送信される場所データを、アプリ内メッセージのトリガーイベントや条件として使用できます。 アプリ内メッセージが SDK から実行され、Analytics でデータが処理されるのを待つ必要がない場合、トリガーが発生するとすぐにリアルタイムでメッセージが表示される可能性があります。

### ローカル通知

使用可能なアプリ内メッセージのタイプの一覧を次に示します。

* フルスクリーン
* アラート
* ローカル通知

これらのタイプは、SDK によってトリガーされるので、アプリ内メッセージです。 ローカル通知は、アプリがバックグラウンドになっているときに表示されるので、プッシュ通知のように見えます。 また、アプリがバックグラウンドになっている間にユーザーが POI に入るか POI を終了すると、これらの通知がリアルタイムで配信されます。

### 前提条件

開始する前に、Mobile Services でアプリ内メッセージを送信および作成する方法と、トリガーの動作について理解します。 詳しくは、 [アプリ内メッセージを作成します。](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/inapp-messages/t-in-app-message.html)

##  Experience Platform Launch でのルール

アプリ内Experience Platform Launchトリガールールの一部として Analytics に使用できるデータを送信するメッセージルールを作成できます。 使用事例に応じて、Experience Platform Launchルール内の Places 拡張機能のデータを、イベントや条件として使用できます。

* 位置データをトリガーイベントとして使用する。

   例えば、ユーザーが POI に入ると Analytics にデータを送信できます。

* 位置データをトリガーイベントの条件として使用する。

   例えば、様々な POI の天気に対して Places Service でカスタムメタデータタグを作成した場合、そのメタデータをルール条件のパラメーターとして使用できます。 この条件は、前述の POI エントリイベントで使用できますが、イベントに対するコンテキストとしても使用できます。

適切なイベントおよび条件パラメーターを使用してルールを設定したら、Analytics にデータを送信するアクションを設定して、ルールの設定を完了します。

## アクションの作成

アクションを作成するには：

1. を選択します。 **[!UICONTROL Adobe Analytics]** 拡張子。
1. 内 **[!UICONTROL アクションタイプ]** ドロップダウンリストで、「 **[!UICONTROL 追跡。]**
1. アクションの名前を入力します。
1. 右側のウィンドウで、 **[!UICONTROL コンテキストデータ]**」で、キー値ペアを選択して、Analytics に送信されるコンテキストデータを設定します。

例えば、 `poiname` をキーとして、 `{%%Last Entered POI Name}` を値として使用します。

>[!TIP]
>
>Analytics の処理ルールを設定して、このコンテキストデータを取得できます。 詳しくは、「[処理ルール](https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-processing-rules.html)」を参照してください。の例では、 *アクションの作成*&#x200B;を呼び出した場合、アクションは `poiname` Analytics に送信される POI エントリイベントを説明するコンテキストとして。

![アクションの作成](/help/assets/configure-action.png)

次に、完全なルールの例を示します。

![完了ルール](/help/assets/create-a-rule.png)

## Mobile Services でのアプリ内メッセージの作成

トリガーパラメーターの一部として、次のいずれかの方法で、Places Service からのデータを使用してメッセージのオーディエンスを作成できます。

* 入口や出口など、場所固有のアクションの使用。
* コンテキストデータとして送信される POI メタデータを使用して、オーディエンスのターゲットを絞り込みます。

   このオプションは、入口などの場所固有のアクションと共に使用することも、起動やボタンクリックなどの別のイベントへのコンテキストとして使用することもできます。

   以下は、 **[!UICONTROL Adobe]** 名前：

   ![トリガーパラメーター](/help/assets/trigger-parameters.png)

* Places Service の見出しのパラメーター ( *トリガーと特性* Mobile Services のページは、Places Service のデータでは動作しません。

   これらのパラメーターは、Mobile Services で作成された従来の Places Service データベースに対してのみ使用されます。
