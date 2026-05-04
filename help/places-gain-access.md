---
title: Places サービスへのアクセス権を取得
description: この節では、Places サービスとExperience Platform Launchにユーザーを追加して、ユーザーがPlaces サービスにアクセスできるようにする方法について説明します。
exl-id: f388945e-cf26-4694-9697-9fe564ae4b69
TQID: https://experienceleague.adobe.com/EYg1wjQJZeHqX7vPnJ1VUZzojqG6ANjS8-VBXV3y51c
product_v2: id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9id: f7bdf6be-dd3b-4d2d-ac52-0e62ed0d3102
feature_v2: id: c132d929-fa62-4271-803e-b823be07b914id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2: id: b64298cc-90cc-46b7-8917-ee391f1c7516id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0id: f5efb499-54f9-432b-ac5c-599dbac103afid: f6ff4d13-7b5c-4533-8556-95e76673d4cb
topic_v2: id: d3cdead0-685a-4489-9250-4bb709942f66id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 919
ht-degree: 2%

---

# Places サービスへのアクセス権を取得 {#adding-user-launch-places}

Places サービスは、データ収集UI内で使用できるようになりました。 [Adobe Experience Cloud ホーム ](https://experience.adobe.com)のクイックアクセスメニューからData Collectionにアクセスできます。

![ クイックアクセスメニュー](/help/assets/quickaccess.png)

Adobe Experience Platform メニューからデータ収集にアクセスすることもできます。

![Experience Platform メニュー](/help/assets/solutionaccessmenu.png)

ユーザーIDにアクセス権がある場合、次に示すように、データ収集のデータ管理の下の左側のパネルにPlaces サービスアイコンが表示されます。

![ データ収集の左側のパネル ](/help/assets/places_in_data_collection.png)

この場所にPlaces サービスが表示されない場合は、組織内の管理者に連絡して、Admin ConsoleのAdobe Experience PlatformにユーザーIDを追加してください。

## Places サービスおよびExperience Adobe Experience Platform Data Collectionへのアクセスにユーザーを追加する

PlacesがAdobe Experience Platformに含まれるようになりました。 [Places サービス ](https://experience.adobe.com/#/data-collection/places)へのアクセスを許可するには、Admin Console as a userのAdobe Experience Platformに追加する必要があります。 モバイルプロパティを設定し、Experience Platform SDKでPlacesを使用するために必要な権限を持つAdobe Experience Platform Data Collectionへのアクセス権をユーザーに付与するには、Admin ConsoleのAdobe Experience Platform Data Collectionにも追加し、Adobe Experience Platform Data Collectionに対する次の権限を付与する必要があります。

* プロパティ権限のすべての権限：
   * 承認
   * 開発
   * プロパティを編集
   * 環境の管理
   * 拡張機能の管理
   * 公開
* 会社権限のプロパティの管理権限

初めてユーザーを追加する場合は、次の手順を実行して、Adobe Experience Platform Data CollectionとAdobe Experience Platformにユーザーを追加します。 以前にユーザーを追加したことがある場合は、複数のプロファイルが表示される可能性があるので、必ず正しいプロファイルを選択してください。

>[!IMPORTANT]
>
>組織管理者のみがAdmin Consoleにアクセスし、ユーザーを追加できます。

### &#x200B;1. Adobe Experience PlatformとAdobe Experience Platform Data Collectionがプロビジョニングされていることを確認します

1. Experience Cloudにログインします。[Adobe Experience Cloud ホーム ](https://experience.adobe.com)。
1. 右上のExperience Cloud シェルスイッチャーをクリックして、ドロップダウンメニューを表示します。

   ![ シェルスイッチャー](/help/assets/places_shell_switcher1.png)

1. リストの下部にある「**[!UICONTROL Admin Console]**」をクリックします。 （**[!UICONTROL Admin Console]**&#x200B;へのリンクは、「クイックアクセス」セクションにも表示されます）。

   リストに&#x200B;**[!UICONTROL Admin Console]**&#x200B;が表示されない場合は、管理者ではありません。 この手順を完了するには、組織の管理者に連絡する必要があります。

1. Admin Consoleで、複数の組織にアクセスできる場合は、ページの右上で正しい組織が選択されていることを確認します。

   これは、ユーザーを追加する組織です。 正しい組織が選択されていない場合は、組織をクリックし、ドロップダウンリストから正しい組織を選択します。

   >[!IMPORTANT]
   >
   >目的の組織がドロップダウンリストにない場合は、その組織への管理者アクセス権がないことを意味します。

1. Admin Consoleで、「Products」タブをクリックし、**[!UICONTROL Adobe Experience Platform Data Collection]**&#x200B;および&#x200B;**[!UICONTROL Adobe Experience Platform]**&#x200B;のカードが表示されていることを確認します。

   ![](/help/assets/places_provisioned1.png)

   これらの2つの製品は、すべての組織に自動的にプロビジョニングされるので、存在する必要があります。


### &#x200B;2. これらの製品にユーザーを追加

#### Places サービス UIへのアクセス権を提供するユーザーを追加

1. 「製品」タブで、**[!UICONTROL Adobe Experience Platform]** カードをクリックします。
2. **[!UICONTROL Adobe Experience Platform]**&#x200B;内の任意のプロファイルにユーザーを追加して、Placesにアクセスできます。特定の権限を設定する必要はありません。
3. プロファイルを選択し（プロファイルが複数ある場合）、クリックして開きます。
4. 青い「**ユーザーを追加**」ボタンをクリックし、ユーザーにAdobeIDと名前を入力してから、「保存」をクリックして追加を完了します。

#### データ収集にユーザーを追加

1. 「製品」タブで、**[!UICONTROL Adobe Experience Platform Data Collection]** カードをクリックします。
2. デフォルトでは、**Default Data Collection All Access**&#x200B;という名前のプロファイルが作成されます。 このプロファイルにユーザーを追加すると、Places サービスとデータ収集を操作するための適切な権限がユーザーに付与されます。 別のプロファイルを選択した場合は、上記の権限が含まれていることを確認します。
3. プロファイルを選択し（プロファイルが複数ある場合）、クリックして開きます。
4. 青い「**ユーザーを追加**」ボタンをクリックし、ユーザーにAdobeIDと名前を入力してから、「保存」をクリックして追加を完了します。

#### Places サービスの開発者としてユーザーを追加します。

Places サービス REST APIへのアクセスも必要なユーザーの場合は、開発者として追加する必要があります。
1. 「製品」タブで、**[!UICONTROL Adobe Experience Platform]** カードをクリックします。
2. 上記の手順で既に&#x200B;**[!UICONTROL Adobe Experience Platform]** カードにユーザーが追加されている場合は、同じ以前に使用したプロファイルを選択してクリックします。
3. プロファイル内で、「**開発者**」タブをクリックします
4. 青い「**開発者を追加**」ボタンをクリックし、ユーザーにAdobeIDと名前を入力してから、「保存」をクリックして追加を完了します。

上記の手順を完了すると、ユーザーは&#x200B;**[!UICONTROL Adobe Experience Platform]**&#x200B;および&#x200B;**[!UICONTROL Adobe Experience Platform Data Collection]**&#x200B;へのアクセス権があることを知らせる電子メールを受け取ります。 次に、この組織の[Adobe Experience Cloud](https://experience.adobe.com)にログインし、Places サービスとData Collectionにアクセスできます。 手順&#x200B;**[!UICONTROL 開発者を追加]**&#x200B;する手順も完了した場合、ユーザーは[Adobe Developer Console](https://developer.adobe.com/console/home)にログインして、Places サービス REST APIへのアクセスを提供するプロジェクトを作成することもできます。
