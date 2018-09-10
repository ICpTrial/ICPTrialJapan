
# デプロイメントの挙動確認

実際に Node.js のサンプル・アプリケーションを用いて、HELMカタログから払い出し挙動を確認していきましょう

## Node.js サンプルの払い出し

1. コンソール左上にあるメニューから、「カタログ」を選択します。
Helmで定義された様々なIBMミドルウェア・ソリューションや、OSSのソリューションがカタログに登録されています。
デフォルトで表示されているものはIBMのHELMコンテンツ・カタログです。コンテンツ・カタログは進化し続けており、WatsonやBlockChainなど多様なソリューションが含まれるように進化していきます。
* [参考] コンソール > プラットフォーム > Helmレポジトリを開き、[Google社のHelmレポジトリ](https://kubernetes-charts.storage.googleapis.com)を追加すれば、Google社が提供している多様なOSSのHELMコンテンツも利用できるようになります。同様に他社のHELMレポジトリを追加すれば、その会社のソリューションが利用可能になります。これがオープンなテクノロジーで製品が実装されていることのメリットです（ライセンスはそれぞれの製品/コンポーネントごとにご確認ください）。
1. カタログページの検索ビューに nodejs と入力し、絞り込まれた *ibm-nodejs-sample* をクリックして開きます。
![Catalog](https://github.com/ICpTrial/ICPTrialJapan/blob/master/pictures/catalog-nodejs.png)
1. ibm-nodejs-sample の helm の 説明を確認します（ helmチャートのReadMeがこちらに表示されています ）
この ReadMe には、HELMによって払い出されるソリューションの説明（今回はNode.jsランタイム）や、その利用方法、設定パラメータの解説などが記載されています。ページをおおまかにどんなことが記載されているか確認してみましょう。
![Nodejs-ReadMe](https://github.com/ICpTrial/ICPTrialJapan/blob/master/pictures/nodejsreadme.png)
1. それでは、実際に Node.js のサンプルを払い出してみましょう。ページの一番したにある「構成」のボタンをクリックします。
1. HELMの中で values.yaml として、デプロイ時に変更できる変数として定義されている内容が、このページで設定できます。
HELMには 各ソリューション提供者が決めたデフォルト値が設定されているはずですので、すべての値を１つ１つ変えていく必要はなく、原則としてデフォルト値をそのまま利用することが可能です。
ここでは、払い出す HELMインスタンスの名前と、払い出し先 Namespace、ライセンス条項への 同意のみを設定します。その他の値はそのまま「インストール」をクリックします。

|変数名|設定値|
|:---:|:----|
|リリース名|任意の名前 （下図では nodejsdemo）|
|ターゲット名前空間|任意のNamespace （下図では defautl）|
|使用条件への同意|ライセンス条項を確認して チェックを入れてください|

![NodejsDeploy](https://github.com/ICpTrial/ICPTrialJapan/blob/master/pictures/nodejsdeploy.png)
1. インストールが始まりますので、以下の画面が表示されたら「Helmリリースの表示」をクリックし、Helmインスタンスの確認をしましょう。
![NodejsDeploy](https://github.com/ICpTrial/ICPTrialJapan/blob/master/pictures/nodejs-helmrelease.png)

## 払い出された Node.jsアプリケーション へのアクセス

1. HElMインスタンスのページが開きますので、払い出された環境を確認してみます。なお、コンソールのメニューから ワークロード > Helmリリース　のページを開き、HELMインスタンス名を選択することでも、このページを表示できます。
![HelmInstance](https://github.com/ICpTrial/ICPTrialJapan/blob/master/pictures/nodejshelminstance.png)
1. このHELMで払い出されたNode.jsでは、「デプロイメント」が１種類定義されており、必要インスタンス数が１です。そして使用可能（実際に動いているインスタンスの数）が１であることを確認します。必要インスタンス数と使用可能が一致していれば、すべて正常に稼働していることになります。
１．また「サービス」にはこのインスタンスを外部に公開する仕組みが定義されています。ここでは *NodePort* という方法で、コンテナの3000番ポートが、30162番ポートで外部にむけて公開されていることが分かります。*クラスターIP* は、Kubernetes内部でこのインスタンスにアクセスする際のIPアドレスです。
1. 下の メモ には、このインスタンスにアクセスする方法が記載されています。
1. ここでは、右上にある「起動」をクリックして、インスタンスにアクセスしてみます。以下の画面が表示されれば成功です。この際にアクセスしているブラウザのポートを確認してみてください。
![NodejsSample](https://github.com/ICpTrial/ICPTrialJapan/blob/master/pictures/nodejssample.png)

## スケールアウト
1. この１つだけで稼働する Node.js のインスタンスを スケールアウトしてみましょう。まずこのhelmインスタンスのページで、このインスタンスの「デプロイメント」の名前を確認してください。この図の環境では「nodejsdemo-ibm-nodejs-sa」です（お客様によって値が異なります）。
1. コンソールのメニューから　ワークロード > デプロイメント を開きます。確認したデプロイメント名で検索をかけてください。
![NodejsDeployemnt](https://github.com/ICpTrial/ICPTrialJapan/blob/master/pictures/nodejsdeployment.png)
1. インスタンスの 右にある「アクション」から「スケール」を選択し、インスタンス数を「３」に設定し、「デプロイメントのスケーリング」をクリックします。
![NodejsScaling](https://github.com/ICpTrial/ICPTrialJapan/blob/master/pictures/nodejsscaling.png)
1. デプロイメントの「必要数」が「３」に更新され、数十秒程度で「使用可能」なインスタンス数も「３」に増加していきます。
この増加したデプロイメント・インスタンスへの負荷分散は、Kubernetesで自動的に実施されるようになります。
![NodejsScaled](https://github.com/ICpTrial/ICPTrialJapan/blob/master/pictures/nodejsscaled.png)

## 自動リカバリー
1. 現在、デプロイメントのインスタンス数「３」での負荷分散構成になっています。この運用ポリシーを保つように Kubernetesが自動的に稼働していることを確認していきます。デプロイメントのインスタンス名をクリックして、デプロイメントの詳細ページを開きましょう。
1. デプロイメントの詳細ページの下方に、このデプロイメントに含まれる３つポッドのエントリーがあります。
現在はもともと動いていた古い１インスタンスと、先程増えた２インスタンスの計３つで稼働しています。
１つのコンテナに障害が発生したことを想定し、どれでもいいので１つ ポッドのインスタンスを削除してみます。
![NodejsPodInstance](https://github.com/ICpTrial/ICPTrialJapan/blob/master/pictures/nodejsha.png)
1. インスタンスが１つ削除され消えますが、即座に別のインスタンスが復旧し、当初の「３」インスタンスでの構成を守るように自動復旧してきます。
![NodejsRecovery](https://github.com/ICpTrial/ICPTrialJapan/blob/master/pictures/nodejsrecovery.png)
