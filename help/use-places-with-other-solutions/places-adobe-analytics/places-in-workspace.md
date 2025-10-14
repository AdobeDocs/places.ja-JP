---
title: Analytics Workspaceでの場所データのレポート
description: この節では、Analytics Workspaceで場所データをレポートする方法について説明します。
exl-id: 45ca3c80-71b7-41de-9b00-645504061935
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 3%

---

# Analytics Workspaceでの場所データのレポート {#places-in-workspace}

このドキュメントでは、Analytics Workspaceでロケーションデータをレポートする方法の例を示します。 各手順には、概要と、他のドキュメントページを参照する際に提供される詳細が含まれます。

## 前提条件

このドキュメントでは、次のことを前提としています。

1. Places 拡張機能はアプリケーションに実装されています。

   Places 拡張機能の実装について詳しくは、[Places 拡張機能 &#x200B;](/help/places-ext-aep-sdks/places-extension/places-extension.md) を参照してください。

1. Adobe Analytics ユーザーは管理者で、処理ルールにアクセスできます。

   処理ルールについて詳しくは、「[処理ルールの概要](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/c-processing-rules/processing-rules.html?lang=ja)」を参照してください。

1. Launch プロパティで、目的とする Places Service 変数のデータ要素が作成されています。

   Launch のデータ要素について詳しくは、「[&#x200B; データ要素の定義 &#x200B;](/help/use-places-launch-workflow/define-data-elements.md)」を参照してください。


## 1. ローンチルールの作成

デバイスが POI に入ると SDK が Analytics にデータを送信するルールを作成します。 このようなルールの作成については、[Analytics への POI エントリおよび離脱データの送信 &#x200B;](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md) ページで説明します。

この例では、ルールのアクションには、Analytics リクエストに対して定義された次の値があります。

* **[!UICONTROL Action]** には **[!UICONTROL Places Entry]** の値を指定します。

* コンテキストデータキー **[!UICONTROL poi.name]** は、データ要素 **[!UICONTROL {%%POI Name%%}]** の値に設定されています。

![&#x200B; 「アクションを設定」 &#x200B;](/help/assets/pt-setAction.png)

## 2. Analytics 変数の作成

コンテキストデータ（手順 1 で送信）をマッピングするには、まず Analytics レポートスイート用の変数を作成する必要があります。 Analytics での変数の作成について詳しくは、[&#x200B; コンバージョン変数（eVars） &#x200B;](https://experienceleague.adobe.com/docs/analytics/implementation/vars/page-vars/evar.html?lang=ja) を参照してください。

この例では、コンバージョン変数 **[!UICONTROL Evar2]** が作成され、**[!UICONTROL Places POI 名]** という名前が付けられています。 レポートで公開する場所変数ごとに、追加の変数を作成する必要があります。

![analytics 変数の作成」 &#x200B;](/help/assets/aa-evar.png)

## 3.処理ルールの作成

この手順は、コンテキストデータ（手順 1）を Analytics 変数（手順 2）にマッピングするために必要です。 処理ルールの作成について詳しくは、[&#x200B; 処理ルールの概要 &#x200B;](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/c-processing-rules/processing-rules.html?lang=ja) を参照してください。

この例では、コンテキストデータ値 **[!UICONTROL poi.name]** を **[!UICONTROL Places POI Name （eVar2）]** にマッピングする処理ルールを作成しました。 作成する場所変数ごとに、追加の処理ルールを作成する必要があります。

![&#x200B; 「処理ルールの作成」 &#x200B;](/help/assets/aa-processing-rule.png)

## 4. Workspaceでのレポートの生成

この手順では、手順 1 ～ 3 で収集したデータを表示するための Analytics Workspaceの基本レポートを示します。 Analytics Workspaceの使用方法について詳しくは、[Analytics Workspaceの概要 &#x200B;](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/home.html?lang=ja) を参照してください。

この例では、レポートには次の設定があります。

* 指標 – **[!UICONTROL 発生件数]**

* Dimension- **[!UICONTROL アクション名]**

   * Dimension別に分類 – **[!UICONTROL Places POI 名]**

![workspace でのレポートの作成」 &#x200B;](/help/assets/aa-workspace.png)
