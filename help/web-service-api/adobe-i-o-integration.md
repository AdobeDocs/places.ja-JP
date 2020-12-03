---
title: Adobe I/O統合の概要
description: Adobe I/O統合の作成に関する情報です。
translation-type: tm+mt
source-git-commit: c22efc36f2eac6b20fc555d998c3988d8c31169e
workflow-type: tm+mt
source-wordcount: '832'
ht-degree: 1%

---


# Integration overview and prerequisites {#integration-prereqs}

この情報では、Adobe I/OとPlaces Serviceの統合を作成する方法を示します。

## ユーザーアクセスの前提条件

組織のシステム管理者に次のタスクが完了していることを確認します。

* コアサービスが組織の管理コンソールに表示されます。
* 組織に追加されました。
* 組織のPlacesコアサービスにユーザーとして追加されている。

   詳しくは、「Places Service *へのアクセス権の取得」で、Places ServiceおよびExperience Platform Launchプロファイル* のユーザーまたは開発者を参照してください [](/help/places-gain-access.md)。

* 組織のPlacesコアサービスに開発者として追加されている。

   開発者の追加について詳しくは、「Places Service *へのアクセスの* 取得」の「Places Service」と「Experience Platform Launchプロファイル [」に、ユーザーまたは開発者を参照してください](/help/places-gain-access.md)。

   開発者ロールについて詳しくは、「開発者の [管理](https://helpx.adobe.com/jp/enterprise/using/manage-developers.html)」を参照してください。

### REST APIリクエスト

Places Service REST APIへの各要求には、次の項目が必要です。

* 組織ID
* APIキー
* ベアラトークン

Adobe I/Oとの統合は、これらの項目と、JSON Web Token(JWT)を使用してベアラトークンをリクエストする方法を提供します。

* JWTについて詳しくは、「JSON Webトークンの [概要](https://jwt.io/introduction/)」を参照してください。
* Places Serviceの統合を作成するには、下の「Places Service統合の *作成* 」セクションを参照してください。
* APIキーの統合、JWTの生成、および公開鍵証明書について詳しくは、 [Adobe I/O認証の概要を参照してください](https://www.adobe.io/apis/cloudplatform/console/authentication/gettingstarted.html)。

>[!IMPORTANT]
>
>Adobe I/Oコンソールにログインできない場合、または統合を *作成ページで「Places Service」オプションが選択できない場合は*、 *WebサービスAPIの概要の* 組織要件 [を参照してください](/help/web-service-api/places-web-services.md)。

## Places Service統合の作成

Places Serviceの統合を作成するには、次のタスクを実行します。

### 公開鍵と秘密鍵のペアを生成する

Places Serviceの統合を作成するには、公開鍵と秘密鍵のペアが必要です。 これらのペアは購入することも、独自の自己署名付きキーを生成することもできます。

独自の自己署名付きキーを生成するには：

1. ターミナルウィンドウで、次の各行をコピーして貼り付け、各行を貼り付けた **[!UICONTROL Enter]** 後にを押します。

   ```text
      mkdir keys
      cd keys
      openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout places_integration_test_private.key -out    places_integration_test_public.crt
   ```

   >[!IMPORTANT]
   >
   >キーを簡単に参照できるように名前を付けて、フォルダーに保存することをお勧めします。 複数の統合を作成する場合、どのキーがどの統合に属するかを簡単に識別および管理できます。

1. OpenSSLから要求された情報を入力します。

   ```text
   Country Name (2 letter code:  // Example: US
   State or Province Name (full name):  // Example: California
   Locality Name (eg, city):  // Example: San Jose
   Organization Name (eg, company):  // Example: Places
   Organizational Unit Name (eg, section):  // Example: Engineering
   Common Name (eg, fully qualified host name):  // Example: places.com
   Email Address:  // Example:  poi@places.com
   ```

   OpenSSLについて詳しくは、OpenSSL [を参照してください](https://www.openssl.org/)。

   >[!IMPORTANT]
   >
   >指定する情報は、キーに組み込まれます。

1. とファイルが存在するディレクトリ `.key` に移動し `.crt` ます。

   例えば、MacOSでは、/ **[!UICONTROL Macintosh HD]** / **[!UICONTROL users]** >に移動し **[!UICONTROL (your user name)]****[!UICONTROL Keys]**&#x200B;ます。

次のビデオでは、キーペアの生成プロセスを順を追って説明します。

![統合ビデオ](/help/assets/places_integration_video.gif)

### Adobe I/OコンソールでPlaces Service統合を作成する

Places Service統合を作成するには：

1. https://console.adobe.ioに移動し、 [Adobe IDでサインインします](https://console.adobe.io) 。
1. In the **Quick Start** section, click on **Create integration**.
1. 「**[!UICONTROL Access an API]**」を選択し、「**[!UICONTROL Continue]**」をクリックします。

   **[!UICONTROL Access an API]** がデフォルトの場所です。

1. 複数のExperience Cloud組織にアクセスできる場合は、右上のドロップダウンリストからその組織を選択します。
1. Under **[!UICONTROL Experience Cloud]**, select **[!UICONTROL Places Service]** as the Adobe service to which you want to integrate and click **[!UICONTROL Continue]**.
1. 「**[!UICONTROL New integration]**」を選択し、「**[!UICONTROL Continue]**」をクリックします。
1. [新しい統合の作成]画面で、名前と説明を入力します。
1. 上で作成した `xxxx_public.crt` ファイルをドロップゾーンにドラッグ&amp;ドロップし **[!UICONTROL Public keys certificates]** ます。
1. 製品プロファイルを選択します。

   選択するプロファイルが不明な場合は、システム管理者に問い合わせてください。
1. ページの下部で、をクリックし **[!UICONTROL Create integration]**&#x200B;ます。
1. 数秒後、 *統合の作成画面で* 、次のメッセージが表示されることを確認します。

   `Your integration has been created.`

1. 統合の詳細ページが上部に統合の名前と共に表示されます。

   この **[!UICONTROL Overview]** タブはデフォルトで表示され、APIキー、組織ID、テクニカルアカウントID、および統合に関するその他の詳細が表示されます。

### 組織IDとAPIキーを記録します

1. 統合の詳細ページで、 **[!UICONTROL Services]** タブをクリックし、が表示さ **[!UICONTROL Places Service]** れることを確認し **[!UICONTROL Configured Services]**&#x200B;ます。
1. タブで、APIキー（クライアントID）と組織IDを探して記録し **[!UICONTROL Overview]** ます。

   これらのIDは、各Places Service REST API要求に必要です。

![](/help/assets/places_orgid_api-key.png)

### JWTトークンの生成

統合の詳細ページでタブをクリックし、JWTを生成して交換URLを指定することで統合をテストできるように **[!UICONTROL JWT]** します。

JWTトークンを生成するには：

1. テキストエディターで、上で作成した `private.key` ファイルを開きます。
1. On the **[!UICONTROL JWT]** tab, copy the contents of the key and paste it in the **[!UICONTROL Paste private key]** field.
1. 「**[!UICONTROL Generate JWT]**」をクリックします。
1. In the **[!UICONTROL Sample CURL command]** section, click **[!UICONTROL Copy]** and paste the contents in your command prompt or terminal window.
1. キーボードを押してコマンド **[!UICONTROL Enter]** を実行します。
1. と `"token_type": "bearer"` 値を探し `"access_token"` ます。

   bearerアクセストークンの値は、Places Service APIリクエストで使用する値です。

>[!IMPORTANT]
>
>Adobeアクセストークンは24時間 **のみ有効なので** 、サンプルのCURLコマンドを保存します（手順5）。 アクセストークンが無効になった場合は、トークンを再生成する必要があります。