---
title: 'Placesサービスへのアクセス権を取得 '
description: このセクションでは、Places Serviceにユーザーを追加し、Experience Platform LaunchがPlaces Serviceにアクセスできるようにする方法について説明します。
translation-type: tm+mt
source-git-commit: ecf50d67d4c08e79d9c3be64480f27d435fd7fcb
workflow-type: tm+mt
source-wordcount: '1160'
ht-degree: 10%

---

# Places Serviceへのアクセスを取得{#adding-user-launch-places}

Places Serviceには、[Adobe Experience Cloudホーム](https://experience.adobe.com)のクイックアクセスメニューからアクセスできます。
ユーザーIDがアクセス権を持っている場合は、次に示すように「Places Service」アイコンが表示されます。

![クイックアクセスメニュー](/help/assets/quickaccess.png)

Places Serviceは、Adobe Experience Platformメニューからもアクセスできます。

![Experience Platformメニュー](/help/assets/solutionaccessmenu.png)

これらのメニューのいずれにもPlaces Serviceが表示されない場合は、組織の管理者に問い合わせて、Admin ConsoleのPlaces Core ServiceにユーザーIDを追加してください。

## PlacesサービスとExperience Platform Launchへのユーザーの追加

ユーザーが[Experience Platform LaunchUI](https://launch.adobe.com)にアクセスできるようにするには、ユーザーとしてAdmin ConsoleのPlaces Core Serviceに追加する必要があります。 ユーザーがExperience Platform Launchにアクセスできるようにし、モバイルプロパティを設定し、Adobe Experience PlatformSDKで場所を使用できるようにするには、Admin ConsoleのExperience Platform Launchに追加し、Experience Platform Launchに関する次の権限を与える必要があります。

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

1. 「**[!UICONTROL プラットフォーム]**」で、「**[!UICONTROL 管理]**」をクリックします。

   リストに&#x200B;**[!UICONTROL 管理]**&#x200B;が表示されない場合は、管理者ではありません。 この手順を実行するには、組織管理者に問い合わせる必要があります。

1. Experience Cloud管理ページの&#x200B;**[!UICONTROL Admin Console]**&#x200B;カードで、**[!UICONTROL Take me there]**&#x200B;をクリックします。

1. Admin Consoleで、複数の組織にアクセスできる場合は、ページの右上で正しい組織が選択されていることを確認します。

   これは、ユーザを追加する先の組織です。 正しい組織が選択されていない場合は、組織をクリックし、ドロップダウンリストから組織を選択します。

   >[!IMPORTANT]
   >
   >組織へのアクセス権を持っていない場合は、その組織への管理者アクセス権が持っていないことを意味します。

1. **[!UICONTROL Adobe Experience Platform Launch]** および **[!UICONTROL Places コアサービス]**&#x200B;のカードが表示されます。

   ![](/help/assets/places_provisioned1.png)

   表示された場合は、Places ServiceとExperience Platform Launchが組織用にプロビジョニングされています。 表示されない場合は、組織用にプロビジョニングする必要があります。


### 2.プロファイルを設定し、権限を追加します

1. Experience Platform Launchプロファイルを設定します。Experience Platformを使用すると、プロファイルに追加されたユーザーは、Experience Platform LaunchとそのモバイルプロパティをSDKで使用できます。

   a.メニューバーで「**[!UICONTROL 製品]**」をクリックします。

   b.左側のウィンドウのproductsリストで、**[!UICONTROL Adobe Experience Platform Launch]**&#x200B;をクリックします。

   * 右側にExperience Platform Launchプロファイルが表示されます。
   * Experience Platform Launchには、*Launch - (org name)*&#x200B;というデフォルトのプロファイルがあります。

      ユーザーを以前にExperience Platform Launchに追加している場合は、複数のプロファイルが一覧に表示される場合があります。

1. 正しいプロファイルを選択します。

   a.デフォルトのプロファイル名をクリックします。

   b.「**[!UICONTROL 権限]**」タブをクリックします。

   c. 「**[!UICONTROL プロパティ権限]**」の隣にある「**[!UICONTROL 編集]**」をクリックします。

   d.左側のウィンドウで、「**[!UICONTROL + 追加 all]**」をクリックします。

   この手順では、使用可能なすべての権限を、含まれる権限リストに移動します。

   e.「**[!UICONTROL 会社権限]**」をクリックします。

   f.左側のウィンドウで、「**[!UICONTROL +プロパティを管理]**」をクリックします。

   g. 「**[!UICONTROL 保存]**」をクリックします。

>[!IMPORTANT]
>
>Places Serviceの場合は、デフォルトのプロファイルがありますが、権限を追加する必要はありません。

作成したプロファイルに権限が正常に追加されました。

### 3. Places Serviceお追加よびExperience Platform Launchプロファイルのユーザーまたは開発者

Places ServiceおよびExperience Platform Launchプロファイルにユーザーや開発者を追加できます。

### ユーザーの追加

Places ServiceおよびExperience Platform Launchプロファイルにユーザーを追加するには：

1. Experience Platform Launch追加プロファイルのユーザー。

   a.メニューバーで「**[!UICONTROL 概要]**」をクリックします。

   b.**[!UICONTROL Adobe Experience Platform Launch]**&#x200B;カードで、次の点を確認します。

   * カードの下部に2つのドットが表示されます。
   * 左側の点は黒です。

      右側のドットが黒い場合は、開発者のみを追加できます。 ユーザーを追加するには、左側の点をクリックします。
   c. 「**[!UICONTROL +追加ユーザー]**」をクリックします。

   d.ユーザーのAdobe IDを入力します。

   e.次のいずれかの手順を実行します。

   * 新しいユーザーを追加する場合は、「**[!UICONTROL 新しいユーザー]**」をクリックし、ユーザーの姓と名を入力します。
   * 既存のユーザーを追加する場合は、表示されるユーザー名をクリックします。

   f.**[!UICONTROL 「Please select a product for this product]**」ドロップダウンリストで、以前に編集したプロファイルを選択します。

   g. 「**[!UICONTROL 保存]**」をクリックします。

1. &lt;a0追加/>コアサービス&#x200B;]**を配置するユーザー。**[!UICONTROL 

   >[!TIP]
   >
   >現在、すべてのPlaces Serviceユーザーに同じ権限が与えられているので、権限を編集する必要はありません。

   a.**[!UICONTROL Places Core Services]**&#x200B;カードで、次を確認します。

   * カードの下部に2つのドットが表示されます。
   * 左側の点は黒です。

   b.「**[!UICONTROL +ユーザーの割り当て]**」をクリックします。

   c.ユーザーのAdobe IDを入力します。

   d.次のいずれかの手順を実行します。

   * 新しいユーザーを追加する場合は、「**[!UICONTROL 新しいユーザー]**」をクリックし、ユーザーの姓と名を入力します。
   * 既存のユーザーを追加する場合は、表示されるユーザー名をクリックします。

   e.**[!UICONTROL 「Places aプロファイルfor this product]**」ドロップダウンリストで、「Places」プロファイルを選択します。

   f. 「**[!UICONTROL 保存]**」をクリックします。

### 開発追加者

Web Service APIへのアクセスも必要なユーザーの場合は、開発者として追加する必要があります。

開発者を追加するには：

1. **[!UICONTROL Places コアサービス]**&#x200B;カードで、以下を確認します。

   * カードの下部に2つのドットが表示されます。
   * 右側のドットをクリックすると、「**[!UICONTROL 開発者の割り当て]**」がカードの下部に表示されます。

1. 「**[!UICONTROL +開発者の割り当て]**」をクリックします。

1. ユーザーの Adobe ID を入力します。

1. 次のいずれかの手順を実行します。

   * 新しいユーザーを追加する場合は、「**[!UICONTROL 新しいユーザー]**」をクリックし、ユーザーの姓と名を入力します。
   * 既存のユーザーを追加する場合は、表示されるユーザー名をクリックします。

1. 「**[!UICONTROL この製品]**&#x200B;のプロファイルを選択してください」ドロップダウンリストで、「Places Service」プロファイルを選択します。

1. 「**[!UICONTROL 保存]**」をクリックします。

ユーザーには、Experience Platform Launch へのアクセス権があることを通知する電子メールが届きます。ユーザーは、この組織の[Experience Platform Launch](https://launch.adobe.com)または[プレースサービス](https://places.adobe.com) UIにログインできます。 「**[!UICONTROL 開発者の追加]**」手順の手順 4 を完了すると、ユーザーは [Adobe I/O コンソール](https://console.adobe.io)にログインして、Places 統合を作成し、Places REST API を使用することもできます。
