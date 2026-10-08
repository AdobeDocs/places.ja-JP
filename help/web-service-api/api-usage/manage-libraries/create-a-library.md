---
title: ライブラリの作成
description: Places REST APIを使用してライブラリを作成します。
exl-id: 155cc6e6-9254-4389-bb02-e526d15908f4
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: d8704da9c84a066f72471421290d4b46c65f41e1
workflow-type: tm+mt
source-wordcount: '48'
ht-degree: 18%
---
# ライブラリの作成 {#create-a-library}

ライブラリを作成できるPOST メソッド。

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

## 応答サンプル

```text
{       "id": "449f08f3-eff5-4658-9329-2d9687af777e",       "name": "Facinating places",      "customerID": "777F20F55BACA09E0A495D8F@AdobeOrg",       "poiCount": 0  }
```

## CURL コマンド

このAPIをテストするには、次のCURL コマンドを使用します。

```text
curl -X POST 'https://api-places.adobe.io/places/placesapi/v1/libraries' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' -d '{"name":"New Library Name"}' -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>`<API KEY>`、`<TOKEN>`、`<ORGID>`などの変数を実際の値に置き換えます。
