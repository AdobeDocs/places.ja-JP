---
title: ライブラリの更新
description: Places REST APIを使用してライブラリを更新します。
exl-id: 37ca2be2-39e1-4f8e-87c2-ef4cb366db0d
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: d8704da9c84a066f72471421290d4b46c65f41e1
workflow-type: tm+mt
source-wordcount: '48'
ht-degree: 6%
---
# ライブラリの更新 {#update-a-library}

ライブラリを更新できるPUT メソッド。

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

## 応答サンプル

```text
{       "id": "449f08f3-eff5-4658-9329-2d9687af777e",       "name": "Really facinating places",      "customerID": "777F20F55BACA09E0A495D8F@AdobeOrg",       "poiCount": 0  }
```

## CURL コマンド

このAPIをテストするには、次のCURL コマンドを使用します。

```text
curl -X PUT 'https://api-places.adobe.io/places/placesapi/v1/libraries/<LIBRARYID>' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' -d '{"name":"Updated Library Name"}' -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>`<lIBRARYID>`、`<API KEY>`、`<TOKEN>`、`<ORGID>`などの変数を実際の値に置き換えます。
