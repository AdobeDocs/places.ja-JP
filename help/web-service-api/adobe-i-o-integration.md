---
title: Adobe I/O統合の概要
description: Adobe I/O統合の作成に関する情報です。
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# Integration overview and prerequisites {#integration-prereqs}

この情報では、Adobe I/OとPlacesの統合を作成する方法を示します。

## ユーザーアクセスの前提条件

組織のシステム管理者に、次のタスクが完了していることを確認します。

* コアサービスを組織の管理コンソールに配置します。
* 組織に追加されました。
* 組織のPlacesコアサービスにユーザーとして追加されました。

   詳しくは、よくある質問(FAQ) *の「ロケーションサービスおよびエクスペリエンスプラットフォーム起動プロファイルへのユーザーまたは開発者の追加* 」 [を参照してください](/help/places-faqs.md)。

* 組織のPlacesコアサービスに開発者として追加されました。

   開発者の追加について詳しくは、よくある質問( *FAQ)の「ロケーションサービスおよびエクスペリエンスプラットフォーム起動プロファイルへのユーザー* または開発者の [追加」を参照してください](/help/places-faqs.md)。

   開発者ロールについて詳しくは、開発者の管理を参照 [してください](https://helpx.adobe.com/enterprise/using/manage-developers.html)。

### REST APIリクエスト

Places REST APIへの各リクエストには、次の項目が必要です。

* 組織ID
* APIキー
* ベアラトークン

Adobe I/Oとの統合により、これらの項目と、JSON Web Token(JWT)を使用してベアラトークンをリクエストする方法が提供されます。

* JWTについて詳しくは、「JSON webトークンの概 [要」を参照してください](https://jwt.io/introduction/)。
* Places用の統合を作成するには、以下の「Places統合の作 *成」の節を参照してください* 。
* APIキーの統合、JWTの生成、および公開鍵証明書について詳しくは、 [Adobe I/O認証の概要を参照してください](https://www.adobe.io/apis/cloudplatform/console/authentication/gettingstarted.html)。

>[!IMPORTANT]
>
>Adobe I/Oコンソールにログインできない場合、またはExperience Platform Location Serviceが統合を作成ページのオプションでない場合は *、* WebサービスAPIの概要の組織の要件 *を参照* してください [](/help/web-service-api/places-web-services.md)。

## 場所の統合の作成

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

   OpenSSLについて詳しくは、OpenSSLを参照してく [ださい](https://www.openssl.org/)。

   >[!IMPORTANT]
   >
   >指定した情報は、キーに組み込まれます。

1. とファイルが存在するディレク `.key` トリ `.crt` に移動します。

   例えば、iOSでは、// **[!UICONTROL Macintosh HD]** &gt;に移 **[!UICONTROL users]** 動し **[!UICONTROL (your user name)]** ます **[!UICONTROL Keys]**。

次のビデオでは、キーペアの生成プロセスを示します。

![統合ビデオ](/help/assets/places_integration_video.gif)

### Adobe I/Oコンソールでの場所統合の作成

場所の統合を作成するには：

1. https://console.adobe.ioに移動 [し](https://console.adobe.io) 、Adobe IDでサインインします。
1. 「クイックス **タート** 」セクションで、「統合を作成」を **クリックします**。
1. を選択し、 **[!UICONTROL Access an API]** をクリックしま **[!UICONTROL Continue]**&#x200B;す。

   **[!UICONTROL Access an API]** がデフォルトの場所です。

1. 複数のExperience cloud組織にアクセスできる場合は、右上のドロップダウンリストから組織を選択します。
1. Under **[!UICONTROL Experience Cloud]**, select **[!UICONTROL Places]** as the Adobe service to which you want to integrate and click **[!UICONTROL Continue]**.
1. を選択し、 **[!UICONTROL New integration]** をクリックしま **[!UICONTROL Continue]**&#x200B;す。
1. 新しい統合を作成画面で、名前と説明を入力します。
1. 上で作成したフ `xxxx_public.crt` ァイルをドロップゾーンにドラッグ&amp;ドロ **[!UICONTROL Public keys certificates]** ップします。
1. 製品プロファイルを選択します。

   選択するプロファイルが不明な場合は、システム管理者に問い合わせてください。
1. At the bottom of the page, click **[!UICONTROL Create integration]**.
1. 数秒後、統合の作成画面で ** 、次のメッセージが表示されることを確認します。

   `Your integration has been created.`

1. 統合の詳細ページが上部に統合の名前と共に表示されます。

   このタ **[!UICONTROL Overview]** ブはデフォルトで表示され、APIキー、組織ID、テクニカルアカウントID、および統合に関するその他の詳細が表示されます。

### 組織IDとAPIキーを記録します

1. 統合の詳細ページで、タブをクリックし **[!UICONTROL Services]** て、がに表示されるこ **[!UICONTROL Places]** とを確認しま **[!UICONTROL Configured Services]**&#x200B;す。
1. タブで、API **[!UICONTROL Overview]** キー（クライアントID）と組織IDを探して記録します。

   これらのIDは、各Places REST APIリクエストに必要です。

![](/help/assets/places_orgid_api-key.png)

### JWTトークンの生成

統合の詳細ページで、タブをクリック **[!UICONTROL JWT]** し、JWTを生成して交換URLを指定することで統合をテストできるようにします。

JWTトークンを生成するには：

1. テキストエディターで、上で作成し `private.key` たファイルを開きます。
1. On the **[!UICONTROL JWT]** tab, copy the contents of the key and paste it in the **[!UICONTROL Paste private key]** field.
1. 「**[!UICONTROL Generate JWT]**」をクリックします。
1. In the **[!UICONTROL Sample CURL command]** section, click **[!UICONTROL Copy]** and paste the contents in your command prompt or terminal window.
1. キーボードを押して、コマ **[!UICONTROL Enter]** ンドを実行します。
1. との値 `"token_type": "bearer"` を探し `"access_token"` ます。

   bearerアクセストークンの値は、Places APIリクエストで使用する値です。

>[!IMPORTANT]
>
>アドビのアクセストークン **は** 24時間のみ有効なので、サンプルのCURLコマンド（手順5）を保存します。 アクセストークンが無効になった場合は、トークンを再生成する必要があります。