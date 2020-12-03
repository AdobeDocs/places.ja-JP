---
title: Analytics Workspaceの場所データに関するレポート
description: この節では、Analytics Workspaceの場所データをレポートする方法について説明します。
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 9%

---


# Analytics Workspaceの場所データに関するレポート {#places-in-workspace}

このドキュメントは、Analytics Workspaceでの場所データのレポート方法の例を示します。 各手順には、概要レベルの概要が含まれ、他のドキュメントページを参照することで詳細が提供されます。

## 前提条件

このドキュメントでは、次の項目を想定しています。

1. Places拡張機能がアプリケーションに実装されます。

   Places拡張機能の実装について詳しくは、「Places拡張機能 [](/help/places-ext-aep-sdks/places-extension/places-extension.md)」を参照してください。

1. Adobe Analyticsのユーザーは管理者で、処理ルールにアクセスできます。

   処理ルールについて詳しくは、「[処理ルールの概要](https://docs.adobe.com/content/help/ja-JP/analytics/admin/admin-tools/processing-rules/processing-rules.html)」を参照してください。

1. Launchプロパティで、目的のPlaces Service変数に対してデータ要素が作成されています。

   「起動」のデータ要素について詳しくは、「データ要素の [定義](/help/use-places-launch-workflow/define-data-elements.md)」を参照してください。


## 1.開始ルールの作成

デバイスがPOIに入ったときにSDKからAnalyticsにデータを送信するルールを作成します。 この種のルールの作成については、POIエントリと出口データをAnalytics [ページに](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md) 送信するで説明します。

この例では、ルールのアクションに、Analyticsリクエストに対して次の値が定義されています。

* **[!UICONTROL Action]** の値が指定され **[!UICONTROL Places Entry]**&#x200B;ます。

* コンテキストデータキー **[!UICONTROL poi.name]** は、データ要素の値に設定され **[!UICONTROL {%%POI Name%%}]**&#x200B;ます。

![&quot;アクションを設定&quot;](/help/assets/pt-setAction.png)

## 2. Analytics変数の作成

コンテキストデータをマッピングする（手順1で送信）には、まずAnalyticsレポートスイート用の変数を作成する必要があります。 Analyticsでの変数の作成について詳しくは、コンバージョン変数(eVar)を参照して [ください](https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-conversion-variables-evar.html)。

この例では、コンバージョン変数 **[!UICONTROL Evar2]**&#x200B;が作成され、名前が付けられてい **[!UICONTROL Places POI Name]**&#x200B;ます。 レポートで公開する場所変数ごとに、追加の変数を作成する必要があります。

![「analytics変数の作成」](/help/assets/aa-evar.png)

## 3.処理ルールの作成

この手順は、コンテキストデータ（手順1）をAnalytics変数にマッピングする場合に必要です（手順2）。 For more information on creating processing rules, see [Processing rules overview](https://docs.adobe.com/content/help/ja-JP/analytics/admin/admin-tools/processing-rules/processing-rules.html).

この例では、コンテキストデータ値をマッピングする処理ルールが作成さ **[!UICONTROL poi.name]** れてい **[!UICONTROL Places POI Name (eVar2)]**&#x200B;ます。 作成した場所変数ごとに、追加の処理ルールを作成する必要があります。

![「処理ルールの作成」](/help/assets/aa-processing-rule.png)

## 4. Workspaceでレポートを生成する

この手順では、Analytics Workspaceで手順1 ～ 3で収集されたデータを表示するための基本的なレポートを示します。 Analytics Workspaceの使用方法について詳しくは、 [Analytics Workspaceの概要を参照してください](https://docs.adobe.com/content/help/ja-JP/analytics/analyze/analysis-workspace/home.html)。

この例では、レポートに次の設定が含まれます。

* 指標 - **[!UICONTROL Occurrences]**

* ディメンション - **[!UICONTROL Action Name]**

   * Dimension別に分類 — **[!UICONTROL Places POI Name]**

![「ワークスペースでのレポートの作成」](/help/assets/aa-workspace.png)
