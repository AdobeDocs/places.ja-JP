---
title: POIの削除
description: Places REST APIを使用してPOIを削除します。
translation-type: tm+mt
source-git-commit: 8a84fe2dc5a0efe94ce3121e589524e3c7a80c5e
workflow-type: tm+mt
source-wordcount: '44'
ht-degree: 6%

---


# POIの削除 {#delete-a-poi}

POIを削除できるDELETE方法。

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

## 応答のサンプル

```text
If successful a Status of "204 No Content" is returned.
```

## CURLコマンド

次のCURLコマンドを使用してAPIをテストします。

```text
curl -X DELETE 'https://api-places.adobe.io/places/placesapi/v1/pois/<POIID>' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>'
```

>[!IMPORTANT]
>
>、 `<POIID>`、 `<API KEY>`およびを実際の値 `<TOKEN>``<ORGID>` に置き換えます。

