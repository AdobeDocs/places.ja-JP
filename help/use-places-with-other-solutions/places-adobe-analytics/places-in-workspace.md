---
title: Analytics Workspaceでの位置情報に関するレポート
description: この節では、Analytics Workspaceでの位置情報のレポート方法について説明します。
exl-id: 45ca3c80-71b7-41de-9b00-645504061935
TQID: https://experienceleague.adobe.com/Xym9Ko8czyd3wYWVo22sQoK6gk-VvftGVHfIDUys06E
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
    internal-label: CX Enterprise
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
    internal-label: Analytics
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
feature_v2:
  - id: b069d60e-95f3-44d6-95a8-ddc862a4bc38
    internal-label: Reports
  - id: c20d46e7-1c7d-476c-a50e-3961d4dce35f
    internal-label: Reporting
  - id: daec7ead-f475-492a-a3b3-02ae08565d6f
    internal-label: Implementation
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
    internal-label: Data collection
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
    internal-label: Places
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
source-git-commit: d8704da9c84a066f72471421290d4b46c65f41e1
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 6%
---
# Analytics Workspaceでの位置情報に関するレポート {#places-in-workspace}

このドキュメントでは、Analytics Workspaceで位置情報をレポートする方法の例を示します。 各ステップには概要が記載され、その詳細は他のドキュメントページを参照することで提供されます。

## 前提条件

このドキュメントでは、次の条件を満たしていることを前提としています。

1. Places拡張機能は、アプリケーションに実装されます。

   Places拡張機能の実装について詳しくは、[Places拡張機能](/help/places-ext-aep-sdks/places-extension/places-extension.md)を参照してください。

1. Adobe Analytics ユーザーは管理者であり、処理ルールにアクセスできます。

   処理ルールについて詳しくは、「[処理ルールの概要](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/c-processing-rules/processing-rules.html)」を参照してください。

1. Launch プロパティでは、目的のPlaces サービス変数に対してデータ要素が作成されています。

   Launchのデータ要素について詳しくは、[&#x200B; データ要素の定義](/help/use-places-launch-workflow/define-data-elements.md)を参照してください。


## &#x200B;1. 起動ルールの作成

デバイスがPOIに入ったときに、SDKがAnalyticsにデータを送信するルールを作成します。 この種類のルールの作成については、[POIのエントリと終了データをAnalytics](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md)に送信ページで説明しています。

この例では、ルールのアクションには、Analytics リクエストに対して定義された次の値があります。

* **[!UICONTROL アクション]**&#x200B;には、**[!UICONTROL Places Entry]**&#x200B;という値が指定されています。

* コンテキストデータキー&#x200B;**[!UICONTROL poi.name]**&#x200B;は、データ要素&#x200B;**[!UICONTROL {%%POI Name%}]**&#x200B;の値に設定されています。

![&quot;アクションを設定&quot;](/help/assets/pt-setAction.png)

## &#x200B;2. Analytics変数の作成

コンテキストデータ（手順1で送信）をマッピングするには、まずAnalytics レポートスイート用の変数を作成する必要があります。 Analyticsでの変数の作成について詳しくは、[&#x200B; コンバージョン変数（eVar） &#x200B;](https://experienceleague.adobe.com/docs/analytics/implementation/vars/page-vars/evar.html?lang=ja)を参照してください。

この例では、コンバージョン変数&#x200B;**[!UICONTROL Evar2]**&#x200B;が作成され、**[!UICONTROL Places POI Name]**&#x200B;という名前が付けられています。 レポートで公開する場所の変数ごとに、追加の変数を作成する必要があります。

![&quot;分析変数を作成&quot;](/help/assets/aa-evar.png)

## &#x200B;3. 処理ルールの作成

この手順は、コンテキストデータ（手順1）をAnalytics変数にマッピングするために必要です（手順2）。 処理ルールの作成について詳しくは、[処理ルールの概要](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/c-processing-rules/processing-rules.html)を参照してください。

この例では、コンテキストデータ値&#x200B;**[!UICONTROL poi.name]**&#x200B;を&#x200B;**[!UICONTROL Places POI Name （eVar2）]**&#x200B;にマッピングするための処理ルールが作成されています。 作成する各場所変数に対して、追加の処理ルールを作成する必要があります。

![&quot;処理ルールを作成&quot;](/help/assets/aa-processing-rule.png)

## &#x200B;4. Workspaceでのレポートの生成

このステップでは、Analytics Workspaceで基本的なレポートを表示し、手順1～3で収集したデータを表示します。 Analytics Workspaceの使用方法について詳しくは、[Analytics Workspaceの概要](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/home.html?lang=ja)を参照してください。

この例では、レポートに次の設定があります。

* 指標 – **[!UICONTROL 発生回数]**

* Dimension - **[!UICONTROL アクション名]**

  * Dimensionで分類 – **[!UICONTROL POI名を配置]**

![&quot;ワークスペースでレポートを作成&quot;](/help/assets/aa-workspace.png)
