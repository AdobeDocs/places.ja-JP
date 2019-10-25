---
title: POIの削除
seo-title: POIの削除
description: Places REST APIを使用してPOIを削除します。
seo-description: Places REST APIを使用してPOIを削除します。
translation-type: tm+mt
source-git-commit: 6ae0c8d90cad4c437e1db7f562a0bc9c6b072ce6

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

