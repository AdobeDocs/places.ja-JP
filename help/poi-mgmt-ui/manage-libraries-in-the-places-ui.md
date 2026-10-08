---
title: Places サービス UIでのライブラリの管理
description: Places サービス UIを使用してライブラリを管理します。
exl-id: 2fb999b4-854a-430f-bb89-4c786d1a89cc
TQID: https://experienceleague.adobe.com/PP7P3aOL3EKSEPJWedHtfyHRzbCueMtNS-J7Ao4mawo
product_v2:
  - id: cb954087-f4fc-4456-afb9-e939cabcdc79
    internal-label: Journey Optimizer
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
    internal-label: CX Enterprise
  - id: dc5cf79d-43c4-4731-bffa-1df5d7549cb1
    internal-label: Adobe Sign
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
feature_v2:
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
    internal-label: Data collection
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
    internal-label: Places
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
source-git-commit: d8704da9c84a066f72471421290d4b46c65f41e1
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 14%
---
# ライブラリの管理 {#manage-libraries-places-ui}

ライブラリはPOIの集まりです。 1つのライブラリには最大150,000個のPOIを設定でき、Experience Cloud組織ごとに最大100個のライブラリを設定できます。

POIをライブラリに整理する方法は、組織にとって最も有用な方法に応じて異なります。 一部の顧客は、モバイルアプリごとに個別のライブラリを作成することを好むかもしれません。また、他の顧客は、コーヒーショップ、公園、ホテルなどの特定の種類のPOIをグループ化するためにライブラリを使用するかもしれません。 たとえば、大手エンターテインメント企業であれば、あるライブラリの屋外会場と、別のライブラリの小売店からなるライブラリを有しているかもしれません。 市政府は、市内のすべての建物で構成される図書館と、市内のすべての公園で構成される別の図書館を持っている場合があります。

ライブラリは、次のように定義されます。

| キー： | 説明 : |
| :--- | :--- |
| ID | 作成時にライブラリに割り当てられた一意のID |
| 名前 | 図書館に付けられた親しみやすい名前 |
| ランキング | 組織内に重複するジオフェンスがない場合、これらのランキングは無視できます。 重複する POI がある場合は、各ジオフェンスを別々のライブラリに配置し、ジオフェンスを相対的に重み付けできるようにすることをお勧めします。 ユーザーは、一度に 1 つのジオフェンス内にしか存在できません。 <br><br>ユーザーが属するジオフェンスの最上位ランキングによって、現在のジオフェンスのメンバーシップが決まります。 同じライブラリランキングを持つジオフェンスがある場合、最小ジオフェンスはユーザーの現在のジオフェンスです。 <br><br>SDKは&#x200B;*最後に入力した*&#x200B;および&#x200B;*最後に離脱した* POIも認識しているため、POIとのユーザーインタラクションに基づいてルールを適用する方法を完全に制御できます。 |

## ライブラリの作成

1. Adobe IDでPlacesにログインします。
1. 右上の「**[!UICONTROL ...]**」 > 「**[!UICONTROL ライブラリを管理]**」をクリックします。
1. 「**[!UICONTROL 新規]**」をクリックします。
1. 名前を入力します。
1. 「**[!UICONTROL 確認]**」をクリックします。

## 場所UIでのライブラリのランクの変更

1. Adobe IDでPlacesにログインします。
1. 右上の「**[!UICONTROL ...]**」 > 「**[!UICONTROL ライブラリを管理]**」をクリックします。
1. ライブラリ名の左側にあるアイコンをクリックし、ライブラリを新しいランクにドラッグします。

## ライブラリ名の変更

1. Adobe IDでPlacesにログインします。
1. 右上の「**[!UICONTROL ...]**」 > 「**[!UICONTROL ライブラリを管理]**」をクリックします。
1. 削除するライブラリを探します。
1. **[!UICONTROL ...]**&#x200B;をクリックし、**[!UICONTROL 名前を変更]**&#x200B;を選択します。
1. 名前を更新し、**[!UICONTROL 保存]**&#x200B;をクリックします。

## ライブラリの削除

1. Adobe IDでPlacesにログインします。
1. 右上の「**[!UICONTROL ...]**」 > 「**[!UICONTROL ライブラリを管理]**」をクリックします。
1. 削除するライブラリを探します。
1. **[!UICONTROL ...]**&#x200B;をクリックし、**[!UICONTROL 削除]**&#x200B;を選択します。
