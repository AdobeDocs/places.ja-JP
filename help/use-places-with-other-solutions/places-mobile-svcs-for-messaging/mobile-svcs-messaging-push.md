---
title: プッシュ通知
description: この節では、プッシュ通知で Places Service を使用する方法について説明します。
exl-id: c094fe9c-6148-45ba-850a-f4c520d3362c
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 10%

---

# プッシュ通知

Mobile Services を使用すると、Adobe Analytics セグメントにプッシュ通知を送信できます。 Places Service では、POI との過去のインタラクションを使用して、プッシュメッセージのオーディエンスをセグメント化できます。 例えば、過去 30 日間にストアのいずれかに滞在しているユーザーにメッセージを送信できます。

開始する前に、次のタスクを完了していることを確認してください。

* Places Service のデータがAdobe Analyticsによって処理されました。

  つまり、モバイルアプリは Places Service のデータをレポートスイートに正常に送信し、データをセグメント化に使用できます。

* Mobile Services のプッシュ通知チャネルが設定されます。

  詳しくは、「[プッシュメッセージの作成](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.html?lang=ja)」を参照してください。

* Mobile Services の Analytics セグメントにプッシュ通知を送信する方法を説明します。

  詳しくは、「[プッシュメッセージの作成](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.html?lang=ja)」を参照してください。

## 通知の送信

**[!UICONTROL プッシュ通知を作成]** ワークフローの *オーディエンス* タブで、次のいずれかの方法でこのメッセージのオーディエンスを作成できます。

* **[!UICONTROL Analytics セグメント]** ドロップダウンリストで、以前に作成したAdobe Analytics セグメントを選択します。

* 「**[!UICONTROL カスタムセグメント]**」セクションで、使用可能なカスタムセグメントパラメーターを使用してオーディエンスを作成します。

![&#x200B; プッシュメッセージの設定 &#x200B;](/help/assets/push-set-up.png)
