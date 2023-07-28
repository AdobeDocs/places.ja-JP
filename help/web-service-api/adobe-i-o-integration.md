---
title: Adobe Developer Project の概要
description: Adobe Developer API プロジェクトの作成に関する情報です。
exl-id: d7d31938-6c0e-40f8-a9d3-30af96043119
source-git-commit: 3d477c6133b74a7e6380d0db1af5125aaa844035
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 2%

---

# Places API アクセスの概要と前提条件 {#developer-prereqs}

この情報では、Adobe Developer Console でプロジェクトを作成し、Places API リクエストで使用するアクセストークンを生成する方法について説明します。

## ユーザーアクセスの前提条件

組織のシステム管理者に問い合わせて、次のタスクが完了していることを確認します。

* 組織に追加されました。
* Adobe Experience Platform内のプロファイルに追加されている。

  詳しくは、 *Places サービスと開発者プロファイルへのExperience Platform Launchまたは開発者の追加* in [Places Service へのアクセス権を取得する](/help/places-gain-access.md).

### REST API リクエスト

Places Service REST API への各リクエストには、次の項目が必要です。

* 組織 ID
* API キー（クライアント ID とも呼ばれます）
* クライアント秘密鍵
* bearer トークン

を持つプロジェクト [Adobe Developer console](https://developer.adobe.com/console) は、これらの項目を提供します。

* Places Service API 用のプロジェクトを作成するには、 *Places Service プロジェクトの作成* 」の節を参照してください。

>[!IMPORTANT]
>
>にログインできない場合は、 [Adobe Developer console](https://developer.adobe.com/console)、または Places Service が *統合を作成ページ*&#x200B;を参照してください。 *組織の要件* in [Web サービス API の概要](/help/web-service-api/places-web-services.md).

## Places Service API プロジェクトの作成

Places Service API 用のプロジェクトを作成するには、以下の手順を実行します。

1. にログインします。 [Adobe Developer Web サイト](https://developer.adobe.com) Adobe IDと
2. クリック **[!UICONTROL コンソール]** をクリックします。
3. 複数のAdobe組織に割り当てられている場合は、ページの右上隅にあるドロップダウンリストから正しい組織を選択します。
4. 次をクリック： **[!UICONTROL 新規プロジェクトを作成]** 」ボタンをクリックします。
5. クリック **[!UICONTROL API を追加]** 」ボタンをクリックします。
6. Places API を選択するには、ページを下にスクロールして Places カードを表示し、カードの右上隅にあるチェックボックスをクリックします。
7. 「**[!UICONTROL Next]**」ボタンをクリックします。
8. 「 OAuth Server-to-Server 」オプションを選択します（選択肢がある場合）。
9. 秘密鍵証明書に名前を付け、 **[!UICONTROL 次へ]**.
10. プロファイルを選択します（複数ある場合は、「 」を選択します）。
11. クリック **[!UICONTROL API の保存と設定]**.
12. 左側のパネルで、 **[!UICONTROL OAuth サーバー間通信]** CREDENTIALS の下のリンク
13. このページでは、次の情報を提供します。
   * Places Service REST API リクエストで使用するアクセストークンを生成する方法です。
   * 独自のコードからアクセストークンを生成する方法の例については、 curl コマンドを参照してください。
   * クライアント ID（API キーとも呼ばれます）を表示します。
   * クライアントシークレットを表示
   * 組織 ID を表示する
   * これらはすべて、Places Service REST API へのリクエストで必要です。
14. ウィンドウの左上にあるパスのプロジェクト名をクリックして、プロジェクトの名前を分かりやすい名前に変更できます
15. 次に、 **[!UICONTROL プロジェクトを編集]** 」ボタンをクリックします。

>[!IMPORTANT]
>
>Adobeアクセストークンが有効です **のみ** 24 時間の場合は、サンプルの CURL コマンド（手順 5）を保存します。 アクセストークンが無効になった場合は、トークンを再生成する必要があります。
