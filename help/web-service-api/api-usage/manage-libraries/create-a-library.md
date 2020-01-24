---
title: ライブラリの作成
description: Places REST APIを使用してライブラリを作成します。
translation-type: tm+mt
source-git-commit: 8a84fe2dc5a0efe94ce3121e589524e3c7a80c5e

---


# ライブラリの作成 {#create-a-library}

ライブラリを作成できるPOSTメソッドです。

## リクエスト

```text
POST https://api-places.adobe.io/places/placesapi/v1/libraries
```

## ヘッダー

```text
-H' Content-Type: application/json'  -H 'Authorization: Bearer <TOKEN>'  -H 'x-api-key: <API KEY>'  -H 'x-gw-ims-org-id: <ORGID>'  -H 'Accept-Language: en-US'
```

## 本文

```text
{"name": "<LIBRARY_NAME>"}
```

## 応答のサンプル

```text
{       "id": "449f08f3-eff5-4658-9329-2d9687af777e",       "name": "Facinating places",      "customerID": "777F20F55BACA09E0A495D8F@AdobeOrg",       "poiCount": 0  }
```

## CURLコマンド

このAPIをテストするには、次のCURLコマンドを使用します。

```text
curl -X POST 'https://api-places.adobe.io/places/placesapi/v1/libraries' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' -d '{"name":"New Library Name"}' -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>、などの変数を `<API KEY>`実際の `<TOKEN>`値に `<ORGID>` 置き換えます。

