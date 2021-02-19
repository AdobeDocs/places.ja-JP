---
title: ライブラリの更新
description: Places REST APIを使用してライブラリを更新します。
translation-type: tm+mt
source-git-commit: 8a84fe2dc5a0efe94ce3121e589524e3c7a80c5e
workflow-type: tm+mt
source-wordcount: '48'
ht-degree: 10%

---


# ライブラリの更新{#update-a-library}

ライブラリを更新できるPUT方法。

## リクエスト

```text
PUT https://api-places.adobe.io/places/placesapi/v1/libraries/<lIBRARYID>
```

## ヘッダー

```text
-H' Content-Type: application/json'  -H 'Authorization: bearer <TOKEN>'  -H 'x-api-key: <API KEY>'  -H 'x-gw-ims-org-id: <ORGID>'  -H 'Accept-Language: en-US'
```

## 本文

```text
{"name": "<NEW_LIBRARY_NAME>"}
```

## 応答のサンプル

```text
{       "id": "449f08f3-eff5-4658-9329-2d9687af777e",       "name": "Really facinating places",      "customerID": "777F20F55BACA09E0A495D8F@AdobeOrg",       "poiCount": 0  }
```

## CURLコマンド

このAPIをテストするには、次のCURLコマンドを使用します。

```text
curl -X PUT 'https://api-places.adobe.io/places/placesapi/v1/libraries/<LIBRARYID>' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' -d '{"name":"Updated Library Name"}' -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>`<lIBRARYID>`、`<API KEY>`、`<TOKEN>`、`<ORGID>`などの変数を実際の値に置き換えます。

