---
title: Places Service へのアクセス権を取得
description: このセクションでは、Places サービスとExperience Platform Launchにユーザーを追加して、Places サービスにアクセスできるようにする方法について説明します。
exl-id: f388945e-cf26-4694-9697-9fe564ae4b69
source-git-commit: c9058e9b70c2ef97151078f43913963471730bd2
workflow-type: tm+mt
source-wordcount: '913'
ht-degree: 1%

---

# Places Service へのアクセス権を取得 {#adding-user-launch-places}

Places Service がデータ収集 UI 内で使用できるようになりました。 データ収集には、 [Adobe Experience Cloudホーム](https://experience.adobe.com).

![クイックアクセスメニュー](/help/assets/quickaccess.png)

Adobe Experience Platformメニューからデータ収集にアクセスすることもできます。

![Experience Platformメニュー](/help/assets/solutionaccessmenu.png)

ユーザー ID がアクセス権を持っている場合は、次に示すように、データ収集のデータ管理の下の左パネルに Places Service アイコンが表示されます。

![データ収集の左パネル](/help/assets/places_in_data_collection.png)

この場所に Places Service が表示されない場合は、組織の管理者に問い合わせて、Admin ConsoleのAdobe Experience Platformにユーザー ID を追加してください。

## Places Service および Experience Adobe Experience Platform Data Collection にアクセスするユーザーの追加

Places がAdobe Experience Platformに含まれるようになりました。 ユーザーが [Places Service](https://experience.adobe.com/#/data-collection/places)の場合、ユーザーとしてAdmin ConsoleのAdobe Experience Platformに追加する必要があります。 必要な権限でExperience Platformのデータ収集にアクセスして、モバイルプロパティを設定し、Adobe Experience Platform SDK で Places を使用できるようにするには、Admin ConsoleのAdobe Experience Platformデータ収集にも追加され、Adobe Experience Platformデータ収集に次の権限が与えられる必要があります。

* プロパティ権限の下のすべての権限：
   * 承認
   * 開発
   * プロパティを編集
   * 環境の管理
   * 拡張機能の管理
   * 公開
* 会社権限のプロパティ管理権限

これが初めてユーザーを追加する場合は、次の手順を実行して、ユーザーをAdobe Experience Platform Data Collection およびAdobe Experience Platformに追加します。 以前にユーザーを追加したことがある場合は、複数のプロファイルが表示される場合があるので、正しいプロファイルを選択するようにしてください。

>[!IMPORTANT]
>
>組織管理者のみが、ユーザーにアクセスし、Admin Consoleを追加できます。

### 1. Adobe Experience PlatformとAdobe Experience Platformのデータ収集がプロビジョニングされていることを確認します

1. Experience Cloud組織にログインし、 [Adobe Experience Cloudホーム](https://experience.adobe.com).
1. 右上にあるシェルスイッチャーをクリックして、Experience Cloudドロップダウンメニューを表示します。

   ![シェルスイッチャー](/help/assets/places_shell_switcher1.png)

1. リストの下部で、 **[!UICONTROL Admin Console]**. ( **[!UICONTROL Admin Console]** は、「クイックアクセス」の節でも参照できます )。

   表示されない **[!UICONTROL Admin Console]** リスト内に管理者ではない。 この手順を完了するには、組織管理者に問い合わせる必要があります。

1. Admin Consoleで、複数の組織にアクセスできる場合は、ページの右上で正しい組織が選択されていることを確認します。

   これは、ユーザーを追加する組織です。 正しい組織が選択されていない場合は、組織をクリックし、ドロップダウンリストから正しい組織を選択します。

   >[!IMPORTANT]
   >
   >目的の組織がドロップダウンリストにない場合は、その組織への管理者アクセス権がないことを意味します。

1. Admin Consoleで、「製品」タブをクリックし、 **[!UICONTROL Adobe Experience Platform Data Collection]** および **[!UICONTROL Adobe Experience Platform]** が表示されます。

   ![](/help/assets/places_provisioned1.png)

   これら 2 つの製品はすべての組織に自動的にプロビジョニングされるので、存在するはずです。


### 2.これらの製品にユーザーを追加する

#### Places Service UI へのアクセスを提供するユーザーを追加

1. 「製品」タブで、 **[!UICONTROL Adobe Experience Platform]** カード。
2. ユーザーは、 **[!UICONTROL Adobe Experience Platform]** Places へのアクセス権を取得するには、特定の権限を設定する必要はありません。
3. プロファイルを選択し（複数ある場合）、クリックして開きます。
4. 青をクリック **ユーザーを追加** ボタンをクリックし、Adobe ID と名前をユーザーに入力し、「保存」をクリックして追加を完了します。

#### ユーザーをデータ収集に追加

1. 「製品」タブで、 **[!UICONTROL Adobe Experience Platform Data Collection]** カード。
2. デフォルトでは、 **デフォルトのデータ収集のすべてのアクセス** が作成されました。 このプロファイルにユーザーを追加すると、Places サービスとデータ収集を操作するための適切な権限がユーザーに付与されます。 別のプロファイルを選択する場合は、上記の権限が含まれていることを確認します。
3. プロファイルを選択し（複数ある場合）、クリックして開きます。
4. 青をクリック **ユーザーを追加** ボタンをクリックし、Adobe ID と名前をユーザーに入力し、「保存」をクリックして追加を完了します。

#### ユーザーを Places Service の開発者として追加します。

Places Service REST API へのアクセスも必要なユーザーの場合は、開発者として追加する必要があります。
1. 「製品」タブで、 **[!UICONTROL Adobe Experience Platform]** カード。
2. ユーザーが既に **[!UICONTROL Adobe Experience Platform]** 上記の手順のカードで、以前に使用したのと同じプロファイルを選択し、クリックします。
3. プロファイル内で、 **開発者** タブ
4. 青をクリック **開発者を追加** ボタンをクリックし、Adobe ID と名前をユーザーに入力し、「保存」をクリックして追加を完了します。

上記の手順が完了すると、ユーザーは、へのアクセス権を持っていることを通知する電子メールを受け取ります。 **[!UICONTROL Adobe Experience Platform]** および **[!UICONTROL Adobe Experience Platform Data Collection]**. その後、 [Adobe Experience Cloud](https://experience.adobe.com) （この組織の場合）、Places サービスとデータ収集にアクセスします。 手順も完了している場合 **[!UICONTROL 開発者の追加]**&#x200B;を使用しない場合、 [Adobe Developer Console](https://developer.adobe.com/console/home) をクリックして、Places Service REST API へのアクセスを提供するプロジェクトを作成します。
