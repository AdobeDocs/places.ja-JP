---
title: 複数のPOIの削除
seo-title: 複数のPOIの削除
description: 複数のPOIを削除するには、バッチAPIを使用します。
seo-description: 複数のPOIを削除するには、バッチAPIを使用します。
translation-type: tm+mt
source-git-commit: 26b0cab7bdada26a7598b20623095b72f7c8d334

---



# 複数のPOIの削除 {#delete-multiple-pois}

複数のPOIを削除できるPOSTメソッド。

## リクエスト

```text
POST https://api-places.adobe.io/places/placesapi/v1/pois/batchDelete
```

## ヘッダー

```text
-H' Content-Type: application/json'  -H 'Authorization: Bearer <TOKEN>'  -H 'x-api-key: <API KEY>'  -H 'x-gw-ims-org-id: <ORGID>'  -H 'Accept-Language: en-US'
```

## 本文

```text
{  "ids": [    "<POIID>",    "<POIID>",    .    .    .    "<POIID>",    "<POIID>"  ]}
```

## 応答のサンプル

```text
If successful a Status of "204 No Content" is returned.
```

## CURLコマンド

このAPIをテストするには、次のCURLコマンドを使用します。

```text
curl -X POST 'https://api-places.adobe.io/places/placesapi/v1/pois/batchDelete' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' --data-binary "@<PATHTOBATCHDELETEJSONFILE>" -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>、、お `<API KEY>`よびを実 `<TOKEN>`数値で `<ORGID>``<PATHTOBATCHDELETEJSONFILE>` 置き換えます。

## サンプルJSONファイル

次に、 `batchDelete` APIのサンプルJSONファイルを示します。

```text
{​"ids":["31a49d5c-c6ad-46ae-b88d-a6912a8a6b2f","6a78a729-7973-4373-9199-36da18cc5b8c","74eaa3da-2464-4298-9b6d-5376fa7ea00f"]​}
```
