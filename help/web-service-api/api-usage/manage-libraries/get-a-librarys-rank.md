---
title: ライブラリのランクを取得する
description: Places REST APIを使用してライブラリのランクを取得します。
translation-type: tm+mt
source-git-commit: 8a84fe2dc5a0efe94ce3121e589524e3c7a80c5e

---


# ライブラリのランクを取得する {#get-library-rank}

ライブラリのランク付けを可能にするGETメソッド。

## リクエスト

`GET https://api-places.adobe.io/places/placesapi/v1/libraries/rank`

## ヘッダー

```
-H Content-Type: application/JSON  
-H 'Authorization: Bearer <TOKEN>'  
-H 'x-api-key: <API KEY>'  
-H 'x-gw-ims-org-id: <ORGID>'  
-H 'Accept-Language: en-US'
```

## レスポンスのサンプル

```
{"library_rank_order":["ea45781f-26af-44b1-b4f8-43baf5f0fe28","dfcc5270-1d6d-4bc9-9cd9-85ecd5ebc12b"]}
```

## CURLコマンド

```
curl -X GET 'https://api-places.adobe.io/places/placesapi/v1/libraries/rank ' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>'
```

>[!IMPORTANT]
>
>、などの変数を `<API KEY>`実際の `<TOKEN>`値に `<ORGID>` 置き換えます。

