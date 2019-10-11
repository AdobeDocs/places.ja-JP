---
title: ライブラリのランクを取得する
seo-title: ライブラリのランクを取得する
description: Places REST APIを使用してライブラリのランクを取得します。
seo-description: Places REST APIを使用してライブラリのランクを取得します。
translation-type: tm+mt
source-git-commit: ef3d77eba407013e1f701ed001ef9ab7b3818e07

---


# ライブラリのランクを取得する

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
