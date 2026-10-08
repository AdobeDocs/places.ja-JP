---
title: ライブラリのランクを取得
description: Places REST APIを使用して、ライブラリのランクを取得します。
exl-id: c0abedd0-5ff4-4a01-9f8d-e3d17ea53a97
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: d8704da9c84a066f72471421290d4b46c65f41e1
workflow-type: tm+mt
source-wordcount: '41'
ht-degree: 9%
---
# ライブラリのランクを取得 {#get-library-rank}

ライブラリをランク付けできるGET メソッド。

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

## CURL コマンド

```
curl -X GET 'https://api-places.adobe.io/places/placesapi/v1/libraries/rank ' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>'
```

>[!IMPORTANT]
>
>`<API KEY>`、`<TOKEN>`、`<ORGID>`などの変数を実際の値に置き換えます。
