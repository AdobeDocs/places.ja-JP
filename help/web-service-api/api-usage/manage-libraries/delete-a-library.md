---
title: ライブラリの削除
description: Places REST API を使用してライブラリを削除します。
exl-id: ad45ea38-9e12-43d7-b05f-17d3e40abaf5
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 4%

---

# ライブラリの削除 {#delete-a-library}

ライブラリを削除できるDELETEメソッド。

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

## 応答のサンプル

```text
If successful a Status of "204 No Content" is returned.
```

## CURL コマンド

次の CURL コマンドを使用して、この API をテストします。

```text
curl -X DELETE 'https://api-places.adobe.io/places/placesapi/v1/libraries/<LIBRARYID>' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>'
```

>[!IMPORTANT]
>
>変数（`<lIBRARYID>`、`<API KEY>`、`<TOKEN>`、`<ORGID>` など）を実際の値に置き換えます。
