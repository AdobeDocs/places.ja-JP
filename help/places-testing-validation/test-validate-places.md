---
title: Placesサービスのテストと検証
description: この節では、Places Serviceのテストおよび検証方法について説明します。
translation-type: tm+mt
source-git-commit: 954bd9a12ede841d189138dfbe3d65ad4c1bd3c3
workflow-type: tm+mt
source-wordcount: '1735'
ht-degree: 2%

---


# Recommendationsがプレースサービスをテスト {#test-validate-loc-svc}

多くの顧客や組織は世界中でPOIを定義するので、Places Serviceがアプリケーションとどのように相互作用するかをシミュレートし、テストする方法を持つことが重要です。 この情報は、定義されたPOIとユーザーの現在の場所に基づいて正しくトリガーされているPlaces Serviceの入口と出口をテストし、検証する方法を理解するのに役立ちます。

環境変数は位置信号と精度の要因になる可能性があるので、まず開発者ツールとシミュレーションした位置エントリをローカルで操作して、ベースライン結果を確立することをお勧めします。 目標は、すべての場所のイベントが正しく機能していることを検証することです。 場所のイベントが正しく検証されると、ソリューションの統合(Analytics、ターゲット、キャンペーンなど)をテストできます。 テストアクティビティを支援するために、ポストバックを含むSlackWebフックを設定し、個々の開発環境にGPXファイルを読み込む必要があります。

