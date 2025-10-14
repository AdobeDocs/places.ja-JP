---
title: Places Service へのアクセス権の取得
description: このセクションでは、Places Service とExperience Platform Launchにユーザーを追加して、ユーザーが Places Service にアクセスできるようにする方法について説明します。
exl-id: f388945e-cf26-4694-9697-9fe564ae4b69
source-git-commit: c9058e9b70c2ef97151078f43913963471730bd2
workflow-type: tm+mt
source-wordcount: '907'
ht-degree: 1%

---

# Places Service へのアクセス権の取得 {#adding-user-launch-places}

Places Service がデータ収集 UI 内で使用できるようになりました。 データ収集には、[Adobe Experience Cloud ホーム &#x200B;](https://experience.adobe.com) のクイックアクセスメニューからアクセスできます。

![&#x200B; クイックアクセスメニュー &#x200B;](/help/assets/quickaccess.png)

また、Adobe Experience Platform メニューからデータ収集にアクセスすることもできます。

![Experience Platform メニュー &#x200B;](/help/assets/solutionaccessmenu.png)

ユーザー ID にアクセス権がある場合、以下に示すように、データ収集のデータ管理の下の左側のパネルに Places Service アイコンが表示されます。

![&#x200B; データ収集の左パネル &#x200B;](/help/assets/places_in_data_collection.png)

この場所に Places Service が表示されない場合は、Admin Consoleの管理者に連絡して、組織のAdobe Experience Platformにユーザー ID を追加してください。

## Places Service および Experience Adobe Experience Platform Data Collection にアクセスするためのユーザーの追加

場所は、Adobe Experience Platformに含まれるようになりました。 ユーザーが [Places Service](https://experience.adobe.com/#/data-collection/places) にアクセスできるようにするには、ユーザーとしてAdmin ConsoleのAdobe Experience Platformに追加される必要があります。 モバイルプロパティを設定し、Adobe Experience Platform SDK で Places を使用するために必要な権限でExperience Platformデータ収集にアクセスできるようにするには、Admin ConsoleでAdobe Experience Platform データ収集に追加し、Adobe Experience Platform データ収集の次の権限を付与する必要もあります。

* プロパティ権限の下のすべての権限：
   * 承認
   * 開発
   * プロパティを編集
   * 環境の管理
   * 拡張機能の管理
   * 公開
* 会社権限の下でのプロパティ管理権限

初めてユーザーを追加する場合は、次の手順を実行して、Adobe Experience Platform Data Collection とAdobe Experience Platformにユーザーを追加します。 以前にユーザーを追加したことがある場合は、複数のプロファイルが表示される場合があるので、必ず正しいプロファイルを選択してください。

>[!IMPORTANT]
>
>組織管理者のみがユーザーにアクセスしてAdmin Consoleを追加できます。

### 1. Adobe Experience PlatformとAdobe Experience Platform Data Collection がプロビジョニングされていることを確認します

1. Experience Cloud組織（[Adobe Experience Cloud ホーム &#x200B;](https://experience.adobe.com) にログインします。
1. 右上のExperience Cloudシェル切り替えボタンをクリックして、ドロップダウンメニューを表示します。

   ![&#x200B; シェルスイッチャー &#x200B;](/help/assets/places_shell_switcher1.png)

1. リストの下部にある [**[!UICONTROL Admin Console]**] をクリックします。 （**[!UICONTROL Admin Console]** へのリンクは、「クイックアクセス」セクションにもあります）。

   リストに **[!UICONTROL Admin Console]** が表示されない場合は、管理者ではありません。 この手順を完了するには、組織管理者に問い合わせる必要があります。

1. Admin Consoleで、複数の組織にアクセスできる場合は、ページの右上で正しい組織が選択されていることを確認します。

   これは、ユーザーを追加する組織です。 正しい組織が選択されていない場合は、組織をクリックし、ドロップダウンリストから正しい組織を選択します。

   >[!IMPORTANT]
   >
   >目的の組織がドロップダウンリストにない場合は、その組織への管理者アクセス権がありません。

1. Admin Consoleで、「製品」タブをクリックし、**[!UICONTROL Adobe Experience Platform Data Collection]** と **[!UICONTROL Adobe Experience Platform]** のカードが表示されていることを確認します。

   ![](/help/assets/places_provisioned1.png)

   これら 2 つの製品はすべての組織に自動的にプロビジョニングされるため、存在する必要があります。


### 2.これらの製品にユーザーを追加する

#### Places Service UI へのアクセスを提供するユーザーを追加

1. 「製品」タブで、**[!UICONTROL Adobe Experience Platform]** カードをクリックします。
2. ユーザーは、**[!UICONTROL Adobe Experience Platform]** 内の任意のプロファイルに追加して、場所へのアクセス権を取得できます。特定の権限を設定する必要はありません。
3. プロファイルを選択し（複数ある場合）、クリックして開きます。
4. 青い **ユーザーを追加** ボタンをクリックして、ユーザーに AdobeID と名前を入力し、「保存」をクリックして追加を完了します。

#### データ収集にユーザーを追加

1. 「製品」タブで、**[!UICONTROL Adobe Experience Platform Data Collection]** カードをクリックします。
2. デフォルトで、「**デフォルトデータ収集のすべてのアクセス** というプロファイルが作成されます。 このプロファイルにユーザーを追加すると、ユーザーに場所サービスおよびデータ収集を使用するための適切な権限が確実に付与されます。 別のプロファイルを選択する場合は、前述の権限が含まれていることを確認します。
3. プロファイルを選択し（複数ある場合）、クリックして開きます。
4. 青い **ユーザーを追加** ボタンをクリックして、ユーザーに AdobeID と名前を入力し、「保存」をクリックして追加を完了します。

#### Places Service の開発者としてユーザーを追加します。

Places Service REST API にもアクセスする必要があるユーザーの場合は、それらを開発者として追加する必要があります。
1. 「製品」タブで、**[!UICONTROL Adobe Experience Platform]** カードをクリックします。
2. 上記の手順で既に **[!UICONTROL Adobe Experience Platform]** カードに追加されている場合は、以前に使用したのと同じプロファイルを選択してクリックします。
3. プロファイル内で、「**開発者**」タブをクリックします。
4. 青い **開発者を追加** ボタンをクリックして、ユーザーに AdobeID と名前を入力し、「保存」をクリックして追加を完了します。

上記の手順が完了すると、**[!UICONTROL Adobe Experience Platformおよび**&#x200B;[!UICONTROL &#x200B; Adobe Experience Platform データ収集 &#x200B;]&#x200B;**へのアクセス権があることを知らせるメールが届き]** す。 その後、この組織の [Adobe Experience Cloud](https://experience.adobe.com) にログインし、Places Service と Data Collection にアクセスできます。 **[!UICONTROL 開発者を追加]** 手順も完了すると、ユーザーは [Adobe Developer Console](https://developer.adobe.com/console/home) にログインしてプロジェクトを作成し、Places Service REST API へのアクセスを提供できます。
