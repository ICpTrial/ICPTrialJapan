# ICPの全体像の把握

ICPの管理コンソールを開いて、ICPの全体を確認してみましょう

## ログイン

コンソールからFirefoxブラウザを開き、IBMCloudPrivateConsoleブックマークをクリックします。ユーザーIDはadmin、パスワードはicp1nCl0udです。

## ダッシュボード

初期画面としてダッシュボードが表示されます。現在のシステムおよびリソースのメトリックを確認できます。
- システムの概要：クラスター内のノード、ストレージ、およびアプリケーションに関する一般情報を表示します。
- リソースの概要：リソースの使用に関する情報を表示します。 各リソースに関する以下の情報を表示できます。
![Dashboard](https://github.com/ICpTrial/ICPTrialJapan/blob/master/pictures/dashboard.png)

## プラットフォーム

コンソール左上にあるメニューから、「プラットフォーム」(Platform)を選択します。ここでは、ICP環境を維持するための機能を提供します。
大別して、物理構成の確認をする、または、管理サービスを使用するための機能が表示されます。
- 物理方法を確認する
  - ネットワーク：ポッド間のネットワーク・アクセスを管理するネットワーク・ポリシーを設定します。ネットワーク・ポリシーをセットアップするには、クラスターのインストール時に Calico ネットワークを有効にする必要があります。
  
  - ノード：ICPを構成するノードの状況や詳細情報、および、そのノード上で動作するPodの状況や詳細情報を確認できます。
  ![Node](https://github.com/ICpTrial/ICPTrialJapan/blob/master/pictures/device_node.png)
  
  - ストレージ：クラスター内に構成されるPersistentVolume(PV)、およびアプリケーションがPVを要求するためのPersistentVolumeClaim(PVC)の状況や詳細情報を確認できます。
  ![Storage](https://github.com/ICpTrial/ICPTrialJapan/blob/master/pictures/storage.png)
  
- 管理サービスを使用する
  - アラート：Prometheusなどのモニタリング結果からアラートを外部へ送信するAlertManagerについて、アラート集約や重複排除などのアラート処理や送付先など、設定されている内容を確認できます。
  
  - ロギング：ICPは、管理ロギング・サービスとしてELK Stackが使用されており、すべてのDockerキャプチャー・ログを収集して保管しています。クリックによりKibanaが起動し、ログの検索やグラフ化が可能なユーザー・インタフェースを使用できます。ロギングの詳細は[ロギング](https://github.com/ICpTrial/ICPTrialJapan/blob/master/logging.md)を参照ください。
  ![Kibana](https://github.com/ICpTrial/ICPTrialJapan/blob/master/pictures/kibana.png)
  
  - 計量：アプリケーションおよびクラスターの詳細な使用量メトリックを表示およびダウンロードできます。
  ![Metering](https://github.com/ICpTrial/ICPTrialJapan/blob/master/pictures/metering.png)
  
  - モニタリング：ICPはGrafanaおよびPrometheusを使用して、クラスター・ノードおよびコンテナーに関するモニタリングを行います。Prometheusの詳細はこ[モニタリング](https://github.com/ICpTrial/ICPTrialJapan/blob/master/monitoring.md)を参照ください。   
  ![Prometheus](https://github.com/ICpTrial/ICPTrialJapan/blob/master/pictures/prometheus.png)
  
  - 脆弱性アドバイザー：プライベート・レジストリー内のコンテナー・イメージのセキュリティー状況を取得し、環境内の稼働しているコンテナーに対するセキュリティー検査を実行します。脆弱性アドバイザーの詳細は[脆弱性アドバイザー](https://github.com/ICpTrial/ICPTrialJapan/blob/master/vulnerabilityadvisor.md)を参照ください。

## HELMカタログ

## ワークロード

### デプロイメント

### ステートフルセット

## 
