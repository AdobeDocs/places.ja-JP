---
title: Adobe Campaign Standardでの場所の使用
seo-title: Adobe Campaign Standardでの場所の使用
description: 顧客の好みと習慣を深く理解することは、成功するマーケティングキャンペーンの鍵となります。 ユーザーが物理的な場所を訪問したかどうかを知ることは、顧客との関係を形成する上で非常に価値のあるコンテキストを追加することもできます。
seo-description: 顧客の好みと習慣を深く理解することは、成功するマーケティングキャンペーンの鍵となります。 ユーザーが物理的な場所を訪問したかどうかを知ることは、顧客との関係を形成する上で非常に価値のあるコンテキストを追加することもできます。
translation-type: tm+mt
source-git-commit: d7c5fe5d7a20a647240114d25307373b493ae2f5

---


# Adobe Campaign Standardでの場所の使用 {#places-with-acs}

*先週はお越し頂きありがとうございます。次回のお訪問では、驚きのお知らせをいたします。*

顧客の好みと習慣を深く理解することは、成功するマーケティングキャンペーンの鍵となります。 ユーザーが検索した項目と以前の購入履歴が、オーディエンスのターゲット設定に大きな役割を果たします。 ユーザーが物理的な場所を訪問したかどうかを知ることは、顧客との関係を形成する上で非常に価値のあるコンテキストを追加することもできます。

最近のeマーケティング担当者のレポートによると、パフォーマンスの高い小売業者の85%が、自社のマーケティング活動にとって場所が非常に重要であると考えています。 さらに、北米の小売業者の58%以上が、顧客体験を高めるために近接/位置テクノロジーに投資する予定です。

![](/help/assets/using-loc-services-acs_0.png)

スマートフォンの使い方において、場所がどれだけ重要かを考えてみましょう。 スマホに近くのレストランやガソリンスタンド、食料品店、その他のサービスを見つけるように頼む頻度はどれくらいか。

ブランドとして、マーケティングキャンペーンに場所を活用する方法を考える必要があるというのは理にかなっています。 このガイドでは、Adobe Experience Platform Experience Platform Location Serviceの機能を活用して、Adobe Campaign Standardを使用してメッセージングに場所のコンテキストを追加し、目標地点(POI)エントリに基づいてパーソナライズされたプッシュ通知やアプリ内メッセージを配信する方法を示します。

始める前に、このガイドは、Adobe Experience Platform Mobile SDKとAdobe Campaign Standard拡張機能を使用して設定されたモバイルアプリケーションがあることを前提としています。 Adobe Experience Platform Mobile SDKおよびCampaign Standardに加えて、Experience Platform Location Serviceにアクセスできる必要があります。

## 前提条件

1. Adobe Experience Platform Mobile SDK [をアプリに統合します](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) 。
1. モバイルア [プリ設定に](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) Adobe Campaign Standard Extensionを追加します。
1. [1つ以上のPOIを作成します](/help/places-database-management-1/managing-pois-in-the-places-ui.md)。

>[!TIP]
>
>POIの一括アップロードまたは管理の方法を探している場合は、このスクリプトを参照してCSV [ファイルからPOIをアップロードします](https://github.com/adobe/places-scripts) 。 また、 [Places APIは](/help/places-rest-apis/api-usage/api-usage.md) 、目標地点の作成や管理に使用できます。

Placesへのアクセス権を持っていない場合は、ここでアクセス権をリク [エストできます](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4fkr821yYptFo-ghlnlXCyhUM0dQVkJCSzVDMFNGWEFXWUUwNEJWSjhSRS4u)。

### Places拡張機能を有効にしてアプリケーションにインストールする

場所インターフェイスに目標地点を作成したら、場所機能をアプリケーションに追加する必要があります。

1. 指示に従って、アプリケーションで場所モニターの拡張機能を有効にします。
1. 「Places」拡張で、以前に作成したPOIの適切なライブラリが選択されていることを確認します。

   追加のライブラリは、いつでも拡張設定に追加できます。

1. これらの設定をライブラリに追加し、「起動」で設定の変更を発行したことを確認します。
1. 「 **[UICONTROLの起動環境」タブで、インストール手順]** (Install Instructions)アイコンをクリックして、適切なCocoaPodおよびGradleファイルをアプリプロジェクトにダウンロードする手順を表示します。
1. アプリケーションで、アプリケーションに場所の背景モードを追加する手順に従い、場所モニターを起動します。
1. デバイスシミュレーターを使用してアプリケーションをテストし、デバイスの場所のスプーフィングに基づいて、近くの目標地点に対するアプリケーションリクエストを確認します。

### エクスペリエンスプラットフォームの起動でのデータ要素の作成

アプリケーションで場所モニターの拡張が正しく機能していることを確認したら、エクスペリエンスプラットフォーム起動でデータ要素を作成し、拡張機能によって提供され、Mobile SDKイベントハブを通過する情報を読み取ります。 データ要素は、基本的にはクライアントアプリケーションからデータを取得するエイリアスとして機能します。 Places拡張からデータを取得するデータ要素をいくつか作成します。

1. エクスペリエンスプラットフォーム起動モバイルのプロパティで、タブ **[!UICONTROL Data Elements]** のをクリックし、をクリックしま **[!UICONTROL Add Data Element]**&#x200B;す。
1. 拡張機能メニューで、を選択しま **[!UICONTROL Places]**&#x200B;す。
1. ドロップダ **[!UICONTROL Data Element]** ウンリストから[!UICONTROL **Name}]を選択します**。
1. 右側のウィンドウで、ユーザーが現在 **[!UICONTROL Current POI]** いるPOIの名前を取得する対象を選択できます。

   * **[!UICONTROL Last Entered]** ユーザーが最後に入力したPOIの名前を取得します。
   * **[!UICONTROL Last Exited]** は、ユーザーが最後に出たPOIの名前を指定します。

