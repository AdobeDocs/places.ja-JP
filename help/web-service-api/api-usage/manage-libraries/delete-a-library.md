---
title: ライブラリの削除
description: Places REST APIを使用してライブラリを削除します。
exl-id: ad45ea38-9e12-43d7-b05f-17d3e40abaf5
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: d8704da9c84a066f72471421290d4b46c65f41e1
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 4%
---
# ライブラリの削除 {#delete-a-library}

ライブラリを削除できるDELETE メソッド。

## リクエスト

```text
DELETE https://api-places.adobe.io/places/placesapi/v1/libraries/<lIBRARYID>
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

このAPIをテストするには、次のCURL コマンドを使用します。

```text
curl -X DELETE 'https://api-places.adobe.io/places/placesapi/v1/libraries/<LIBRARYID>' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>'
```

>[!IMPORTANT]
>
>`<lIBRARYID>`、`<API KEY>`、`<TOKEN>`、`<ORGID>`などの変数を実際の値に置き換えます。
