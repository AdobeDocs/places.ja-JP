---
title: 'Placesサービスへのアクセス権を取得 '
description: このセクションでは、Places Serviceにユーザーを追加し、Experience Platform LaunchがPlaces Serviceにアクセスできるようにする方法について説明します。
translation-type: tm+mt
source-git-commit: 26538602a73e806a4822705c7a3aa44d76351030
workflow-type: tm+mt
source-wordcount: '1079'
ht-degree: 7%

---

# Placesサービスへのアクセス権を取得 {#adding-user-launch-places}

Places Serviceには、 [Adobe Experience Cloudホームのクイックアクセスメニューからアクセスできます](https://experience.adobe.com)。
ユーザーIDがアクセス権を持っている場合は、次に示すように「Places Service」アイコンが表示されます。

![クイックアクセスメニュー](/help/assets/quickaccess.png)

Places Serviceは、Adobe Experience Platformメニューからもアクセスできます。

![Experience Platformメニュー](/help/assets/solutionaccessmenu.png)

これらのメニューのいずれにもPlaces Serviceが表示されない場合は、組織の管理者に問い合わせて、Admin ConsoleのPlaces Core ServiceにユーザーIDを追加してください。

## PlacesサービスとExperience Platform Launchへのユーザーの追加

ユーザーが [Experience Platform LaunchUIにアクセスできるようにするには](https://launch.adobe.com)、Admin ConsoleのPlaces Core Serviceにユーザーとして追加する必要があります。 ユーザーがExperience Platform Launchにアクセスできるようにし、モバイルプロパティを設定し、Adobe Experience PlatformSDKで場所を使用できるようにするには、Admin ConsoleのExperience Platform Launchに追加し、Experience Platform Launchに関する次の権限を与える必要があります。

* All Property Rights:
   * 開発
   * 承認
   * 公開
   * 拡張機能の管理
   * 環境の管理
* 「会社権限」の下のプロパティの管理権限

Experience Platform Launchを初めて追加する場合は、次の手順を実行してユーザーをユーザーおよびプレースサービスに追加します。 以前にユーザーを追加したことがある場合は、複数のプロファイルが表示される可能性があるので、必ず正しいプロファイルを選択してください。

>[!IMPORTANT]
>
>組織の管理者のみがAdmin Consoleにアクセスし、ユーザーを追加できます。

### 1. Places ServiceとExperience Platform Launchがプロビジョニングされていることを確認する

1. Experience Cloud組織にログインします。
1. 右上のExperience Cloudシェルスイッチャをクリックします。

   ![シェルスイッチャー](/help/assets/places_shell_switcher1.png)

1. **[!UICONTROL Platform]** の下で、「**[!UICONTROL Administration]**」をクリックします。

   リストに「 **管理** 」が表示されない場合は、管理者ではありません。 この手順を実行するには、組織管理者に問い合わせる必要があります。

1. Experience Cloud管理ページで、 **[!UICONTROL Admin Console]** カードのをクリックし **[!UICONTROL Take me there]**&#x200B;ます。

1. Admin Consoleで、複数の組織にアクセスできる場合は、ページの右上で正しい組織が選択されていることを確認します。

   これは、ユーザを追加する先の組織です。 正しい組織が選択されていない場合は、組織をクリックし、ドロップダウンリストから組織を選択します。

   >[!IMPORTANT]
   >
   >組織へのアクセス権を持っていない場合は、その組織への管理者アクセス権が持っていないことを意味します。

1. とのカードが表示され **[!UICONTROL Adobe Experience Platform Launch]** ていることを確認 **[!UICONTROL Places Core Services]** します。

   ![](/help/assets/places_provisioned1.png)

   表示された場合は、Places ServiceとExperience Platform Launchが組織用にプロビジョニングされています。 表示されない場合は、組織用にプロビジョニングする必要があります。


### 2.プロファイルを設定し、権限を追加します

1. Experience Platform Launchプロファイルを設定します。Experience Platformを使用すると、プロファイルに追加されたユーザーは、Experience Platform LaunchとそのモバイルプロパティをSDKで使用できます。

   a.メニューバーでをクリックし **[!UICONTROL Product]**&#x200B;ます。

   b.左側のパネルの「products」リストで、をクリックし **[!UICONTROL Adobe Experience Platform Launch]**&#x200B;ます。

   * 右側にExperience Platform Launchプロファイルが表示されます。
   * Experience Platform Launchには、「 *Launch - (org name)」というデフォルトのプロファイルがあり* ます。

      ユーザーを以前にExperience Platform Launchに追加している場合は、複数のプロファイルが一覧に表示される場合があります。

1. 正しいプロファイルを選択します。

   a.デフォルトのプロファイル名をクリックします。

   b. Click the **[!UICONTROL Permissions]** tab.

   c.の **[!UICONTROL Edit]** 横のをクリックし **[!UICONTROL Property Rights]**&#x200B;ます。

   d.左側のペインで、をクリックし **[!UICONTROL + Add all]**&#x200B;ます。

   この手順では、使用可能なすべての権限を、含まれる権限リストに移動します。

   e.をクリック **[!UICONTROL Company Rights]**&#x200B;します。

   f.左側のペインで、をクリックし **[!UICONTROL + Manage Properties]**&#x200B;ます。

   g.をクリック **[!UICONTROL Save]**&#x200B;します。

>[!IMPORTANT]
>
>Places Serviceの場合は、デフォルトのプロファイルがありますが、権限を追加する必要はありません。

作成したプロファイルに権限が正常に追加されました。

### 3. Places Serviceお追加よびExperience Platform Launchプロファイルのユーザーまたは開発者

Places ServiceおよびExperience Platform Launchプロファイルにユーザーや開発者を追加できます。

### ユーザーの追加

Places ServiceおよびExperience Platform Launchプロファイルにユーザーを追加するには：

1. Experience Platform Launch追加プロファイルのユーザー。

   a.メニューバーでをクリックし **[!UICONTROL Overview]**&#x200B;ます。

   b.カード上で、次のこ **[!UICONTROL Adobe Experience Platform Launch]** とを確認します。

   * カードの下部に2つのドットが表示されます。
   * 左側の点は黒です。

      右側のドットが黒い場合は、開発者のみを追加できます。 ユーザーを追加するには、左側の点をクリックします。
   c.をクリックし **[!UICONTROL + Add Users]**&#x200B;ます。

   d.ユーザーのAdobe IDを入力します。

   e.次のいずれかの手順を実行します。

   * 新しいユーザーを追加する場合は、をクリック **[!UICONTROL New user]**&#x200B;し、ユーザーの姓と名を入力します。
   * 既存のユーザーを追加する場合は、表示されるユーザー名をクリックします。

   f.ドロップダウン **[!UICONTROL Please select a profile for this product]** リストで、前に編集したプロファイルを選択します。

   g.をクリック **[!UICONTROL Save]**&#x200B;します。

1. Add a user to **[!UICONTROL Places Core Services]**.

   >[!TIP]
   >
   >現在、すべてのPlaces Serviceユーザーに同じ権限が与えられているので、権限を編集する必要はありません。

   a.カード上で、次のこ **[!UICONTROL Places Core Services]** とを確認します。

   * カードの下部に2つのドットが表示されます。
   * 左側の点は黒です。

   b.をクリック **[!UICONTROL + Assign Users]**&#x200B;します。

   c.ユーザーのAdobe IDを入力します。

   d.次のいずれかの手順を実行します。

   * 新しいユーザーを追加する場合は、をクリック **[!UICONTROL New user]**&#x200B;し、ユーザーの姓と名を入力します。
   * 既存のユーザーを追加する場合は、表示されるユーザー名をクリックします。

   e.ドロップダウン **[!UICONTROL Please select a profile for this product]** リストで、「配置」プロファイルを選択します。

   f.をクリック **[!UICONTROL Save]**&#x200B;します。

### 開発追加者

Web Service APIへのアクセスも必要なユーザーの場合は、開発者として追加する必要があります。

開発者を追加するには：

1. On the **[!UICONTROL Places Core Services]** card, verify the following:

   * カードの下部に2つのドットが表示されます。
   * 右側の点をクリックすると、カードの下部に **[!UICONTROL Assign Developers]** 表示されます。

1. 「**[!UICONTROL + Assign Developers]**」をクリックします。

1. ユーザーの Adobe ID を入力します。

1. 次のいずれかの手順を実行します。

   * 新しいユーザーを追加する場合は、をクリック **[!UICONTROL New user]** し、ユーザーの姓と名を入力します。
   * 既存のユーザーを追加する場合は、表示されるユーザー名をクリックします。

1. ドロップダウン **[!UICONTROL Please select a profile for this product]** リストで、「Places Service」プロファイルを選択します。

1. 「**保存**」をクリックします。

ユーザーには、Experience Platform Launch へのアクセス権があることを通知する電子メールが届きます。They can can log in to the [Experience Platform Launch](https://launch.adobe.com) or the [Places Service](https://places.adobe.com) UIs for this organization. 「**開発者の追加**」手順の手順 4 を完了すると、ユーザーは [Adobe I/O コンソール](https://console.adobe.io)にログインして、Places 統合を作成し、Places REST API を使用することもできます。
