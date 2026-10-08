---
title: POIの削除
description: Places REST APIを使用してPOIを削除します。
exl-id: 0325eb3b-f9b2-4b21-bed8-e318e8072a69
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: d8704da9c84a066f72471421290d4b46c65f41e1
workflow-type: tm+mt
source-wordcount: '44'
ht-degree: 4%
---
# POIの削除 {#delete-a-poi}

POIを削除できるDELETE メソッド。

## リクエスト

```text
DELETE https://api-places.adobe.io/places/placesapi/v1/pois/<POIID>
```

## ヘッダー

```text
-H' Content-Type: application/json'  
-H 'Authorization: Bearer <TOKEN>'  
-H 'x-api-key: <API KEY>'  
-H 'x-gw-ims-org-id: <ORGID>'  
-H 'Accept-Language: en-US'
```

## 応答サンプル

```text
If successful a Status of "204 No Content" is returned.
```

## CURL コマンド

APIをテストするには、次のCURL コマンドを使用します。

```text
curl -X DELETE 'https://api-places.adobe.io/places/placesapi/v1/pois/<POIID>' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>'
```

>[!IMPORTANT]
>
>`<POIID>`、`<API KEY>`、`<TOKEN>`、`<ORGID>`を実際の値に置き換えます。
