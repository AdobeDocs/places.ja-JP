---
title: Analytics Workspaceの場所データに関するレポート
description: この節では、Analytics Workspaceの場所データをレポートする方法について説明します。
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 8%

---


# Analytics Workspace {#places-in-workspace}の場所データに関するレポート

このドキュメントは、Analytics Workspaceでの場所データのレポート方法の例を示します。 各手順には、概要レベルの概要が含まれ、他のドキュメントページを参照することで詳細が提供されます。

## 前提条件

このドキュメントでは、次の項目を想定しています。

1. Places拡張機能がアプリケーションに実装されます。

   Places拡張機能の実装について詳しくは、[Places extensions](/help/places-ext-aep-sdks/places-extension/places-extension.md)を参照してください。

1. Adobe Analyticsのユーザーは管理者で、処理ルールにアクセスできます。

   処理ルールについて詳しくは、「[処理ルールの概要](https://docs.adobe.com/content/help/ja-JP/analytics/admin/admin-tools/processing-rules/processing-rules.html)」を参照してください。

1. Launchプロパティで、目的のPlaces Service変数に対してデータ要素が作成されています。

   Launchのデータ要素について詳しくは、[データ要素の定義](/help/use-places-launch-workflow/define-data-elements.md)を参照してください。


## 1.開始ルールの作成

デバイスがPOIに入ったときにSDKからAnalyticsにデータを送信するルールを作成します。 この種のルールの作成については、[Analytics](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md)へのPOIエントリおよび出口データの送信ページで説明しています。

この例では、ルールのアクションに、Analyticsリクエストに対して次の値が定義されています。

* **** Actionsには、「 **[!UICONTROL Places Entry]**」という値が指定されます。

* コンテキストデータキー&#x200B;**[!UICONTROL poi.name]**&#x200B;は、データ要素&#x200B;**[!UICONTROL {%%POI Name%%}]**&#x200B;の値に設定されます。

![&quot;アクションを設定&quot;](/help/assets/pt-setAction.png)

## 2. Analytics変数の作成

コンテキストデータをマッピングする（手順1で送信）には、まずAnalyticsレポートスイート用の変数を作成する必要があります。 Analyticsでの変数の作成について詳しくは、[コンバージョン変数(eVar)](https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-conversion-variables-evar.html)を参照してください。

この例では、コンバージョン変数&#x200B;**[!UICONTROL Evar2]**&#x200B;が作成され、**[!UICONTROL Places POI Name]**&#x200B;という名前が付けられています。 レポートで公開する場所変数ごとに、追加の変数を作成する必要があります。

![「analytics変数の作成」](/help/assets/aa-evar.png)

## 3.処理ルールの作成

この手順は、コンテキストデータ（手順1）をAnalytics変数にマッピングする場合に必要です（手順2）。 処理ルールの作成について詳しくは、[処理ルールの概要](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html)を参照してください。

この例では、コンテキストデータ値&#x200B;**[!UICONTROL poi.name]**&#x200B;を&#x200B;**[!UICONTROL Places POI Name (eVar2)]**&#x200B;にマップする処理ルールが作成されています。 作成した場所変数ごとに、追加の処理ルールを作成する必要があります。

![「処理ルールの作成」](/help/assets/aa-processing-rule.png)

## 4. Workspaceでレポートを生成する

この手順では、Analytics Workspaceで手順1 ～ 3で収集されたデータを表示するための基本的なレポートを示します。 Analytics Workspaceの使用方法について詳しくは、[Analytics Workspaceの概要](https://docs.adobe.com/content/help/ja-JP/analytics/analyze/analysis-workspace/home.html)を参照してください。

この例では、レポートに次の設定が含まれます。

* 指標 — **[!UICONTROL 回数]**

* Dimension- **[!UICONTROL アクション名]**

   * Dimension別に分類 — **[!UICONTROL POI名]**&#x200B;を配置

![「ワークスペースでのレポートの作成」](/help/assets/aa-workspace.png)
