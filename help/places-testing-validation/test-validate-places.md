---
title: 場所のテストと検証
description: ここでは、場所をテストして検証する方法について説明します。
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# ロケーションサービスをテストするための推奨事項 {#test-validate-loc-svc}

多くの顧客や組織は世界中でPOIを定義するので、ロケーションサービスがアプリケーションとどのように相互作用するかをシミュレートしテストする方法が重要です。

この情報は、定義されたPOIとユーザーの現在の場所に基づいて正しくトリガーされているロケーションサービスの入口と出口をテストし、検証する方法を理解するのに役立ちます。

環境変数は位置信号と精度の要因となる可能性があるので、まず開発者ツールとシミュレートした位置エントリをローカルで使用して、ベースライン結果を確立することをお勧めします。 ここでの目標は、すべての場所イベントが正しく機能していることを検証することです。

場所のイベントが正しく検証されると、ソリューションの統合（例えば、Analytics、TargetおよびCampaign）をテストできます。 テスト作業を支援するには、ポストバックを使用してSlack Webhooksを設定し、個々の開発環境にGPXファイルを読み込む必要があります。

>[!IMPORTANT]
>
>この計画では、 [](https://places.adobe.com) Location Service Management UIでPOIが作成済みで、Places拡張機能とPlaces Monitor拡張機能の最新バージョンがインストールされ、正しく設定されていることを前提としています。

| 手順 ： | 説明 | 期待される結果 |
|--- |--- |--- |
| 1 | Androidに対して正しいマニフェストキーが入力され、追跡場所へのアクセス権が付与されていることを確認します。 詳しくは、マニフェストへの権 [限の追加を参照してください](https://docs.adobe.com/content/help/en/places/using/places-ext-aep-sdks/places-monitor-extension/using-places-monitor-extension.html#add-permissions-to-the-manifest)。 | 確認済み |
| 1a | 場所の更新がiOSで設定されていることを確認します。 また、iOSで適切なPLISTキーが設定され、場所を追跡するユーザー権限を要求できることを確認します。 詳しくは、バックグラウンドでの位置 [の更新の有効化を参照してください。](https://docs.adobe.com/content/help/en/places/using/places-ext-aep-sdks/places-monitor-extension/using-places-monitor-extension.html#enable-location-updates-background) | 確認済み |
| 2 | iOSに対して設定されている監視モードを確認します。 連続モードでは、精度と持続性が向上しますが、バッテリー寿命が大幅に低下します。 詳しくは、監視モード( [iOSのみ)を参照してください。](https://docs.adobe.com/content/help/en/places/using/places-ext-aep-sdks/places-monitor-extension/places-monitor-api-reference.html#monitoring-mode-ios-only) | 大幅な変更または継続的な変更 |
| 3 | 複数のPOIライブラリを使用する場合は、エクスペリエンスプラットフォーム起動用の場所拡張で適切なライブラリが選択されていることを確認します。 | 確認済み |
| 4 | Mobile coreおよび場所/場所モニターの最新バージョンが、GradleまたはCocoaPod経由でアプリにバンドルされていることを確認します。 | 確認済み — 最近の更新の詳細については、リリースノートを参照 [してください。](/help/release-notes.md) |
| 5 | テスト用に正しい環境が設定されていることを確認します。 起動環境IDは、起動開発環境と一致する必要があります。 | 確認済み |
| 6 | テストするPOIごとにGPXファイルを作成します。 GPXファイルは、ローカル開発環境で、場所のエントリをシミュレートするために使用できます。 GPXファイルの作成と使用について詳しくは、次を参照してください。iOSシミュレー <br>[ター用のGPXファイル[閉じる]](https://stackoverflow.com/questions/17292783/gpx-files-for-ios-simulator)<br>[https://mapstogpx.com/mobiledev.](https://mapstogpx.com/mobiledev.php)<br>[phpモバイルアプリでの場所のテスト](https://qacumtester.wordpress.com/2014/02/27/location-testing-in-mobile-apps/) | GPXファイルが作成され、アプリケーションプロジェクトに読み込まれます。 |
| 7 | 他の操作を行わないと、Android studioまたはXCodeからアプリケーションを起動し、適切なアラートを確認して、追跡場所へのアクセスをリクエストできます。 「常に許可」 *権限をクリックします* 。<br><br>デバイスシミュレーターを使用する代わりに、コンピューターに接続された実際のデバイスを使用することをお勧めします。 | 場所の要求プロンプトは、IDEを使用して読み込んだアプリケーションで表示する必要があります |
| 8 | 場所の権限が受け入れられたら、 場所SDKはデバイスの現在の場所を取得し、場所モニター拡張機能は現在の場所から最も近い20個のPOIの監視を開始します | 表の下のログサンプルを参照してください。 |
| 9 | XCodeまたはAndroid studioで異なる場所を切り替えると、特定のPOIに対してエントリイベントが生成されます。 POIへのエントリ時には、以下のログが必要です。 | 表の下のログサンプルを参照してください。 |
| 10 | プレースモニターが近くのPOIを見つけたら、場所のpingを送信してテストする必要があります。 「起動」で、「場所」拡張を使用してジオフェンスのエントリに基づいてトリガーする新しいルールを作成します。 次に、Mobile coreを使用してポストバックを送信し、新しいアクションを作成します。 Slack Webhookアプリを作成すると、場所の入口と出口を確認できます。 Slack Webhookアプリの作成について詳しくは、「受信Webhookを使用したメ [ッセージの送信」を参照してください。](https://api.slack.com/messaging/webhooks) |  |
| 10a | 「起動」で、「場所」拡張に次のデータ要素が追加されていることを確認します。現在 <br>POI名現在POI<br>lat POI<br>lat POI<br>long最後に入力された<br>POI<br>last最後に入力された<br>LONG最後に出力されたPOI<br><br><br>LAT最後に出力されたPOI最新のPOI long |  |
| 10b | イベント=配置を含む新しいルールを作成し、「POIを入力」を選択します。 |  |
| 10c | アクションの作成=モバイルコア→ポストバック |  |
| 10d | SlackアプリのWebフックURLを使用します(例：https://hooks.slack.com/services/TKN5FKS68/BNFP7SVD....)。 |  |
| 10e | 投稿の本文は次のようになります。 `{text: User is in POI -  {%%Last Entered POI Name%%} in {%%Last Entered POI City%%} additional information: Radius:{%%Last Entered POI Radius%%} Timestamp: {%%timestamp%%}}`. <br>ここで作成した特定のデータ要素を使用していることを確認します。 |  |
| 10f | 「起動」で、すべての新しいデータ要素とルールの変更を発行します。 （起動インターフェイスの右上で、作業用開発ライブラリを選択する必要があります）。 |  |
| 11 | 開発者IDEでGPXの場所をめくってアプリケーションを再び起動し、テストします。 | 開発環境で別々の場所を選択すると、Slack通知に各POIのエントリが表示されます。 |
|  | **このテスト**<br>&#x200B;の概要一部は、特定のPOIの場所に移動する必要なく、ローカルで実行できます。 検証テストは、アプリケーションが正しく設定され、場所に対する正しい権限を受け取っていることを確認するのに役立ちます。 <br><br>また、この検証により、定義したPOIがプレースモニター拡張機能で正しく機能していることを確認できます。  この手順の後、Campaignでメッセージをテストし、POIの入口と出口に基づいて適切なメッセージが表示されるかどうかを確認します。 |  |
|  | **ロケーションサービスを使用したAdobe Campaign Standardのアプリ内メッセージのテストを参照してください。** |  |
| 12 | メインのキャンペーンダッシュボードで、新しいアプリ内メッセージ（タイプ=ブロードキャスト）を設定します。 |  |
| 12a | トリガーで、「 **Places」イベントタイプの「Entry」をトリガーとして選択します**。 |  |
| 12b | 「 **[UICONTROL」を選択すると、カスタムメタデータが追加のフィルタ]**- POIタイプ=最後に入力されたPOIを使用します。<br>POIタイプ**[!UICONTROL Last Entered]** は、ほとんどの場合と同じなので、 **[!UICONTROL Last Entered]**使用します**[!UICONTROL Current POI]**。 <br><br>**[!UICONTROL Current POI]** は、重複するPOI地域フェンスがある場合にのみ使用する必要があります。 この場合、これらのPOIをRANKEDに設定する必要があります。その後、ユーザが現在参加している可能性のある2 ～ 3つのジオフェンスのうち、上位のPOIがに表示されます。 **[!UICONTROL Current POI]** |  |
| 12c | メッセージを受信するPOIを絞り込むのに役立つカスタムメタデータキーを選択します。 |  |
| 12d | 頻度と期間については、1 ～ 2日に制限し、条件が気に入らない場合は、短い期間でトリガーの有効期限を切れるようにします。 |  |
| 12e | 「常に1回」または「クリックスルーまで」では、「 *ALWAYS* 」を選択して、複数の場所でテストできるようにします。 | 適切なメタデータ条件を満たす場所の変更をシミュレートすると、アプリ内メッセージが常に表示されます。 |
| 12f | 表示に対して、「ローカル通知」以外のオプションを選択します。 これにより、前景でアプリを使用してテストする際に、見やすくなります)。 |  |
| 12g | アプリ内メッセージを準備/確認し、デプロイします。 |  |
| 13 | 開発環境で、新しいキャンペーンルールをダウンロードするには、アプリケーションを終了してから再起動します。 | 新しいCampaignルールファイルをデバイスにダウンロードするには、アプリケーションを再び完全に起動する必要があることを忘れないでください。 |
| 14 | 開発アプリケーションで、以前に作成したGPXファイルを使用して場所を切り替えます。 | 以前に設定した条件に基づいて、アプリ内メッセージが表示されます。 |
| 15 | 次のテストでは、基本的に前と同じ手順をコピーしますが、今回はローカル通知をテストします。 | 結果として、一致する条件が満たされるたびにローカル通知が表示されます。 |
| 16 | 新しいアプリ内メッセージを設定します（タイプ=ブロードキャスト）。 |  |
| 16a | トリガーで、 **[!UICONTROL Places event type]**— を選択しま**[!UICONTROL Entry as the trigger]**&#x200B;す。 |  |
| 16b | 追加のフィルターとして「カスタムメタデータを配置」を選択し、「=」を **[!UICONTROL POI type]**使用しま**[!UICONTROL Last Entered POI]**&#x200B;す。 |  |
| 16c | メッセージを受信するPOIを絞り込むのに役立つカスタムメタデータキーを選択します。 |  |
| 16d | 頻度と期間については、1 ～ 2日のみを保持し、条件が気に入らない場合は、トリガーの有効期限を短い期間で切れるようにします。 |  |
| 16e | 「常に/1回」または「まで」のクリックスルーの場 **[!UICONTROL ALWAYS]**合、 |  |
| 16f | 表示タイプとして、を選択しま **[!UICONTROL Local Notification]**す。 |  |
| 16g | アプリ内メッセージを準備/確認し、デプロイします。 |  |
| 17 | 開発者環境で、デバイスを接続し、ビルド **[!UICONTROL Play]**を押します。 その場所が機能していることを確認したら、アプリケーションをバックグラウンドにして、XcodeまたはAndroid studioで場所の切り替えを続行します。 場所の変更を示すコンソールの読み取りは引き続き表示され、トリガーに設定した条件に応じてローカル通知も表示されます。 （1 ～ 2秒の遅延が生じる場合があります）。 | 結果として、一致条件が満たされるたびにローカル通知が表示されます。 |
|  | **概要ポイント**<br>この段階では、ローカル環境でPOIエントリを確認する必要があります。 また、POIの仕事に基づくキャンペーンからのメッセージも表示されます。 エラーが発生した場合は、Slack通知が発生しなかったかどうかを確認します。 Slackメッセージがない場合は、新しい場所のエントリが記録されていない可能性があるので、アプリケーションコンソールを確認します。 結果が正常に得られた場合は、アプリケーションが正しく動作し、ロケーションサービスとキャンペーンのメッセージングサービスも正しく動作していることを確認できます。 |  |
|  | **オンサイトテスト場所でのテ**<br>ストでは、大きな変更は必要ありません。 スラックポストバックをアクティブにしておくと、デバイスがその場所のエントリを取得し、終了するかどうかを把握するのに役立ちます。 |  |
| 18 | Wi-Fiとセルラーが無効になっているデバイスでテストを実行し、POI領域で1回有効にします。 | エラーが発生した場合は、Slackでジオフェンスのエントリと通知を取得するかどうかを確認します。 Slack通知のタイムスタンプは何ですか。 |
| 19 | 携帯電話のみを有効にし、Wi-Fiをオフにしてテストを実施します。 |  |
| 20 | 携帯電話とWi-Fiの両方をオンにしてテストを実施します。 |  |
|  | **SUMMARY POINT** On <br>Site Testingは、開発テストと密接に一致する必要があります。 POIジオフェンスでの滞在時間、セル信号の可用性、近くのWi-Fiアクセスポイントの強さなど、ユーザーの場所を決定する際に生じる環境要因がいくつかあることに注意してください。 |  |

## ログサンプル

**** 手順8 :場所の更新中にiOSおよびAndroidのログが予想される

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

**** 手順9:イベント中にiOSおよびAndroidのログが予想される

**iOS**

```
[AdobeExperienceSDK TRACE <Places>]: Dispatching Places region entry event for place ID <poiId>
```

**Android**

```
PlacesExtension -  Dispatching Places Region Event for <poi name> with eventType entry
```
