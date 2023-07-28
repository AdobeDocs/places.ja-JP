---
title: Analytics Workspace での場所データのレポート
description: この節では、Analytics Workspace で場所データをレポートする方法について説明します。
exl-id: 45ca3c80-71b7-41de-9b00-645504061935
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 5%

---

# Analytics Workspace での場所データのレポート {#places-in-workspace}

このドキュメントでは、Analytics Workspace でロケーションデータをレポートする方法の例を示します。 各ステップには、概要レベルの概要と、他のドキュメントページを参照することで提供される詳細が含まれます。

## 前提条件

このドキュメントでは、次の点を前提としています。

1. Places 拡張機能は、アプリケーションに実装されます。

   Places 拡張機能の実装について詳しくは、 [Places 拡張機能](/help/places-ext-aep-sdks/places-extension/places-extension.md).

1. Adobe Analyticsユーザーは管理者で、処理ルールにアクセスできます。

   処理ルールについて詳しくは、「[処理ルールの概要](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/c-processing-rules/processing-rules.html)」を参照してください。

1. Launch プロパティでは、必要な Places Service 変数用にデータ要素が作成されています。

   Launch のデータ要素について詳しくは、 [データ要素の定義](/help/use-places-launch-workflow/define-data-elements.md).


## 1. Launch ルールを作成する

デバイスが POI に入ったときに SDK が Analytics にデータを送信するルールを作成します。 この種のルールの作成については、 [POI 入口および出口データを Analytics に送信](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md) ページに貼り付けます。

この例では、ルールのアクションで、Analytics リクエストに対して次の値が定義されています。

* **[!UICONTROL アクション]** が次の値で提供される **[!UICONTROL 場所の入口]**.

* コンテキストデータキー **[!UICONTROL poi.name]** がデータ要素の値に設定されている **[!UICONTROL {%%POI 名%%}]**.

![&quot;アクションを設定&quot;](/help/assets/pt-setAction.png)

## 2. Analytics 変数を作成する

コンテキストデータ（手順 1 で送信）をマッピングするには、まず Analytics レポートスイート用に変数を作成する必要があります。 Analytics での変数の作成について詳しくは、 [コンバージョン変数 (eVar)](https://experienceleague.adobe.com/docs/analytics/implementation/vars/page-vars/evar.html?lang=ja).

この例では、コンバージョン変数 **[!UICONTROL Evar2]**、が作成され、という名前が付けられました。 **[!UICONTROL 場所 POI 名]**. レポートで表示する各ロケーション変数に対して、追加の変数を作成する必要があります。

![「analytics 変数の作成」](/help/assets/aa-evar.png)

## 3.処理ルールを作成する

この手順は、コンテキストデータ（手順 1）を Analytics 変数（手順 2）にマッピングするために必要です。 処理ルールの作成について詳しくは、 [処理ルールの概要](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/c-processing-rules/processing-rules.html).

この例では、コンテキストデータ値をマッピングする処理ルールが作成されています **[!UICONTROL poi.name]** into **[!UICONTROL 場所 POI 名 (eVar2)]**. 場所変数を作成するたびに、追加の処理ルールを作成する必要があります。

![「処理ルールの作成」](/help/assets/aa-processing-rule.png)

## 4. Workspace でレポートを生成する

この手順では、手順 1 ～ 3 で収集したデータを表示するための、Analytics Workspace の基本レポートを示します。 Analytics Workspace の使用方法について詳しくは、 [Analytics Workspace の概要](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/home.html?lang=ja).

この例では、レポートの設定は次のようになります。

* 指標 — **[!UICONTROL 発生件数]**

* DIMENSION- **[!UICONTROL アクション名]**

   * Dimension別 — **[!UICONTROL 場所 POI 名]**

![&quot;workspace でのレポートの作成&quot;](/help/assets/aa-workspace.png)
