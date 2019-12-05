---
title: POIの削除
description: Places REST APIを使用してPOIを削除します。
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# POIの削除

POIを削除できるDELETEメソッド。

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
>、、お `<POIID>`よびを実 `<API KEY>`際の値 `<TOKEN>``<ORGID>` に置き換えます。

