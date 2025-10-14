---
title: Adobe Developer プロジェクトの概要
description: Adobe Developer API プロジェクトの作成に関する情報。
exl-id: d7d31938-6c0e-40f8-a9d3-30af96043119
source-git-commit: 3d477c6133b74a7e6380d0db1af5125aaa844035
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 1%

---

# API アクセスの概要と前提条件を配置します {#developer-prereqs}

この情報では、Adobe Developer Consoleでプロジェクトを作成し、Places API リクエストで使用されるアクセストークンを生成する方法について説明します。

## ユーザーアクセスの前提条件

組織のシステム管理者に、次のタスクが完了していることを確認します。

* あなたは組織に追加されました。
* Adobe Experience Platform内のプロファイルに追加されています。

  詳しくは、*Places Service へのアクセス権の取得 [&#x200B; の「Places Service およびExperience Platform Launchプロファイルへのユーザーまたは開発者の追加* を参照してください &#x200B;](/help/places-gain-access.md)。

### REST API リクエスト

Places Service REST API への各リクエストには、次の項目が必要です。

* 組織 ID
* API キー（クライアント ID とも呼ばれます）
* クライアント秘密鍵
* ベアラートークン

[Adobe Developer コンソール &#x200B;](https://developer.adobe.com/console) を含むプロジェクトは、次の項目を提供します。

* Places Service API のプロジェクトを作成するには、以下の *Places Service プロジェクトの作成* の節を参照してください。

>[!IMPORTANT]
>
>[Adobe Developer コンソール &#x200B;](https://developer.adobe.com/console) にログインできない場合、または Places Service が *統合を作成* ページで利用できない場合は、[Web サービス API の概要 &#x200B;](/help/web-service-api/places-web-services.md) の *組織の要件* を参照してください。

## Places Service API プロジェクトの作成

Places Service API 用のプロジェクトを作成するには、次の手順を実行します。

1. Adobe IDを使用して [&#128279;](https://developer.adobe.com)0&rbrace;Adobe Developer web サイトにログインします。
2. ページの右上隅にある「**[!UICONTROL コンソール]**」をクリックします。
3. 複数のAdobe組織に割り当てられている場合は、ページの右上隅にあるドロップダウンリストから正しい組織を選択します。
4. **[!UICONTROL 新規プロジェクトを作成]** ボタンをクリックします。
5. 新規プロジェクトの概要セクションの「**[!UICONTROL API を追加]**」ボタンをクリックします。
6. Places API を選択するには、ページを下にスクロールして Places カードを表示し、カードの右上隅にあるチェックボックスをクリックします。
7. 「**[!UICONTROL 次へ]**」ボタンをクリックします。
8. 「OAuth サーバー間」オプションを選択します（選択する場合）。
9. 資格情報に名前を付け、「次へ **[!UICONTROL をクリックし]** す。
10. プロファイルを選択します（複数ある場合はすべてが機能します）。
11. **[!UICONTROL API を保存して設定]** をクリックします。
12. 左側のパネルで、「資格情報」の下の **[!UICONTROL OAuth サーバー間]** リンクをクリックします
13. このページの主な機能は次のとおりです。
    * Places Service REST API リクエストで使用されるアクセストークンを生成する方法。
    * 独自のコードからアクセストークンを生成する方法の例として、curl コマンドを表示します。
    * クライアント ID （API キーとも呼ばれます）を表示します
    * クライアント秘密鍵の表示
    * 組織 ID を表示
    * これらはすべて、Places Service REST API へのリクエストで必要です。
14. ウィンドウの左上のパスにあるプロジェクト名をクリックすると、プロジェクトの名前をわかりやすいものに変更できます
15. 次に、ページの右上にある「**[!UICONTROL プロジェクトを編集]**」ボタンをクリックします。

>[!IMPORTANT]
>
>Adobeアクセストークンは 24 時間 **のみ** 有効なので、サンプルの CURL コマンドを保存します（手順 5）。 アクセストークンが無効になった場合は、トークンを再生成する必要があります。
