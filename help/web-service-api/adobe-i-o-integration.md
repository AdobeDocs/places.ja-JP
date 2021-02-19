---
title: Adobe I/O統合の概要
description: Adobe I/O統合の作成に関する情報です。
translation-type: tm+mt
source-git-commit: c22efc36f2eac6b20fc555d998c3988d8c31169e
workflow-type: tm+mt
source-wordcount: '879'
ht-degree: 5%

---


# 統合の概要と前提条件{#integration-prereqs}

この情報では、Adobe I/OとPlaces Serviceの統合を作成する方法を示します。

## ユーザーアクセスの前提条件

組織のシステム管理者に次のタスクが完了していることを確認します。

* コアサービスが組織の管理コンソールに表示されます。
* 組織に追加されました。
* 組織のPlacesコアサービスにユーザーとして追加されている。

   詳しくは、「[Places Service](/help/places-gain-access.md)へのアクセス権を取得する」の「*Places ServiceおよびExperience Platform Launchプロファイル*&#x200B;追加へのユーザーまたは開発者のアクセス権」を参照してください。

* 組織のPlacesコアサービスに開発者として追加されている。

   開発者の追加について詳しくは、[Places Service](/help/places-gain-access.md)の&#x200B;*ユーザーまたは開発者追加をPlaces ServiceおよびExperience Platform Launchプロファイル*&#x200B;に参照してください。

   開発者の役割について詳しくは、[開発者の管理](https://helpx.adobe.com/jp/enterprise/using/manage-developers.html)を参照してください。

### REST APIリクエスト

Places Service REST APIへの各要求には、次の項目が必要です。

* 組織ID
* APIキー
* ベアラトークン

Adobe I/Oとの統合は、これらの項目と、JSON Web Token(JWT)を使用してベアラトークンをリクエストする方法を提供します。

* JWTについて詳しくは、[JSON Web Tokensの概要](https://jwt.io/introduction/)を参照してください。
* Places Serviceの統合を作成するには、下の&#x200B;*Places Service統合の作成*&#x200B;の節を参照してください。
* APIキーの統合、JWTの生成、および公開鍵証明書について詳しくは、[Adobe I/O認証の概要](https://www.adobe.io/apis/cloudplatform/console/authentication/gettingstarted.html)を参照してください。

>[!IMPORTANT]
>
>Adobe I/Oコンソールにログインできない場合、またはPlaces Serviceが&#x200B;*統合の作成ページ*&#x200B;のオプションでない場合は、[WebサービスAPIの概要](/help/web-service-api/places-web-services.md)の&#x200B;*組織要件*&#x200B;を参照してください。

## Places Service統合の作成

Places Serviceの統合を作成するには、次のタスクを実行します。

### 公開鍵と秘密鍵のペアを生成する

Places Serviceの統合を作成するには、公開鍵と秘密鍵のペアが必要です。 これらのペアは購入することも、独自の自己署名付きキーを生成することもできます。

独自の自己署名付きキーを生成するには：

1. ターミナルウィンドウで、次の各行をコピーして貼り付け、各行を貼り付けた後に&#x200B;**[!UICONTROL Enter]**&#x200B;キーを押します。

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

   OpenSSLについて詳しくは、[OpenSSL](https://www.openssl.org/)を参照してください。

   >[!IMPORTANT]
   >
   >指定する情報は、キーに組み込まれます。

1. `.key`ファイルと`.crt`ファイルが存在するディレクトリに移動します。

   例えば、MacOSでは、**[!UICONTROL Macintosh HD]** > **[!UICONTROL users]** > **[!UICONTROL （ユーザー名）]** > **[!UICONTROL Keys]**&#x200B;に移動します。

次のビデオでは、キーペアの生成プロセスを順を追って説明します。

![統合ビデオ](/help/assets/places_integration_video.gif)

### Adobe I/OコンソールでPlaces Service統合を作成する

Places Service統合を作成するには：

1. [https://console.adobe.io](https://console.adobe.io)に移動し、Adobe IDにサインインします。
1. [**クイック開始**]セクションで[**統合を作成**]をクリックします。
1. 「**[!UICONTROL API にアクセス]**」を選択し、「**[!UICONTROL 続行]**」をクリックします。

   **[!UICONTROL デフォルトの場所は]** APIにアクセスします。

1. 複数のExperience Cloud組織にアクセスできる場合は、右上のドロップダウンリストからその組織を選択します。
1. **[!UICONTROL Experience Cloud]**&#x200B;の下で、統合するAdobeサービスとして「**[!UICONTROL サービス]**&#x200B;を配置」を選択し、「**[!UICONTROL 続行]**」をクリックします。
1. 「**[!UICONTROL 新しい統合]**」を選択し、「**[!UICONTROL 続行]**」をクリックします。
1. [新しい統合の作成]画面で、名前と説明を入力します。
1. 上で作成した`xxxx_public.crt`ファイルを&#x200B;**[!UICONTROL 公開鍵証明書]**&#x200B;ドロップゾーンにドラッグ&amp;ドロップします。
1. 製品プロファイルを選択します。

   選択するプロファイルが不明な場合は、システム管理者に問い合わせてください。
1. ページの下部にある「**[!UICONTROL 統合を作成]**」をクリックします。
1. 数秒後、*統合の作成*&#x200B;画面で、次のメッセージが表示されることを確認します。

   `Your integration has been created.`

1. 統合の詳細ページが上部に統合の名前と共に表示されます。

   「**[!UICONTROL 概要]**」タブはデフォルトで表示され、APIキー、組織ID、テクニカルアカウントID、および統合に関するその他の詳細が表示されます。

### 組織IDとAPIキーを記録します

1. 統合の詳細ページで、「**[!UICONTROL サービス]**」タブをクリックし、「**[!UICONTROL 設定済みのサービス]**」の下に「**[!UICONTROL サービス]**&#x200B;を配置」が表示されることを確認します。
1. 「**[!UICONTROL 概要]**」タブで、APIキー（クライアントID）と組織IDを探して記録します。

   これらのIDは、各Places Service REST API要求に必要です。

![](/help/assets/places_orgid_api-key.png)

### JWTトークンの生成

統合の詳細ページで、「**[!UICONTROL JWT]**」タブをクリックし、JWTを生成して交換URLを指定することで統合をテストできるようにします。

JWTトークンを生成するには：

1. テキストエディタで、上で作成した`private.key`ファイルを開きます。
1. 「**[!UICONTROL JWT]**」タブで、キーの内容をコピーし、「**[!UICONTROL 秘密鍵を貼り付け]**」フィールドに貼り付けます。
1. 「**[!UICONTROL JWT]**&#x200B;を生成」をクリックします。
1. 「**[!UICONTROL CURL コマンドの例]**」セクションで、「**[!UICONTROL コピー]**」をクリックし、コマンドプロンプトまたはターミナルウィンドウに内容を貼り付けます。
1. キーボードの&#x200B;**[!UICONTROL Enter]**&#x200B;キーを押して、コマンドを実行します。
1. `"token_type": "bearer"`と`"access_token"`の値を探します。

   bearerアクセストークンの値は、Places Service APIリクエストで使用する値です。

>[!IMPORTANT]
>
>Adobeアクセストークンは24時間有効&#x200B;****&#x200B;のみなので、サンプルのCURLコマンドを保存します（手順5）。 アクセストークンが無効になった場合は、トークンを再生成する必要があります。