1. Select **[!UICONTROL Last Entered]**.
1. などのデータ要素の名前を入力し、をク **[!UICONTROL Last Entered POI Name]**&#x200B;リックします **[!UICONTROL Save]**。


   ![](/help/assets/using-loc-services-acs_1.png)

1. 上記と同じ手順を繰り返し、最後に入力したPOI緯度 *、最後に入力したPOI経*&#x200B;度 *、最後に入力したPOI半*&#x200B;径のデータ要素を作成します **。

場所のデータ要素に加えて、 *App IDと* Experience Cloud IDのMobile coreデータ要素も作成済みであることを確 *認します*。

### 場所データをAdobe Campaign Standardに送信するルールの作成

エクスペリエンスプラットフォームの起動のルールを使用すると、イベントトリガーに基づいて複雑な複数ソリューションのワークフローを作成できます。 新しいアップデートを作成したり、既存のルールを変更したりして、アップデートをモバイルアプリケーションに動的にデプロイしたりできます。 この例では、ユーザーが地域フェンスのPOIに入ったときにトリガーされるルールを作成します。 ルールがトリガーされると、そのユーザーの特定のPOIへのエントリを記録するために、キャンペーン標準に更新が送信されます。 このPOIはExperience Cloud IDに基づいています。

1. エクスペリエンスプラットフォームの起動モバイルプロパティで、タブをク **[!UICONTROL Rules]** リックし、をクリックしま **[!UICONTROL Add Rule]**&#x200B;す。
1. セクション **[!UICONTROL Events]** でをクリックし、を **[!UICONTROL +]** 選択しま **[!UICONTROL Places]**&#x200B;す。
1. で、を **[!UICONTROL Event Type]**&#x200B;選択しま **[!UICONTROL Enter POI]**&#x200B;す。
1. 例えば、ルールの名前を入力します **[!UICONTROL User entered POI]**。
1. 「**[!UICONTROL Keep Changes]**」をクリックします。
1. セクションは空 **[!UICONTROL Conditions]** 白のままにします。

   このセクションでは、このルールをいつ実行するかをフィルターまたは制限できます。

1. In the **[!UICONTROL Actions]** section, click **[!UICONTROL +]**.
1. でを選 **[!UICONTROL Extension]**&#x200B;択し、 **[!UICONTROL Mobile Core]** でを選 **[!UICONTROL Action Type]**&#x200B;択します **[!UICONTROL Send Postback]**。

1. URLの場合は、キャンペーン標準のロケーションエンドポイントを作成する必要があります。

   URLは次のようになります。 CampaignサーバーおよびpKey用に以前に作成した正しいデータ要素を使用していることを確認します。

   `https://{%%camp-server%%}/rest/head/mobileAppV5/{%%pkey%%}/locations/`

1. ボックスをクリックして投稿の本文を追加し、以下を送信します。

   ```text
   {
   "locationData": {
   "distances": "{%%Last Entered POI Radius%%}",
   "poiLabel": "{%%Last Entered POI Name%%}",
   "latitude": "{%%Last Entered POI Lat%%}",
   "longitude": "{%%Last Entered POI Long%%}",
   "appId": "{%%AppID%%}",
   "marketingCloudId": “{%%ecid%%}”
   }
   }
   ```

1. 前の節で作成した特定のデータ要素を使用します。
1. に、と **[!UICONTROL Content Type]**&#x200B;入力しま **[!UICONTROL application/json]**&#x200B;す。
1. この設 **[!UICONTROL Keep Changes]** 定が完了したら、をクリックします。

   Slack webフックを追加のアクションとして設定すると、自分のアクションがトリガーされ、適切なデータが収集されていることを検証できる場合があります。

   >[!IMPORTANT]
   >
   >ルールとすべてのデータ要素が設定の一部としてデプロイされていることを確認するために、アプリに最新の変更を公開してください。 公開後、モバイルアプリケーションを再起動して、最新の設定の更新を取得する必要があります。

