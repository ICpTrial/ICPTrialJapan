
# デプロイメントの挙動確認

実際に Node.js のサンプル・アプリケーションを用いて、HELMカタログから払い出し挙動を確認していきましょう

## Node.js サンプルの払い出し

1. コンソール左上にあるメニューから、「カタログ」を選択します。
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

## 自動リカバリー

