---
title: 'Adobe Experience Platform Location Serviceへのアクセス '
description: ここでは、ユーザーがロケーションサービスにアクセスできるように、ロケーションサービスとExperience Platformの起動にユーザーを追加する方法について説明します。
translation-type: tm+mt
source-git-commit: e5d6c7f9ad1e2c9c37c1537aadc309ee20757156

---

# ロケーションサービスにアクセスする {#adding-user-launch-places}

プラットフォームロケーションサービスには、 [Adobe Experience cloudホームのクイックアクセスメニューからアクセスできます](https://experience.adobe.com)。
ユーザーIDにアクセス権がある場合は、次に示すように「ロケーションサービス」アイコンが表示されます。

![クイックアクセスメニュー](/help/assets/quick-access.png)

Adobe Experience Platformメニューからも、プラットフォームロケーションサービスにアクセスできます。

![エクスペリエンスプラットフォームメニュー](/help/assets/exp-platform-menu-sm.png)

これらのメニューにプラットフォームロケーションサービスが表示されない場合は、組織内の管理者に問い合わせて、管理コンソールのPlacesコアサービスにユーザーIDを追加する必要があります。

## ロケーションサービスとExperience Platformの起動へのユーザーの追加

ユーザーが「サービスの起動」UI [にアクセスできるようにするには](https://places.adobe.com)、ユーザーとして管理コンソールの「Placesコアサービス」に追加する必要があります。 ユーザーがエクスペリエンスプラットフォーム起動へのアクセス権を持ち、モバイルプロパティを設定し、Adobe Experience Platform SDKで場所を使用できるようにするには、管理コンソールのエクスペリエンスプラットフォーム起動に追加し、エクスペリエンスプラットフォーム起動に関する次の権限を与える必要があります。

* All Property Rights:
   * 開発
   * 承認
   * 投稿
   * 拡張機能の管理
   * 環境の管理
* 「会社権限」の下の「プロパティの管理」権限

初めてユーザーを追加する場合は、次の手順を実行して、Experience Platform Launch and Location Serviceにユーザーを追加します。 以前にユーザーを追加したことがある場合は、複数のプロファイルが表示される可能性があるので、必ず正しいプロファイルを選択してください。

>[!IMPORTANT]
>
>組織の管理者のみが管理コンソールにアクセスし、ユーザーを追加できます。

### 1.ロケーションサービスとExperience Platformの起動がプロビジョニングされていることを確認します。

ロケーションサービスとExperience Platformの起動がプロビジョニングされていることを確認するには：

1. Experience cloud組織にログインします。
1. 右上部で、Experience cloudシェルスイッチャーをクリックします。

   ![シェルスイッチャー](/help/assets/places_shell_switcher1.png)

1. **[!UICONTROL Platform]**の下で、「**[!UICONTROL Administration]**」をクリックします。

   リストに「管理」が **表示されない場合** 、管理者ではありません。 この手順を完了するには、組織の管理者に問い合わせる必要があります。

1. Experience cloud管理ページのカードで、をク **[!UICONTROL Admin Console]**リックします**[!UICONTROL Take me there]**。

1. 管理コンソールで、複数の組織にアクセスできる場合は、ページの右上部で正しい組織が選択されていることを確認します。

   これは、ユーザーを追加する組織です。 正しい組織が選択されていない場合は、組織をクリックし、ドロップダウンリストから組織を選択します。

   >[!IMPORTANT]
   >
   >組織へのアクセス権がない場合は、その組織への管理者アクセス権がないことを意味します。

1. およびのカードが表示され **[!UICONTROL Adobe Experience Platform Launch]**ているこ**[!UICONTROL Places Core Services]** とを確認します。

   ![](/help/assets/places_provisioned1.png)

   表示された場合は、ロケーションサービスとエクスペリエンスプラットフォームの起動が組織用にプロビジョニングされています。 表示されない場合は、組織のプロビジョニングが必要です。


### 2.プロファイルの設定と権限の追加

プロファイルを設定し、権限を追加するには：

1. エクスペリエンスプラットフォーム起動プロファイルを設定します。これにより、プロファイルに追加されたユーザーは、エクスペリエンスプラットフォーム起動と、エクスペリエンスプラットフォームSDKのモバイルプロパティを使用できます。

   a.メニューバーで、をクリックしま **[!UICONTROL Product]**す。

   b.左側のウィンドウの製品リストで、をクリックします **[!UICONTROL Adobe Experience Platform Launch]**。

   * エクスペリエンスプラットフォーム起動プロファイルが右側に表示されます。
   * エクスペリエンスプラットフォームの起動には、起動 — （組織名） *と呼ばれるデフォルトのプロファイルがありま* す。

      以前にエクスペリエンスプラットフォームの起動にユーザーを追加した場合は、複数のプロファイルが表示される場合があります。

1. 正しいプロファイルを選択します。

   a.デフォルトのプロファイルの名前をクリックします。

   b.タブをクリック **[!UICONTROL Permissions]**します。

   c.の横にあ **[!UICONTROL Edit]**るをクリックしま**[!UICONTROL Property Rights]**&#x200B;す。

   d.左側のウィンドウで、をクリックしま **[!UICONTROL + Add all]**す。

   この手順では、使用可能なすべての権限が、含まれる権限リストに移動されます。

   e.をクリックし **[!UICONTROL Company Rights]**ます。

   f.左側のウィンドウで、をクリックしま **[!UICONTROL + Manage Properties]**す。

   g.をクリックし **[!UICONTROL Save]**ます。

>[!IMPORTANT]
>
>ロケーションサービスの場合は、デフォルトのプロファイルがありますが、権限を追加する必要はありません。

作成したプロファイルに権限が正常に追加されました。

### 3.ロケーションサービスおよびExperience Platform Launchプロファイルへのユーザーまたは開発者の追加

ロケーションサービスおよびエクスペリエンスプラットフォーム起動プロファイルに、ユーザーまたは開発者を追加できます。

### ユーザーの追加

ロケーションサービスおよびエクスペリエンスプラットフォーム起動プロファイルにユーザーを追加するには：

1. エクスペリエンスプラットフォーム起動プロファイルにユーザーを追加します。

   a.メニューバーで、をクリックしま **[!UICONTROL Overview]**す。

   b.カード上で、 **[!UICONTROL Adobe Experience Platform Launch]**次の内容を確認します。

   * カードの下部に2つのドットが表示されます。
   * 左の点は黒です。

      右側のドットが黒の場合は、開発者のみを追加できます。 ユーザーを追加するには、左側の点をクリックします。
   c.をクリックし **[!UICONTROL + Add Users]**ます。

   d.ユーザーのAdobe IDを入力します。

   e.次のいずれかの手順を実行します。

   * 新しいユーザーを追加する場合は、をク **[!UICONTROL New user]**リックし、ユーザーの姓と名を入力します。
   * 既存のユーザーを追加する場合は、表示されるユーザーの名前をクリックします。
   f.ドロップダ **[!UICONTROL Please select a profile for this product]**ウンリストで、前に編集したプロファイルを選択します。

   g.をクリックし **[!UICONTROL Save]**ます。

1. にユーザーを追加しま **[!UICONTROL Places Core Services]**す。

   >[!TIP]
   >
   >現在、すべてのLocation Serviceユーザーに同じ権限が与えられているので、権限を編集する必要はありません。

   a.カード上で、 **[!UICONTROL Places Core Services]**次の内容を確認します。

   * カードの下部に2つのドットが表示されます。
   * 左の点は黒です。
   b.をクリックし **[!UICONTROL + Assign Users]**ます。

   c.ユーザーのAdobe IDを入力します。

   d.次のいずれかの手順を実行します。

   * 新しいユーザーを追加する場合は、をク **[!UICONTROL New user]**リックし、ユーザーの姓と名を入力します。
   * 既存のユーザーを追加する場合は、表示されるユーザーの名前をクリックします。
   e.ドロップダウ **[!UICONTROL Please select a profile for this product]**ンリストで、Placesプロファイルを選択します。

   f.をクリックし **[!UICONTROL Save]**ます。

### 開発者の追加

Web Service APIへのアクセスも必要なユーザーの場合は、開発者として追加する必要があります。

開発者を追加するには：

1. On the **[!UICONTROL Places Core Services]**card, verify the following:

   * カードの下部に2つのドットが表示されます。
   * カードの下部に表示される右 **[!UICONTROL Assign Developers]**側の点をクリックします。

1. **[!UICONTROL + Assign Developers]**をクリックします。

1. ユーザーの Adobe ID を入力します。

1. 次のいずれかの手順を実行します。

   * 新しいユーザーを追加する場合は、をクリック **[!UICONTROL New user]**し、ユーザーの姓と名を入力します。
   * 既存のユーザーを追加する場合は、表示されるユーザーの名前をクリックします。

1. ドロップダウ **[!UICONTROL Please select a profile for this product]**ンリストで、Location Serviceプロファイルを選択します。

1. 「**保存**」をクリックします。

ユーザーには、Experience Platform Launch へのアクセス権があることを通知する電子メールが届きます。ユーザーは、この組織の [Experience Platform Launch](https://launch.adobe.com) または [Places](https://places.adobe.com) UI にログインできます。「**開発者の追加**」手順の手順 4 を完了すると、ユーザーは [Adobe I/O コンソール](https://console.adobe.io)にログインして、Places 統合を作成し、Places REST API を使用することもできます。
