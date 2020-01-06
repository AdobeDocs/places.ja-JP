---
title: Analytics Workspaceの場所データに関するレポート
description: ここでは、Analytics Workspaceで場所データをレポートする方法について説明します。
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# Analytics Workspaceの場所データに関するレポート {#places-in-workspace}

このドキュメントでは、Analytics Workspaceでの場所データのレポート方法の例を示します。 各手順には、他のドキュメントページを参照することで提供される詳細を含む概要が含まれます。

## 前提条件

このドキュメントでは、次の事項を前提としています。

1. Adobe Places拡張機能がアプリケーションに実装されます。 Adobe Placesの実装について詳しくは、Places拡張機能を参照 [してください](/help/places-ext-aep-sdks/places-extension/places-extension.md)。

1. Adobe Analyticsユーザーは管理者で、処理ルールにアクセスできます。 処理ルールについて詳しくは、「[処理ルールの概要](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html)」を参照してください。

1. Launchプロパティで、目的のLocation Service変数に対してデータ要素が作成されています。 「起動」のデータ要素について詳しくは、「データ要素の定 [義」を参照してください](/help/use-places-launch-workflow/define-data-elements.md)。


## 1.起動ルールの作成

デバイスがPOIに入ったときにSDKがAnalyticsにデータを送信するルールを作成します。 この種のルールの作成については、AnalyticsにPOIエントリ [と出口データを送信ページで説明します](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md) 。

この例では、ルールのアクションに、Analyticsリクエストに対して次の値が定義されています。

* **[!UICONTROL Action]**の値が指定される場合は**[!UICONTROL Places Entry]**、

* コンテキストデータ **[!UICONTROL poi.name]**キーは、データ要素の値に設定されま**[!UICONTROL {%%POI Name%%}]**&#x200B;す。

![&quot;アクションを設定&quot;](/help/assets/pt-setAction.png)

## 2.Analytics変数の作成

（手順1で送信された）コンテキストデータをマップするには、まずAnalyticsレポートスイート用の変数を作成する必要があります。 Analyticsでの変数の作成について詳しくは、コンバージ [ョン変数\(eVars\)を参照してください](https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-conversion-variables-evar.html)。

この例では、コンバージョン変数、 **[!UICONTROL Evar2]**が作成され、名前が付けられていま**[!UICONTROL Places POI Name]**&#x200B;す。 レポートに表示する場所変数ごとに、追加の変数を作成する必要があります。

![「analytics変数の作成」](/help/assets/aa-evar.png)

## 3.処理ルールの作成

この手順は、コンテキストデータ（手順1）をAnalytics変数にマッピングするために必要です（手順2）。 For more information on creating processing rules, see [Processing rules overview](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html).

この例では、コンテキストデータ値をマッピングする処理ルールが作成され **[!UICONTROL poi.name]**ていま**[!UICONTROL Places POI Name \(eVar2\)]**&#x200B;す。 作成した場所の変数ごとに、追加の処理ルールを作成する必要があります。

![「処理ルールの作成」](/help/assets/aa-processing-rule.png)

## 4.Workspaceでのレポートの生成

この手順は、Analytics Workspaceで手順1 ～ 3で収集されたデータを表示する基本レポートを示します。 Analytics Workspaceの使用方法について詳しくは、 [Analytics Workspaceの概要を参照してください](https://docs.adobe.com/content/help/en/analytics/analyze/analysis-workspace/analysis-workspace-features.html)。

この例では、レポートに次の設定が含まれます。

* 指標 - **[!UICONTROL Occurrences]**

* ディメンション - **[!UICONTROL Action Name]**

   * ディメンション別の分類 — **[!UICONTROL Places POI Name]**

![「ワークスペースでのレポートの作成」](/help/assets/aa-workspace.png)
