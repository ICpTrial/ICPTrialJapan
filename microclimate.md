# Microclimate
## 概要
Microclimateはエンドツーエンドの開発環境です。
マイクロサービスアプリケーションを雛形から生成し，継続的かつ迅速な開発，Kubernetesへの継続的なデプロイを自動化するなどの仕組みを実現する機能です。現在は，Java，Node.js，Swift，Go，Pythonの言語をサポートしています。

## 動作環境
Microclimateは以下の環境でコンテナとして動作します。
- Kubernetes  (IBM Cloud Private)
- ローカル端末  (Mac/Windows)

## Handson
[Microclimate Handson (GitHub)](https://github.com/capsmalt/k8s-handson/tree/master/Microclimate) では，ICP Kubernetes クラスターを使用して以下のことを実施します。

- Lab1) Microclimate ツールを Kubernetes上に構築

- Lab2) マイクロサービスを新規作成して Kubernetes 上にデプロイ


ご参考) ハンズオンで使用するテクノロジー
- Kubernetes: **kubectl CLI**
    - Kubernetes クラスターの簡易操作
- Kubernetes: **Helm**
    - Microclimateの導入
- Application: **Java**
    - jax-rsベースのシンプルなREST API
    - pom.xml (Mavenによる自動ビルド)
    - Dockerfile (Dockerイメージのビルド)
- SCM: **GitHub**
    - アプリケーションおよび各種OSS構成ファイルの管理
    - Webhook
- CI/CD: **Jenkins**
    - K8sクラスターへの自動デプロイ