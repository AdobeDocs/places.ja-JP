---
title: Adobe I/O統合の概要
seo-title: Adobe I/O統合の概要
description: Adobe I/O統合の作成に関する情報です。
seo-description: Adobe I/O統合の作成に関する情報です。
translation-type: tm+mt
source-git-commit: f6c92bbd4fb21999f5c96ea0df8ede6919d1bc79

---


# Adobe I/O統合の概要 {#adobeio-integration}

Places REST APIへの各リクエストには、次の項目が必要です。

* 組織ID
* APIキー
* ベアラトークン

Adobe I/Oとの統合により、これらの項目と、JSON Web Token(JWT)を使用してベアラトークンをリクエストする方法が提供されます。

## 追加情報

* JWTについて詳しくは、「JSON webトークンの概 [要」を参照してください](https://jwt.io/introduction/)。
* Places用の統合を作成するには、以下の「Places統合の作 *成」の節を参照してください* 。
* APIキーの統合、JWTの生成、および公開鍵証明書について詳しくは、 [Adobe I/O認証の概要を参照してください](https://www.adobe.io/apis/cloudplatform/console/authentication/gettingstarted.html)。

>[!IMPORTANT]
>
>Adobe I/Oコンソールにログインできない場合、またはExperience Platform Location Serviceが統合を作成ページのオプションでない場合は *、**Places webサービスの概要での組織の要件* を参照 [してください](/help/places-web-service-api/places-web-services.md)。

## 場所の統合の作成 {#create-places-integration}

Places統合を作成するには、次のタスクを実行します。

### 公開鍵と秘密鍵のペアを生成する

場所の統合を作成するには、公開鍵と秘密鍵のペアが必要です。 これらのペアは購入することも、独自の自己署名キーを生成することもできます。

独自の自己署名キーを生成するには：

1. ターミナルウィンドウで、次の各行をコピーして貼り付け、各行を貼り付け **[!UICONTROL Enter]** た後にを押します。

   ```text
      mkdir keys
      cd keys
      openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout places_integration_test_private.key -out    places_integration_test_public.crt
   ```

   >[!IMPORTANT]
   >
   >キーを参照しやすいように名前を付けて、フォルダーに保存することをお勧めします。 複数の統合を作成する場合、どのキーがどの統合に属するかを簡単に識別し、管理できます。

2. OpenSSLから要求された情報を入力します。

   ```text
   Country Name (2 letter code:  // Example: US
   State or Province Name (full name):  // Example: California
   Locality Name (eg, city):  // Example: San Jose
   Organization Name (eg, company):  // Example: Places
   Organizational Unit Name (eg, section):  // Example: Engineering
   Common Name (eg, fully qualified host name):  // Example: places.com
   Email Address:  // Example:  poi@places.com
   ```

   OpenSSLについて詳しくは、OpenSSLを参照してく [ださい](https://www.openssl.org/)。

   >[!IMPORTANT]
   >
   >指定した情報は、キーに組み込まれます。

3. とファイルが存在するディレク `.key` トリ `.crt` に移動します。

   例えば、iOSでは、// **[!UICONTROL Macintosh HD]** &gt;に移 **[!UICONTROL users]** 動し **[!UICONTROL (your user name)]** ます **[!UICONTROL Keys]**。

次のビデオでは、キーペアの生成プロセスを示します。

![](/help/assets/places_integration_video.gif)

### Adobe I/Oコンソールでの場所統合の作成

場所の統合を作成するには：

1. https://console.adobe.ioに移動 [し](https://console.adobe.io) 、Adobe IDでサインインします。
2. 複数のExperience cloud組織にアクセスできる場合は、左側のドロップダウンリストから組織を選択します。
3. 「**[!UICONTROL New Integration]**」をクリックします。
4. を選択し、 **[!UICONTROL Access an API]** をクリックしま **[!UICONTROL Continue]**&#x200B;す。
5. の下 **[!UICONTROL Experience Cloud]**&#x200B;で、統 **[!UICONTROL Places]** 合するアドビサービスを選択し、をクリックします **[!UICONTROL Continue]**。
6. を選択し、 **[!UICONTROL New integration]** をクリックしま **[!UICONTROL Continue]**&#x200B;す。
7. [新しい統 *合を作成]画面で* 、名前と説明を入力します。
8. 上で作成したフ `xxxx_public.crt` ァイルをドロップゾーンにドラッグ&amp;ドロ **[!UICONTROL Public keys certificates]** ップします。
9. At the bottom of the page, click **[!UICONTROL Create integration]**.
10. 数秒後、統合の作成画面で ** 、次のメッセージが表示されることを確認します。

   `Your integration has been created.`

11. 「**[!UICONTROL Continue to integration details]**」をクリックします。

   APIキーとの統合の概要、組織ID、テクニカルアカウントID、および統合に関するその他の詳細が表示されます。

### 組織IDとAPIキーを記録します

1. タブに、そ **[!UICONTROL Services]** れが表示されることを確 **[!UICONTROL Places]** 認します。
2. タブで、API **[!UICONTROL Overview]** キー（クライアントID）と組織IDを探して記録します。

   これらのIDは、各Places REST APIリクエストに必要です。

![](/help/assets/places_orgid_api-key.png)

### JWTトークンの生成

Adobe I/Oコ **[!UICONTROL JWT]** ンソールのタブでは、JWTを生成し、交換URLを指定することで、統合をテストできます。

JWTトークンを生成するには：

1. テキストエディターで、上で作成し `private.key` たファイルを開きます。
2. タブで、 **[!UICONTROL JWT]** キーの内容をコピーし、フィールドに貼り付け **[!UICONTROL Paste private key]** ます。
3. 「**[!UICONTROL Generate JWT]**」をクリックします。
4. セクションで、 **[!UICONTROL Sample CURL command]** をクリックして、コ **[!UICONTROL Copy]** マンドプロンプトまたはターミナルウィンドウにコンテンツを貼り付けます。
5. キーボードを押して、コマ **[!UICONTROL Enter]** ンドを実行します。
6. との値 `"token_type": "bearer"` を探し `"access_token"` ます。

   bearerアクセストークンの値は、Places APIリクエストで使用する値です。

>[!IMPORTANT]
>
>アドビのアクセストークン **は** 24時間のみ有効なので、サンプルのCURLコマンド（手順5）を保存します。 アクセストークンが無効になった場合は、トークンを再生成する必要があります。

