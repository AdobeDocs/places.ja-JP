---
title: Places サービスのテストと検証
description: この節では、Places サービスをテストおよび検証する方法について説明します。
exl-id: 8dad6619-566b-4aea-b29c-a89192a66441
TQID: https://experienceleague.adobe.com/nO4tOQW9rp3zjkHT6aJ5IcXHcD9heOaRAJiEchiz1Fk
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
    internal-label: CX Enterprise
  - id: dc5cf79d-43c4-4731-bffa-1df5d7549cb1
    internal-label: Adobe Sign
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
    internal-label: Target
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
    internal-label: Analytics
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
feature_v2:
  - id: c93393a4-e558-47e1-992e-c91ed4d480ce
    internal-label: Implementation
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
    internal-label: Integrations
  - id: daec7ead-f475-492a-a3b3-02ae08565d6f
    internal-label: Implementation
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
    internal-label: Data collection
  - id: eb9732ab-8232-4b21-bc4c-89de86dbe4d7
    internal-label: Integrations
  - id: ed0d8d0e-04b9-4326-be72-a0fbca265377
    internal-label: Integrations
  - id: f7c7de77-382f-4f48-8b36-61a170f06d3d
    internal-label: Integrations
  - id: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
    internal-label: API
subfeature_v2:
  - id: c3bf7e1e-1db5-4c72-9293-e2f0b1ab73d0
    internal-label: Triggers
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
    internal-label: Places
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
    internal-label: Metadata
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
source-git-commit: d8704da9c84a066f72471421290d4b46c65f41e1
workflow-type: tm+mt
source-wordcount: '1748'
ht-degree: 2%
---
# Places サービスをテストするための推奨事項 {#test-validate-loc-svc}

多くの顧客や組織が世界中のPOIを定義するため、Places サービスがアプリケーションとどのように相互作用するかをシミュレートしてテストする方法を持つことが重要です。 この情報は、定義済みのPOIとユーザーの現在の場所に基づいて、正しくトリガーされているPlaces サービスのエントリと離脱をテストおよび検証する方法を理解するのに役立ちます。

環境変数は位置情報や精度の要因となる可能性があるため、まず開発者ツールやシミュレートされた位置情報を使用して、ベースラインの結果を確認することをお勧めします。 ここでの目的は、すべてのロケーションイベントが正しく動作していることを検証することです。 場所イベントが正しく検証されたら、ソリューション統合（Analytics、Target、Campaignなど）をテストできます。 テスト作業に役立てるために、Slack Webhookをポストバックで設定し、個々の開発環境にGPX ファイルを読み込む必要があります。

