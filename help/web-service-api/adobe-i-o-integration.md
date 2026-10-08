---
title: Adobe Developer プロジェクトの概要
description: Adobe Developer API プロジェクトの作成に関する情報。
exl-id: d7d31938-6c0e-40f8-a9d3-30af96043119
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: d8704da9c84a066f72471421290d4b46c65f41e1
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 2%
---
# Places API アクセスの概要と前提条件 {#developer-prereqs}

ここでは、Adobe Developer Consoleでプロジェクトを作成し、Places API リクエストで使用するアクセストークンを生成する方法について説明します。

## ユーザーアクセスの前提条件

組織のシステム管理者に、次のタスクが完了したことを確認します。

* 組織に追加されました。
* Adobe Experience Platform内のプロファイルに追加されました。

  詳細については、[Places サービスへのアクセスを取得](/help/places-gain-access.md)の「*Places サービスとExperience Platform Launch プロファイルにユーザーまたは開発者を追加する*」を参照してください。

### REST API リクエスト

Places サービス REST APIへの各リクエストには、次の項目が必要です。

* 組織ID
* API キー（クライアント IDとも呼ばれます）
* クライアント秘密鍵
* ベアラートークン

[Adobe Developer コンソール ](https://developer.adobe.com/console)を含むプロジェクトには、次のアイテムが用意されています。

* Places サービス API用のプロジェクトを作成するには、以下の「*Places サービスプロジェクトの作成*」セクションを参照してください。

>[!IMPORTANT]
>
>[Adobe Developer コンソール ](https://developer.adobe.com/console)にログインできない場合、または&#x200B;*統合の作成ページ*&#x200B;でPlaces サービスがオプションでない場合は、[Web サービス APIの概要](/help/web-service-api/places-web-services.md)の&#x200B;*組織の要件*&#x200B;を参照してください。

## Places サービス API プロジェクトの作成

Places サービス API用のプロジェクトを作成するには、次の手順を実行します。

1. Adobe IDで[Adobe Developer web サイト ](https://developer.adobe.com)にログインします。
2. ページの右上隅にある「**[!UICONTROL コンソール]**」をクリックします。
3. 複数のAdobe組織に割り当てられている場合は、ページの右上隅にあるドロップダウンリストから正しい組織を選択します。
4. 「**[!UICONTROL 新しいプロジェクトを作成]**」ボタンをクリックします。
5. 新しいプロジェクトの概要セクションの「**[!UICONTROL API]**&#x200B;を追加」ボタンをクリックします。
6. Places APIを選択するには、ページをPlaces カードまでスクロールし、カードの右上隅にあるチェックボックスをクリックします。
7. 「**[!UICONTROL 次へ]**」ボタンをクリックします。
8. 「OAuth サーバー間」オプションを選択します（選択肢がある場合）。
9. 資格情報に名前を付けて、**[!UICONTROL 次へ]**&#x200B;をクリックします。
10. プロファイルを選択します（複数がある場合は、どれでも機能します）。
11. 「**[!UICONTROL 保存してAPI]**&#x200B;を設定」をクリックします。
12. 左側のパネルで、「資格情報」の下の「**[!UICONTROL OAuth サーバー間]**」リンクをクリックします
13. このページでは、次の情報を提供します。
    * Places サービス REST API リクエストで使用するアクセストークンを生成する方法。
    * 独自のコードからアクセストークンを生成する方法の例として、curl コマンドを表示します。
    * クライアント IDの表示（API キーとも呼ばれます）
    * クライアントシークレットの表示
    * 組織IDの表示
    * Places サービス REST APIに対するリクエストで必要とされるすべてです。
14. ウィンドウの左上にあるパスのプロジェクト名をクリックすると、プロジェクトの名前をより分かりやすいものに変更できます
15. 次に、ページの右上にある「**[!UICONTROL プロジェクトを編集]**」ボタンをクリックします。

>[!IMPORTANT]
>
>Adobe アクセストークンは24時間有効な&#x200B;**のみ**&#x200B;なので、サンプル CURL コマンドを保存します（手順5）。 アクセストークンが無効になった場合は、トークンを再生成する必要があります。
