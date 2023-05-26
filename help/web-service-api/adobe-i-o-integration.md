---
title: Adobe I/O統合の概要
description: 統合の作成に関するAdobe I/O。
exl-id: d7d31938-6c0e-40f8-a9d3-30af96043119
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '879'
ht-degree: 7%

---

# 統合の概要と前提条件 {#integration-prereqs}

この情報では、Adobe I/Oと Places Service の統合の作成方法を示します。

## ユーザーアクセスの前提条件

組織のシステム管理者に問い合わせて、次のタスクが完了していることを確認します。

* Places コアサービスが組織の Admin Console に表示されます。
* 組織に追加されました。
* 組織の Places コアサービスにユーザーとして追加されている。

   詳しくは、 *Places サービスと開発者プロファイルへのExperience Platform Launchまたは開発者の追加* in [Places Service へのアクセス権を取得](/help/places-gain-access.md).

* 組織の Places コアサービスに開発者として追加されている。

   開発者の追加について詳しくは、 *Places サービスと開発者プロファイルへのExperience Platform Launchまたは開発者の追加* in [Places Service へのアクセス権を取得](/help/places-gain-access.md).

   開発者の役割について詳しくは、 [開発者の管理](https://helpx.adobe.com/jp/enterprise/using/manage-developers.html).

### REST API リクエスト

Places Service REST API への各リクエストには、次の項目が必要です。

* 組織 ID
* API キー
* bearer トークン

Adobe I/Oとの統合により、これらの項目と、JSON Web トークン (JWT) を使用して bearer トークンをリクエストする方法が提供されます。

* JWT について詳しくは、 [JSON Web トークンの概要](https://jwt.io/introduction/).
* Places Service の統合を作成するには、 *Places Service 統合の作成* 」の節を参照してください。
* API キーの統合、JWT および公開鍵証明書の生成について詳しくは、 [Adobe I/O認証の概要](https://www.adobe.io/apis/cloudplatform/console/authentication/gettingstarted.html).

>[!IMPORTANT]
>
>Adobe I/Oコンソールにログインできない場合、または *統合を作成ページ*&#x200B;を参照してください。 *組織の要件* in [Web サービス API の概要](/help/web-service-api/places-web-services.md).

## Places サービス統合の作成

Places Service 統合を作成するには、次のタスクを実行します。

### 公開鍵と秘密鍵のペアを生成する

Places Service 統合を作成するには、公開鍵と秘密鍵のペアが必要です。 これらのペアは購入することも、独自の自己署名付きキーを生成することもできます。

独自の自己署名付きキーを生成するには：

1. ターミナルウィンドウで、次の各行をコピーして貼り付け、を押します。 **[!UICONTROL 入力]** 各行を貼り付けた後：

   ```text
      mkdir keys
      cd keys
      openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout places_integration_test_private.key -out    places_integration_test_public.crt
   ```

   >[!IMPORTANT]
   >
   >キーを参照しやすいように名前を付け、フォルダーに保存することをお勧めします。 複数の統合を作成する場合、どのキーがどの統合に属しているかを簡単に識別および管理できます。

1. OpenSSL から要求された情報を入力します。

   ```text
   Country Name (2 letter code:  // Example: US
   State or Province Name (full name):  // Example: California
   Locality Name (eg, city):  // Example: San Jose
   Organization Name (eg, company):  // Example: Places
   Organizational Unit Name (eg, section):  // Example: Engineering
   Common Name (eg, fully qualified host name):  // Example: places.com
   Email Address:  // Example:  poi@places.com
   ```

   OpenSSL について詳しくは、 [OpenSSL](https://www.openssl.org/).

   >[!IMPORTANT]
   >
   >入力した情報は、キーに組み込まれます。

1. を含むディレクトリに移動します。 `.key` および `.crt` ファイルが見つかります。

   例えば、MacOSで、 **[!UICONTROL Macintosh HD]** > **[!UICONTROL ユーザー]** > **[!UICONTROL （ユーザー名）]** > **[!UICONTROL キー]**.

次のビデオでは、キーペアを生成するプロセスを説明します。

![統合ビデオ](/help/assets/places_integration_video.gif)

### Adobe I/Oコンソールでの Places Service 統合の作成

Places Service 統合を作成するには、次の手順を実行します。

1. に移動します。 [https://console.adobe.io](https://console.adobe.io) をクリックし、Adobe IDでログインします。
1. 内 **クイックスタート** セクションで、 **統合の作成**.
1. 「**[!UICONTROL API にアクセス]**」を選択し、「**[!UICONTROL 続行]**」をクリックします。

   **[!UICONTROL API へのアクセス]** はデフォルトの場所です。

1. 複数の組織にアクセスできる場合は、右上のExperience Cloudドロップダウンリストから組織を選択します。
1. の下 **[!UICONTROL Experience Cloud]**&#x200B;を選択します。 **[!UICONTROL Places Service]** を統合するAdobe サービスとして選択し、 **[!UICONTROL 続行]**.
1. 選択 **[!UICONTROL 新しい統合]** をクリックし、 **[!UICONTROL 続行]**.
1. 「新しい統合を作成」画面で、名前と説明を入力します。
1. をドラッグ&amp;ドロップします。 `xxxx_public.crt` 上で作成したファイルを **[!UICONTROL 公開鍵証明書]** ドロップゾーン。
1. 製品プロファイルの選択.

   選択するプロファイルが不明な場合は、システム管理者に問い合わせてください。
1. ページの下部で、 **[!UICONTROL 統合の作成]**.
1. 数秒後、 *統合が作成されました* 画面で、次のメッセージが表示されることを確認します。

   `Your integration has been created.`

1. 統合の詳細ページが上部に統合の名前と共に表示されます。

   この **[!UICONTROL 概要]** 「 」タブはデフォルトで表示され、API キー、組織 ID、テクニカルアカウント ID、統合に関するその他の詳細が表示されます。

### 組織 ID と API キーを記録します。

1. 統合の詳細ページで、 **[!UICONTROL サービス]** タブで確認し、 **[!UICONTROL Places Service]** が **[!UICONTROL 構成済みサービス]**.
1. の **[!UICONTROL 概要]** タブで、API キー（クライアント ID）と組織 ID を探して記録します。

   これらの ID は、Places Service REST API リクエストごとに必要です。

![](/help/assets/places_orgid_api-key.png)

### JWT トークンの生成

統合の詳細ページで、 **[!UICONTROL JWT]** 」タブをクリックし、JWT を生成して exchange URL を指定することで統合をテストできるようにします。

JWT トークンを生成するには：

1. テキストエディターで、 `private.key` 上で作成したファイル。
1. 「**[!UICONTROL JWT]**」タブで、キーの内容をコピーし、「**[!UICONTROL 秘密鍵を貼り付け]**」フィールドに貼り付けます。
1. クリック **[!UICONTROL JWT を生成]**.
1. 「**[!UICONTROL CURL コマンドの例]**」セクションで、「**[!UICONTROL コピー]**」をクリックし、コマンドプロンプトまたはターミナルウィンドウに内容を貼り付けます。
1. を押して、コマンドを実行します。 **[!UICONTROL 入力]** キーボードで
1. を `"token_type": "bearer"` そして `"access_token"` の値です。

   bearer アクセストークンの値は、Places Service API リクエストで使用する値です。

>[!IMPORTANT]
>
>Adobeアクセストークンが有効です **のみ** 24 時間の場合は、サンプルの CURL コマンド（手順 5）を保存します。 アクセストークンが無効になった場合は、トークンを再生成する必要があります。