>[!IMPORTANT]
>
>このプランでは、POIが[Places サービス UI](https://places.adobe.com)で作成され、Places拡張機能の最新バージョンがインストールされ、正しく設定されていることを前提としています。 アクティブな地域モニタリングを行う場合は、地域モニタリングソリューションが実装されていることも前提としています。 詳しくは、[Places拡張機能](/help/places-ext-aep-sdks/places-extension/places-extension.md)、[iOSのCoreLocation ドキュメント &#x200B;](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions)、または[Androidの場所ドキュメント &#x200B;](https://developer.android.com/training/location/geofencing)を参照してください。

| 手順 | 説明 | 期待される結果 |
|--- |--- |--- |
| 1 | Androidでトラックロケーションへのアクセス権を付与するために、適切なマニフェストキーが入力されていることを確認します。 | 確認済み |
| 1a | 場所の更新がiOSで設定されていることを確認します。 また、iOSで適切なプリストキーを設定し、ユーザーに位置情報のトラッキングを依頼する必要があります。 | 確認済み |
| 2 | IOSに設定されているモニタリングモードを確認します。 連続モードは、より高い精度と持続性を可能にするだけでなく、バッテリー寿命をより大きく排出します。 | 大きな変化または継続的 |
| 3 | 複数のPOI ライブラリを使用している場合は、Experience Platform LaunchのPlaces拡張機能で適切なライブラリが選択されていることを確認します。 | 確認済み |
| 4 | Mobile CoreおよびPlaces拡張機能の最新バージョンが、GradleまたはCocoaPodsを介してアプリにバンドルされていることを確認します。 | 確認済み – 最近の更新について詳しくは、[&#x200B; リリースノートを参照してください。](/help/release-notes.md) |
| 5 | テスト用に正しい環境が設定されていることを確認します。 Launch環境IDは、Launch開発環境と一致する必要があります。 | 確認済み |
| 6 | テストするPOIごとにGPX ファイルを作成します。 GPX ファイルは、ローカル開発環境で使用して、場所エントリをシミュレートできます。 GPX ファイルの作成と使用について詳しくは、次を参照してください。iOS Simulatorの<br>[GPX ファイル [閉じる]](https://stackoverflow.com/questions/17292783/gpx-files-for-ios-simulator)<br>[https://mapstogpx.com/mobiledev.php](https://mapstogpx.com/mobiledev.php)<br>[&#x200B; モバイルアプリでの位置情報テスト &#x200B;](https://qacumtester.wordpress.com/2014/02/27/location-testing-in-mobile-apps/) | GPX ファイルが作成され、アプリプロジェクトに読み込まれます。 |
| 7 | 他の操作を行わなくても、Android StudioまたはXCodeからアプリケーションを起動し、トラッキング場所へのアクセスをリクエストするための適切なアラートを確認できます。 *Always Allow*&#x200B;権限をクリックします。<br><br> デバイス シミュレーターを使用する代わりに、コンピューターに接続されている実際のデバイスを使用することをお勧めします。 | IDEを介して読み込まれたアプリケーションに位置情報の要求プロンプトが表示される |
| 8 | 場所の権限が承認されると。 Places SDKは、デバイスの現在の場所を取得し、リージョンモニタリングコードは、現在の場所から最も近い20のPOIのモニタリングを開始する必要があります | 表の下にあるログサンプルを参照してください。 |
| 9 | XCodeまたはAndroid studioの異なる場所を切り替えると、特定のPOIのエントリイベントが生成されます。 POIへのエントリには、次のログが必要です。 | 表の下にあるログサンプルを参照してください。 |
| 10 | リージョンモニターが近くのPOIを見つけたら、位置情報のpingを送信してテストする必要があります。 Launchで、Geo-fence エントリに基づいてPlaces拡張機能を使用してトリガーする新しいルールを作成します。 次に、モバイルコアを使用して新しいアクションを作成し、Postbackを送信します。 Slack Webhook アプリを作成すると、位置情報の出入りを確認できます。 Slack Webhook アプリの作成について詳しくは、[受信Webhookを使用したメッセージの送信を参照してください。](https://api.slack.com/messaging/webhooks) |  |
| 10a | Launchで、Places拡張機能のデータ要素が次のように追加されていることを確認します。<br>現在のPOI名<br>現在のPOI長<br>現在のPOI長<br>現在のPOI長<br>最後に入力した長さ<br>最後に入力した長さ<br>最後に終了した長さ<br>最後に終了した長さ<br> タイムスタンプ<br> |  |
| 10b | イベント = POIを入力する場所で新しいルール→作成します |  |
| 10c | アクションの作成= Mobile Core → Postback |  |
| 10d | Slack アプリのWebhook URL （例：https://hooks.slack.com/services/TKN5FKS68/BNFP7SVD...）を使用します。 |  |
| 10e | 投稿の本文は次のようになります：`{text: User is in POI -  {%%Last Entered POI Name%%} in {%%Last Entered POI City%%} additional information: Radius:{%%Last Entered POI Radius%%} Timestamp: {%%timestamp%%}}`。 <br>ここで作成した特定のデータ要素を使用してください。 |  |
| 10f | Launchで新しいデータ要素とルールの変更をすべて公開していることを確認します。 （Launch インターフェイスの右上にある作業中の開発ライブラリを選択する必要があります）。 |  |
| 11 | 開発者IDEのGPXの場所の間を反転して、アプリケーションを起動し、もう一度テストします。 | これで、開発環境で別の場所を選択すると、各POIのエントリが表示されるSlackの通知が表示されます。 |
|  | **簡単な概要ポイント**<br>&#x200B;このテストはすべて、特定のPOIの場所に移動することなく、ローカルで実行できます。 検証テストは、アプリケーションが正しく設定され、その場所に対する正しい権限を受け取っていることを確認するのに役立ちます。 <br><br>この検証により、定義済みのPOIが地域モニタリング実装で正しく動作しているという確信も得られます。  この手順の後、Campaignでメッセージのテストを開始し、POIのエントリと終了に基づいて適切なメッセージが表示されるかどうかを確認します。 |  |
|  | **Places サービスを使用したAdobe Campaign Standard アプリ内メッセージのテスト。** |  |
| 12 | メインのCampaign ダッシュボードで、新しいアプリ内メッセージを設定します（タイプ = ブロードキャスト） |  |
| 12a | トリガーで、**Places event type - Entryをトリガー**&#x200B;として選択します。 |  |
| 12b | **[!UICONTROL Places Custom metadata]**&#x200B;を追加フィルターとして選択します。POI タイプ = Last Entered POIを使用します。<br>ほとんどの場合、**[!UICONTROL Last Entered]**&#x200B;は&#x200B;**[!UICONTROL 現在のPOI]**&#x200B;と同じであるため、**[!UICONTROL Last Entered]**&#x200B;をPOI タイプとして使用します。 <br><br>**[!UICONTROL 現在のPOI &#x200B;]**&#x200B;は、重複するPOI ジオフェンスがあるインスタンスでのみ使用してください。 この場合、これらのPOIをランク付けする必要があります。その場合、**[!UICONTROL &#x200B;現在のPOI &#x200B;]**&#x200B;は、ユーザーが現在使用している可能性のある2または3つのジオフェンスのうち、上位にランク付けされたPOIを表示します。 |  |
| 12c | メッセージを受信するPOIを絞り込むのに役立つカスタムメタデータキーを選択します。 |  |
| 12d | 頻度と期間については、条件が気に入らない場合はトリガーの有効期限を短くできるように、1日または2日に制限してください。 |  |
| 12e | Always/OnceまたはUntil click-throughの場合は、*ALWAYS*&#x200B;を選択して、複数の場所でテストを行うことができます。 | 適切なメタデータ条件を満たす場所の変更をシミュレートすると、アプリ内メッセージが常に表示されます。 |
| 12f | 表示には、「ローカル通知」以外のオプションを選択します。 これにより、アプリをフォアグラウンドでテストする際に見やすくなります。） |  |
| 12g | アプリ内メッセージの準備/確認とデプロイ。 |  |
| 13 | 開発環境で、新しいキャンペーンルールがダウンロードされていることを確認するには、アプリケーションを終了して再度起動します。 | 新しいCampaign ルールファイルをデバイスにダウンロードするには、アプリケーションを完全に再度起動する必要があることを忘れないでください。 |
| 14 | 開発アプリケーションで、以前に作成したGPX ファイルを使用して場所を切り替えます。 | 以前に設定した条件に基づいて、アプリ内メッセージが表示されます。 |
| 15 | 次のテストでは、基本的に以前と同じ手順をコピーしますが、今回はローカル通知をテストします。 | 期待される結果は、一致する条件が満たされるたびにローカル通知が表示されることです。 |
| 16 | 新しいアプリ内メッセージ（type = broadcast）を設定します。 |  |
| 16a | トリガーで、**[!UICONTROL Places event type]** - **[!UICONTROL Entryをトリガー]**&#x200B;として選択します。 |  |
| 16b | 場所カスタムメタデータを追加のフィルターとして選択します。**[!UICONTROL POI タイプ]** = **[!UICONTROL 最後に入力したPOI]**&#x200B;を使用します。 |  |
| 16c | メッセージを受信するPOIを絞り込むのに役立つカスタムメタデータキーを選択します。 |  |
| 16d | 頻度と期間の場合は、1日または2日のみを保持します。これにより、条件が気に入らない場合は、より短い期間でトリガーの有効期限を切ることができます。 |  |
| 16e | Always/Onceまたはクリックスルーまでの場合は、**[!UICONTROL ALWAYS]**。 |  |
| 16f | 表示タイプとして、**[!UICONTROL ローカル通知]**&#x200B;を選択します。 |  |
| 16g | アプリ内メッセージの準備/確認とデプロイ。 |  |
| 17 | 開発者環境で、デバイスを接続し、ビルドで&#x200B;**[!UICONTROL Play]**&#x200B;を押します。 その場所が機能していることを確認したら、アプリケーションをバックグラウンド化し、XcodeまたはAndroid Studioで場所を切り替えます。 引き続き、場所の変更を示すコンソールの読み上げや、トリガーで設定された条件に応じたローカル通知の表示も表示されます。 （1～2秒間の遅延が発生する場合があります）。 | 期待される結果は、一致する条件を満たすたびにローカル通知が表示されることです。 |
|  | **概要ポイント** <br>この段階では、ローカル環境でPOI エントリが表示されます。 POI作業にもとづいたキャンペーンのメッセージが表示されます。 エラーが発生した場合は、Slack通知が送信されなかったかどうかを確認します。 Slack メッセージがない場合は、新しい場所のエントリが記録されていない可能性があるため、アプリケーションコンソールを確認してください。 結果が成功した場合、アプリケーションが正しく動作していること、およびPlaces サービスとCampaign メッセージングサービスも正しく動作していることを確認できます。 |  |
|  | **オンサイトテスト** <br>場所でテストを行う場合、変更する必要はあまりありません。 スタックのポストバックをアクティブに保つことで、デバイスがその場所に対する入口と出口を取得しているかどうかを把握するのに役立ちます。 |  |
| 18 | Wi-Fiとモバイル通信を無効にして始まるデバイスでテストを行い、POI地域で1回有効にします。 | エラーが発生した場合は、Slackでジオフェンスのエントリと通知を受け取っているかどうかを確認します。 Slack通知のタイムスタンプは何ですか？ |
| 19 | モバイル通信のみ有効にし、Wi-Fiがオフになっている状態でテストを行います。 |  |
| 20 | モバイルとWi-Fiの両方をオンにしてテストを実施します。 |  |
|  | **要約点** <br> オンサイトテストは、開発テストと密接に一致する必要があります。 POI ジオフェンスで過ごす時間、セル信号の可用性、近くのWi-Fi アクセスポイントの強度など、ユーザーの場所を決定する際に発生する可能性のある環境要因がいくつかあることに留意してください。 |  |

## ログサンプル

**手順8 :**&#x200B;場所の更新中にiOSとAndroidのログが必要です

**iOS**

```
[AdobeExperienceSDK DEBUG <Places>]: Requesting 20 nearby POIs for device location (<lat>, <longitude>)
[AdobeExperienceSDK DEBUG <Places>]: Response from Places Query Service contained <n> nearby POIs   
```

**Android**

```
PlacesExtension - Dispatching nearby places event with n POIs   
```

**手順9 :** イベント中にiOSとAndroidのログが予想されます

**iOS**

```
[AdobeExperienceSDK TRACE <Places>]: Dispatching Places region entry event for place ID <poiId>
```

**Android**

```
PlacesExtension -  Dispatching Places Region Event for <poi name> with eventType entry
```
