[See this in English](./README.md)

## Part 3: Red Hatチュートリアル 

OpenShiftクラスターの準備が整うまで待機している時間を使用します。 Red Hat OpenShift [Interactive Learning Portal](https://learn.openshift.com/) には非常に優れた資料がたくさんあります。 これらのチュートリアルでは、実際のOpenShiftシステムにアクセスできます。

1）[OpenShift for Developers入門](https://learn.openshift.com/introduction/getting-started/) ：
このチュートリアルでは、基本を学習します。
    * OpenShiftプラットフォームとラーニングポータル環境の基本（Katacoda）
    * `oc`CLIとWebコンソールを使用する
    * プロジェクトとは何か？ OpenShiftでプロジェクトを作成する
    * Dockerイメージからアプリをデプロイする
    * アプリのスケーリング、自己修復
    * ルートとは何か？ ルートを作成する
    * Source-to-Imageを使用してアプリを作成する


2）[イメージからのアプリケーションのデプロイ](https://learn.openshift.com/introduction/deploying-images/) ：
このチュートリアルでは、既存のイメージ（Docker Hubから）からアプリケーションをデプロイする方法と、開発者がYAMLファイルに触れることなくOpenShiftがKubernetesにデプロイメントを作成する方法について説明します。これには以下が含まれます。

    * プロジェクトの作成
    * WebコンソールからDockerイメージをデプロイする
    * 外部ルートを作成する
    * ラベルを使用してコマンドラインからアプリケーション（すべて）を削除する
    * コマンドラインからDockerイメージをデプロイする
    * アプリケーションイメージをインポートし、イメージストリームを操作する


3) [Deploying Applications From Source](https://learn.openshift.com/introduction/deploying-python/):
This tutorial uses a code repository on Github that holds a Python application. The Source-to-Image builder uses a Python template from the OpenShift catalog to create a Container image within OpenShift and deploys it, again without the developer touching any YAML files. Another method, binary build, creates the image from code on the developers workstation. These are the topics of this tutorial:  
   * Create a Project
   * Source-to-Image (S2I) of a Python project in Github
   * Builder Logs
   * Accessing the application
   * Deleting the application via CLI
   * S2I via `oc`command line, differences to Web Console
   * Triggering a new build
   * Binary build from a local code repository
   
3）[ソースからのアプリケーションのデプロイ](https://learn.openshift.com/introduction/deploying-python/) ：
このチュートリアルでは、PythonアプリケーションのGithubのコードリポジトリを使用します。 Source-to-Imageビルダーは、OpenShiftカタログのPythonテンプレートを使用してOpenShift内にコンテナーイメージを作成し、展開します。これも、開発者がYAMLファイルに触れることはありません。 別の方法であるバイナリビルドは、開発者ワークステーションのコードからイメージを作成します。 これらはこのチュートリアルのトピックです：
    * プロジェクトを作成する
    * GithubのPythonプロジェクトのソースからイメージ（S2I）
    * ビルダーログ
    * アプリケーションへのアクセス
    * CLIを介したアプリケーションの削除
    * `oc`コマンドライン経由のS2I、Webコンソールとの違い
    * 新しいビルドのトリガー
    * ローカルコードリポジトリからのバイナリビルド


__次のワークショップ [Part 4: アプリケーションをIBM Cloud上のOpenShiftへデプロイする](./Part4-ja.md#part-4-deploy-an-application-on-openshift-on-the-ibm-cloud)__
