---
title: ライブラリの削除
seo-title: ライブラリの削除
description: Places REST APIを使用してライブラリを削除します。
seo-description: Places REST APIを使用してライブラリを削除します。
translation-type: tm+mt
source-git-commit: ef3d77eba407013e1f701ed001ef9ab7b3818e07

---


# ライブラリの削除

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

## CURLコマンド

このAPIをテストするには、次のCURLコマンドを使用します。

```text
curl -X DELETE 'https://api-places.adobe.io/places/placesapi/v1/libraries/<LIBRARYID>' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>'
```

>[!IMPORTANT]
>
>、、などの変数を `<lIBRARYID>`実際の値 `<API KEY>`に `<TOKEN>`置き換 `<ORGID>`えてください。