>[!IMPORTANT]
>
>この計画では、POIが [](https://places.adobe.com) Places Service UIで作成済みで、Places拡張機能とPlaces Monitor拡張機能の最新バージョンがインストールされ、正しく構成されていることを前提としています。 詳しくは、「 [Places拡張子](/help/places-ext-aep-sdks/places-extension/places-extension.md) 」および「 [Places Monitor拡張子」を参照してください](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md)。

| 手順 | 説明 | 期待される結果 |
|--- |--- |--- |
| 1 | Androidに対して正しいマニフェストキーが入力され、追跡場所へのアクセス権が付与されていることを確認します。 詳しくは、マニフェストへの [権限を参照してください](https://docs.adobe.com/content/help/en/places/using/places-ext-aep-sdks/places-monitor-extension/using-places-monitor-extension.html#add-permissions-to-the-manifest)。 | 確認済み |
| 1a | 場所の更新がiOSで設定されていることを確認します。 また、iOSで適切なplist keysが設定されていて、場所を追跡するユーザー権限を要求できることを確認してください。 詳しくは、「バックグラウンドで場所の更新を [有効にする」を参照してください。](https://docs.adobe.com/content/help/en/places/using/places-ext-aep-sdks/places-monitor-extension/using-places-monitor-extension.html#enable-location-updates-background) | 確認済み |
| 2 | iOSに対して設定されている監視モードを確認します。 連続モードでは、精度と持続性が向上しますが、バッテリーの寿命が大幅に低下します。 詳しくは、「 [監視モード（iOSのみ）」を参照してください。](https://docs.adobe.com/content/help/en/places/using/places-ext-aep-sdks/places-monitor-extension/places-monitor-api-reference.html#monitoring-mode-ios-only) | 重要な変更または継続的な変更 |
| 3 | 複数のPOIライブラリを使用する場合は、[Experience Platform Launch用の場所]で適切なライブラリが選択されていることを確認します。 | 確認済み |
| 4 | Mobile CoreおよびPlaces/Places Monitorの最新バージョンが、GradleまたはCocoaPodを使用してアプリにバンドルされていることを確認します。 | 確認済み — 最近の更新について詳しくは、 [リリースノートを参照してください。](/help/release-notes.md) |
| 5 | テスト用に正しい環境が設定されていることを確認します。 起動環境IDは、起動の開発環境と一致する必要があります。 | 確認済み |
| 6 | テストするPOIごとにGPXファイルを作成します。 GPXファイルは、ローカル開発環境で、場所のエントリをシミュレートするために使用できます。 GPXファイルの作成と使用について詳しくは、次を参照してください。 <br>[iOSシミュレーター用のGPXファイル（閉じた状態）](https://stackoverflow.com/questions/17292783/gpx-files-for-ios-simulator)<br>[https://mapstogpx.com/mobiledev.](https://mapstogpx.com/mobiledev.php)<br>[phpLOCATION TESTING IN MOBILE APPS](https://qacumtester.wordpress.com/2014/02/27/location-testing-in-mobile-apps/) | GPXファイルが作成され、アプリケーションプロジェクトに読み込まれます。 |
| 7 | 他の操作を行わないと、Android StudioまたはXCodeからアプリケーションを起動し、適切なアラートを確認して、トラッキング場所へのアクセスをリクエストできます。 「 *常に許可* 」権限をクリックします。<br><br>デバイスシミュレーターを使用する代わりに、コンピューターに接続された実際のデバイスを使用することをお勧めします。 | 場所の要求プロンプトは、IDEを介して読み込まれたアプリケーションで表示する必要があります |
| 8 | 場所の権限が受け入れられたら、 配置SDKはデバイスの現在の場所を取得し、配置モニター拡張は開始で現在の場所から最も近い20個のPOIを監視します | 表の下のログサンプルを参照してください。 |
| 9 | XCodeまたはAndroid Studioで異なる場所を切り替えると、特定のPOIに対するエントリイベントが生成されます。 POIへのエントリ時に、以下のログが必要になります。 | 表の下のログサンプルを参照してください。 |
| 10 | プレースモニターが近くのPOIを見つけたら、場所をpingアウトしてテストする必要があります。 「起動」で、場所拡張子を使用してジオフェンスのエントリに基づいてトリガーする新しいルールを作成します。 次に、Mobile Coreを使用してポストバックを送信する新しいアクションを作成します。 SlackのWebフックアプリを作成すると、場所のエントリと出口を確認できます。 SlackWebhookアプリの作成について詳しくは、「受信Webhookを使用したメッセージの [送信」を参照してください。](https://api.slack.com/messaging/webhooks) |  |
| 10a | 「Launch」で、Places拡張のデータ要素が以下を含めて追加されていることを確認します。 <br>現在のPOI<br>名現在のPOI POI POI<br>LAT現在のPOI<br>longLast入力<br>名最後の入力最後の入力最後の入力最後の入力最後<br>の出力最後の出力<br>名最後の出力最後の出力<br><br><br>最後の出力タイムスタンプ |  |
| 10b | イベント=場所= POIと入力して新しいルールを作成する |  |
| 10c | アクションの作成=モバイルコア→ポストバック |  |
| 10d | SlackアプリのWebフックURLを使用します(例：https://hooks.slack.com/services/TKN5FKS68/BNFP7SVD....)。 |  |
| 10e | 投稿の本文は次のようになります。 `{text: User is in POI -  {%%Last Entered POI Name%%} in {%%Last Entered POI City%%} additional information: Radius:{%%Last Entered POI Radius%%} Timestamp: {%%timestamp%%}}`. <br>ここで作成した特定のデータ要素を使用していることを確認します。 |  |
| 10f | 「起動」で、新しいデータ要素およびルールの変更をすべて発行してください。 （起動インターフェイスの右上で、作業用開発ライブラリを選択する必要があります）。 |  |
| 11 | 開発者IDEでGPXの場所をフリップして、アプリケーションを起動し、再びテストします。 | 開発環境で異なる場所を選択すると、各POIのエントリがSlack通知に表示されます。 |
|  | **簡易概要**<br>&#x200B;ポイントこのテストのすべては、特定のPOIの場所に移動することなく、ローカルで実行できます。 検証テストは、アプリケーションが正しく設定され、その場所に対する正しい権限を受け取っていることを確認するのに役立ちます。 <br><br>また、この検証により、定義したPOIがPlaces Monitor拡張機能で正しく動作していることを確認できます。  この手順の後、キャンペーンでのメッセージのテストを開始し、POIの入口と出口に基づいて適切なメッセージが表示されるかどうかを確認します。 |  |
|  | **Placesサービスを使用したAdobe Campaign Standardのアプリ内メッセージのテスト」を参照してください。** |  |
| 12 | メインキャンペーンダッシュボードで、新しいアプリ内メッセージ（タイプ=ブロードキャスト）を設定します。 |  |
| 12a | トリガーで、トリガーとして「 **配置イベントタイプ — 入口**」を選択します。 |  |
| 12b | 追加のフィルタ **[!UICONTROL Places Custom metadata]** として選択します。POIタイプを使用=最後に入力されたPOIを使用します。<br>POIタイプ **[!UICONTROL Last Entered]** は、ほとんどの場合と同じなので、POIタイプ **[!UICONTROL Last Entered]** として使用し **[!UICONTROL Current POI]**&#x200B;ます。 <br><br>**[!UICONTROL Current POI]**は、重複するPOIジオフェンスがある場合にのみ使用する必要があります。 この場合、これらのPOIを「ランク付け」にする必要があります。その後、ユーザーが現在参加している可能性のある2 ～ 3つのジオフェンスのうち、上位のPOIがに表示されます。**[!UICONTROL Current POI]** |  |
| 12c | メッセージを受信するPOIを絞り込むのに役立つカスタムメタデータキーを選択します。 |  |
| 12d | 頻度と期間については、条件が気に入らない場合に短い期間でトリガーの有効期限を切れるように、1 ～ 2日に制限します。 |  |
| 12e | 「常に/1回」または「クリックスルーまで」の場合は、「 *常に* 」を選択して、複数の場所でテストできるようにします。 | 適切なメタデータ条件を満たす場所の変更をシミュレートすると、アプリ内メッセージが常に表示されます。 |
| 12f | 表示に対して、「ローカル通知」以外のオプションを選択します。 これにより、前景でアプリを使用してテストする際に、見やすくなります)。 |  |
| 12g | アプリ内メッセージを準備/確認し、デプロイします。 |  |
| 13 | 開発環境で、新しいキャンペーンルールをダウンロードするには、を終了して、もう一度アプリケーションを起動します。 | 新しいキャンペーンルールファイルをデバイスにダウンロードするには、アプリケーションを再び完全に起動する必要があることを忘れないでください。 |
| 14 | 開発アプリケーションで、以前に作成したGPXファイルを使用して場所を切り替えます。 | 以前に設定した条件に基づいて、アプリ内メッセージが表示されます。 |
| 15 | 次のテストでは、基本的に前と同じ手順をコピーしますが、今回はローカル通知をテストします。 | 結果として、一致する条件が満たされるたびにローカル通知が表示されます。 |
| 16 | 新しいアプリ内メッセージを設定します（タイプ=ブロードキャスト）。 |  |
| 16a | トリガーで、 **[!UICONTROL Places event type]** — を選択し **[!UICONTROL Entry as the trigger]**&#x200B;ます。 |  |
| 16b | 追加のフィルターとして「カスタム」メタデータを配置する — 「 **[!UICONTROL POI type]** =」を使用 **[!UICONTROL Last Entered POI]**&#x200B;します。 |  |
| 16c | メッセージを受信するPOIを絞り込むのに役立つカスタムメタデータキーを選択します。 |  |
| 16d | 頻度と期間については、1 ～ 2日のみにして、条件が気に入らない場合は、短い期間でトリガーの有効期限を切れるようにします。 |  |
| 16e | 「常に/1回」または「クリックスルーまで」の場合は、 **[!UICONTROL ALWAYS]**&#x200B;です。 |  |
| 16f | 表示タイプに対して、を選択し **[!UICONTROL Local Notification]**&#x200B;ます。 |  |
| 16g | アプリ内メッセージを準備/確認し、デプロイします。 |  |
| 17 | 開発者環境で、デバイスを接続し、ビルド **[!UICONTROL Play]** を押します。 その場所が機能していることを確認したら、アプリケーションをバックグラウンドにして、XcodeまたはAndroid Studioで場所の切り替えを続行します。 場所の変更を示すコンソールの読み取りは引き続き表示され、トリガーに設定した条件に応じてローカル通知が表示される必要があります。 （1 ～ 2秒の遅延が生じる場合があります）。 | 結果として、一致条件が満たされるたびにローカル通知が表示されます。 |
|  | **概要ポイント**<br>この段階では、ローカル環境にPOIエントリが表示されます。 また、POI作業に基づくキャンペーンからのメッセージも確認する必要があります。 エラーが発生した場合は、Slack通知が発生しなかったかどうかを確認します。 Slackメッセージがない場合は、アプリケーションコンソールを確認してください。これは、新しい場所のエントリが記録されていない可能性があるためです。 結果が成功した場合は、アプリケーションが正しく動作していること、およびプレースサービスとキャンペーンのメッセージングサービスも正しく動作していることを確認できます。 |  |
|  | **オンサイトテスト**<br>：場所でテストする際に大きな変更はありません。 スラックポストバックを有効にしておくと、デバイスがその場所に対して入口と出口を得ているかどうかを把握するのに役立ちます。 |  |
| 18 | Wi-Fiとセルラーが無効になっているデバイスでテストを実施し、POI領域で1回だけ有効にします。 | エラーが発生した場合は、Slackでジオフェンスのエントリと通知を取得するかどうかをメモしてください。 Slack通知のタイムスタンプは何ですか。 |
| 19 | セルラーのみを有効にし、wi-fiをオフにしてテストを実行します。 |  |
| 20 | 携帯電話とWi-Fiの両方をオンにしてテストを実施します。 |  |
|  | **サマリポイント**<br>オンサイトテストは、開発テストに近い結果が得られます。 POIジオフェンスでの滞在時間、セル信号の可用性、近くのWiFiアクセスポイントの強さなど、ユーザーの場所の決定に影響を及ぼす環境要因がいくつかあることに注意してください。 |  |

## ログサンプル

**手順8:** 場所の更新中にiOSおよびAndroidのログが予期される

**iOS**

```
[AdobeExperienceSDK DEBUG <com.adobe.placesMonitor>]: Authorization status changed: Always
[AdobeExperienceSDK DEBUG <Places>]: Requesting 20 nearby POIs for device location (<lat>, <longitude>)
[AdobeExperienceSDK DEBUG <Places>]: Response from Places Query Service contained <n> nearby POIs
[AdobeExperienceSDK DEBUG <com.adobe.placesMonitor>]: Received a new list of POIs from Places: (
<ACPPlacePoi: 0x600002b75a40> Name: <poi name>; ID:<poi id>; Center: (<lat>, <long>); Radius: <radius>
..
..)   
```

**Android**

```
PlacesMonitor - All location settings are satisfied to monitor location
PlacesMonitor - PlacesMonitorInternal : New location obtained: <latitude> <longitude> Attempting to get the near by pois
PlacesExtension - Dispatching nearby places event with n POIs
PlacesMonitor - Attempting to Monitor POI with id <poi id> name <poi name> latitude <lat> longitude <longitude>
PlacesMonitor - Attempting to Monitor POI with id <poi id> name <poi name> latitude <lat> longitude <longitude>
PlacesMonitor - Attempting to Monitor POI with id <poi id> name <poi name> latitude <lat> longitude <longitude>
...
...
PlacesMonitor - Successfully added n fences for monitoring
```

**手順9:** イベント中にiOSおよびAndroidのログが予想される

**iOS**

```
[AdobeExperienceSDK TRACE <Places>]: Dispatching Places region entry event for place ID <poiId>
```

**Android**

```
PlacesExtension -  Dispatching Places Region Event for <poi name> with eventType entry
```
