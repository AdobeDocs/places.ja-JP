---
title: 組織内のすべてのライブラリを読み取る
seo-title: 組織内のすべてのライブラリを読み取る
description: Places REST APIを使用して、組織内のすべてのライブラリを読み取ります。
seo-description: Places REST APIを使用して、組織内のすべてのライブラリを読み取ります。
translation-type: tm+mt
source-git-commit: ef3d77eba407013e1f701ed001ef9ab7b3818e07

---


# 組織内のすべてのライブラリを読み取る

組織内のすべてのライブラリの詳細を返すGETメソッド。

## リクエスト

```text
GET https://api-places.adobe.io/places/placesapi/v1/libraries
```

## ヘッダー

```text
-H' Content-Type: application/json'  -H 'Authorization: Bearer <TOKEN>'  -H 'x-api-key: <API KEY>'  -H 'x-gw-ims-org-id: <ORGID>'  -H 'Accept-Language: en-US'
```

## 応答のサンプル

```text
[    {        "id": "5abb5c6d-ce4f-43f3-a253-120ae883777f",        "name": "Restaurants",        "customerID": "777F20F55BACA09E0A495D8F@AdobeOrg",        "poiCount": 1    },    {        "id": ""9aa7f663-35cc-4de6-8643-ae7779f3bb87",        "name": "Gas stations",        "customerID": "777F20F55BACA09E0A495D8F@AdobeOrg",        "poiCount": 30    },    {        "id": "6efd87bc-c9c4-4ff3-9503-051bfbc81777",        "name": "Coffee shops",        "customerID": "777F20F55BACA09E0A495D8F@AdobeOrg",        "poiCount": 25151    },    {        "id": "d1330287-79bd-44fb-b777-5e59ec37faad",        "name": "Theatres",        "customerID": "777F20F55BACA09E0A495D8F@AdobeOrg",        "poiCount": 0    }]
```

## CURLコマンド

このAPIをテストするには、次のCURLコマンドを使用します。

```text
curl -X GET 'https://api-places.adobe.io/places/placesapi/v1/libraries' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>'
```

>[!IMPORTANT]
>
>やなどの変数を実際 `<API KEY>`の値 `<TOKEN>,` に置 `<ORGID>` き換えます。