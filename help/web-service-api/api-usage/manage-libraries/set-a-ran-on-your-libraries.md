---
title: ライブラリにランクを設定する
seo-title: ライブラリにランクを設定する
description: Places REST APIを使用してライブラリにランクを設定します。
seo-description: Places REST APIを使用してライブラリにランクを設定します。
translation-type: tm+mt
source-git-commit: 6ae0c8d90cad4c437e1db7f562a0bc9c6b072ce6

---


# ライブラリにランクを設定する

すべてのライブラリにランク順を設定できるPUTメソッド。

## リクエスト

`PUT https://api-places-dev.adobe.io/places/placesapi/v1/libraries/rank`

## ヘッダー

```-H Content-Type: application/json'
-H 'Authorization: Bearer <TOKEN>`  
-H 'x-api-key: <API KEY>'  
-H 'x-gw-ims-org-id: <ORGID>'  
-H 'Accept-Language: en-US'
```

## PUTデータ

```
"library_rank_order": ["dfcc5270-1d6d-4bc9-9cd9-85ecd5ebc12b","ea45781f-26af-44b1-b4f8-43baf5f0fe28"]  
}
```

## レスポンスのサンプル

```
{"library_rank_order" ["dfcc5270-1d6d-4bc9-9cd9-85ecd5ebc12b","ea45781f-26af-44b1-b4f8-43baf5f0fe28"]}
```

## CURLコマンド

```
curl -X PUT `'https://api-places.adobe.io/places/placesapi/v1/libraries/rank'` -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' -d '{"library_rank_order": ["dfcc5270-1d6d-4bc9-9cd9-85ecd5ebc12b","ea45781f-26af-44b1-b4f8-43baf5f0fe28"]}' -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>、などの変数を `<API KEY>`実際の `<TOKEN>`値に `<ORGID>` 置き換えます。