### 場所データを使用してキャンペーン標準のメッセージをターゲットにする

キャンペーンに場所のデータが入力されたので、目標地点をオーディエンスセグメントツールとして使用できます。

1. Adobe Campaign Standardインスタンス内で、「 **[UICONTROLプッシュ通知を作成」をクリックします]**。
1. プッシュ通知タイプとして、「 **[UICONTROLアプリの購読者にプッシュを送信」を選択します]**。

   このプッシュタイプは、アプリのすべてのユーザーをターゲットにします。 モバイルユーザーがCampaignプロファイルに添付されている場合は、「 **[UICONTROL Send push to Campaign profiles]** i」も選択できます。

1. をクリ **[!UICONTROL Next]** ックし、次の画面で一般的な詳細を入力します。
1. オーディエンス画面で、をクリック **[!UICONTROL Count]** して、プッシュ通知が送信される推定ユーザー数を確認します。

   この場合、カウントは3です。3つのデバイスがテストアプリケーションにインストールされています。

1. 左側のサイドバーで、タブを展開し **[!UICONTROL Profile]** 、メイン領域にフィル **[!UICONTROL POI location]** ターをドラッグします。
1. POIフィルタウィンドウで、ターゲットにするPOIの正確な名前を入力します。

   このPOIを最後に訪問してからの時間範囲を指定するには、追加の選択を行います。

   ![](/help/assets/using-loc-services-acs_2.png)

1. クリック [!**UICONTROL確認]**。
1. 上部でもう一度カウントを実行し、オーディエンスのサイズ変更を確認します。

   カウントの更新が表示されない場合は、エントリをトリガーしたデバイスがないPOI名を入力した可能性があります。 様々なテストデバイスのPOIエントリのリストを見ることができるので、Slack webフックを持つことはここで重要になります。
1. 追加のPOI位置フィルターをドラッグして、メッセージに複数のPOIを含めることができます。
1. クリック **[!UICONTROL Next]** して、配信用のプッシュ通知の作成を終了します。

   ![](/help/assets/using-loc-services-acs_3.png)

プッシュ通知に加えて、場所データを使用して、アプリ内メッセージを受信するユーザーをセグメント化することもできます。

1. Adobe Campaign Standardインスタンスで、をクリックしま **[!UICONTROL Create In-App message]**&#x200B;す。
1. メッセージタイプに対して、を選択しま **[!UICONTROL Target all users of a Mobile application]**&#x200B;す。
1. をクリ **[!UICONTROL Next]** ックし、次の画面で一般的な詳細を入力します。
1. 左側のペインで、場所に関連する様々なトリガーを使用できることを確認します。
1. ユーザーがPOIジオフェンスを入力した場合は、アプリ内メッセージを表示するように選択できます。

   場所UIで定義したメタデータを使用して、オーディエンスをフィルターすることもできます。 この例では、体育館の施設を持つPOIを最後に退出したユーザーにのみ表示されるアプリ内メッセージをトリガーします。 ジムを使うか、気に入ったかを調べる調査を送りたいのかもしれません。

1. をクリ **[!UICONTROL Next]** ックして、配信するアプリ内メッセージの作成を終了します。

   ![](/help/assets/using-loc-services-acs_4.png)

場所とAdobe Campaign Standardを使用すると、過去の場所に基づいてメッセージをセグメント化し、ユーザーにターゲット化するための非常に強力なツールが提供されます。 このシンプルな統合により、よりパーソナライズされた状況に応じた使用例を構築することができます。

モバイルワークフローに位置情報を取り込むため、場所と統合ソリューションを常に改善しています。 Placesを活用する製品の1つは、今後のTriggered Journeyのソリューションで、場所などのイベントトリガーに基づいてリアルタイムのワークフローを作成できるようになります。

## 推奨リンク

詳しくは、次を参照してください。

* [Adobe Experience Location Service](https://www.adobe.com/experience-platform/location-service.html)
* [Adobe Campaign Standard](https://www.adobe.com/marketing/campaign.html)
* [新規登録してAdobe Places Betaにアクセス](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4fkr821yYptFo-ghlnlXCyhUM0dQVkJCSzVDMFNGWEFXWUUwNEJWSjhSRS4u)
* [Adobe Experience Platform Mobile SDK](https://sdkdocs.com/)
* [Experience Platform SDKとのAdobe Campaignの統合](https://helpx.adobe.com/campaign/kb/configuring-app-sdk.html)
