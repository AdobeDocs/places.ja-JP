---
title: 既存のPOIの管理
description: Places サービス UIでは、既存のPOIを編集、削除またはフィルタリングできます。
exl-id: a4cf28ae-1e3c-4724-bca3-ac1d0cd6da09
TQID: https://experienceleague.adobe.com/2VnBQ5-flpx5cyeK3n5b3AOKqnt7RVkdqFBXYa9O5Ys
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: dc5cf79d-43c4-4731-bffa-1df5d7549cb1
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2:
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 408
ht-degree: 6%

---

# 既存のPOIの管理 {#managing-existing-pois}

POIとライブラリは、Places UIを使用してPlaces データベースで作成および管理されます。

## POIの編集

1. Adobe IDを使用してPlacesにログインします。
1. Adobe IDを使用してPlaces サービスにログインします。
1. 右上の箇条書きリストのようなアイコンをクリックします。
1. 編集するPOIを探します。
1. **[!UICONTROL ...]**&#x200B;をクリックし、**[!UICONTROL 詳細を表示]**&#x200B;を選択します。
1. 情報を更新し、**[!UICONTROL 保存]**&#x200B;をクリックします。

## POIの削除

1. Adobe IDを使用してPlacesにログインします。
1. Adobe IDを使用してPlaces サービスにログインします。
1. 右上の箇条書きリストのようなアイコンをクリックします。
1. 削除するPOIを探します。
1. **[!UICONTROL ...]**&#x200B;をクリックし、**[!UICONTROL 削除]**&#x200B;を選択します。

## 都市、州、国、メタデータごとにPOIをフィルタリング

![POIのフィルター](/help/assets/filter_poi.png)

1. Adobe IDを使用してPlaces サービス UIにログインします。
1. 右上のフィルターアイコンをクリックします。
1. POIは、次のいずれかの方法でフィルタリングできます。

   * ライブラリ別：

     a. ライブラリを選択します。

   * プロパティ別：

     a. プロパティ ドロップダウンリストで、**[!UICONTROL 国]**、**[!UICONTROL 州]**、または&#x200B;**[!UICONTROL 都市]**&#x200B;を選択します。

     b. 次の行に値を入力します。

     例えば、**[!UICONTROL State]**&#x200B;を選択して&#x200B;**[!UICONTROL California]**&#x200B;と入力できます。

   * メタデータ：

     a. キーと値を入力します。

## ジオフェンス POIの定義

ジオフェンスはPOIの一種であり、次のキーに基づいてデータベースで定義されます。

| キー | 説明 | 必須？ |
| :--- | :--- | :--- |
| ID | 各POIに割り当てられた一意のID | ○ |
| 名前 | POIに割り当てられたわかりやすい名前。 | ○ |
| ライブラリ | 各POIには、組織用のライブラリを割り当てる必要があります。 | ○ |
| 半径 | POIの半径（メートル）。 | ○ |
| アイコン | POIのビジュアライゼーションの支援： | はい（割り当てられたデフォルト） |
| カラー | POIのビジュアライゼーションの支援： | はい（割り当てられたデフォルト） |
| カテゴリ | すべてのライブラリのすべてのPOIで共通するカテゴリの共通フレームワークを割り当てます。 | × |
| Address | 住所： | × |
| 市区町村 | POIの街。 | × |
| 都道府県/地域 | POIの州または地域。 | × |
| 国 | POIの国。 | × |
| 緯度 | POIの中心の緯度座標。 | ○ |
| 経度 | POIの中心の経度座標。 | ○ |
| メタデータ | POIに割り当てることができるカスタムキーと値のペア。 このメタデータにより、各ライブラリのPOIをグループ化し、下流のワークフローでルールやフィルターを使用できるようになります。例えば、誰かがタイプ =競合他社のPOIを入力したときにプッシュ通知を送信します。 | × |
