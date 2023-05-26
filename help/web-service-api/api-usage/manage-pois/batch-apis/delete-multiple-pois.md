---
title: 複数の POI を削除
description: バッチ API を使用して複数の POI を削除します。
exl-id: f170b722-e6f4-42a2-b3a6-1bf56965eb17
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '56'
ht-degree: 14%

---

# 複数の POI を削除 {#delete-multiple-pois}

複数の POI をPOSTできる削除メソッド。

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

## CURL コマンド

この API をテストするには、次の CURL コマンドを使用します。

```text
curl -X POST 'https://api-places.adobe.io/places/placesapi/v1/pois/batchDelete' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' --data-binary "@<PATHTOBATCHDELETEJSONFILE>" -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>置換 `<API KEY>`, `<TOKEN>`, `<ORGID>`、および `<PATHTOBATCHDELETEJSONFILE>` 実際の値を持つ

## サンプル JSON ファイル

次に、 `batchDelete` API:

```text
{​"ids":["31a49d5c-c6ad-46ae-b88d-a6912a8a6b2f","6a78a729-7973-4373-9199-36da18cc5b8c","74eaa3da-2464-4298-9b6d-5376fa7ea00f"]​}
```
