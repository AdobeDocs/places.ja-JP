---
title: 組織内のすべてのライブラリを読み取る
description: Places REST API を使用して、組織内のすべてのライブラリを読み取ります。
exl-id: 3384e1f2-9626-498d-85f7-84569d869c2c
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '60'
ht-degree: 6%

---

# 組織内のすべてのライブラリを読み取る {#read-all-lib-in-org}

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

## CURL コマンド

この API をテストするには、次の CURL コマンドを使用します。

```text
curl -X GET 'https://api-places.adobe.io/places/placesapi/v1/libraries' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>'
```

>[!IMPORTANT]
>
>次のような変数を置き換える `<API KEY>`, `<TOKEN>,` および `<ORGID>` を実際の値に置き換えます。
