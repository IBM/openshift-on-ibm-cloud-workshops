[See this in English](./README.md)

# IBM CloudでJavaマイクロサービスをOpenShiftにデプロイする

このワークショップでは、Javaを使用してマイクロサービスを構築する方法と、IBMクラウドのOpenShiftにデプロイする方法を示します。

マイクロサービスは可能な限りシンプルに保たれるため、他のマイクロサービスの開始点として使用できます。 マイクロサービスは、Java EEおよび [Eclipse MicroProfile](https://microprofile.io/) を使用して開発されました。

[アプリケーションをOpenShiftにデプロイするさまざまな方法](http://heidloff.net/article/deploying-open-liberty-microservices-openshift/)があります。 オプションにはさまざまな長所と短所があり、以下のラボで説明します。

## Labs

このワークショップは7つのLabです。 ワークショップを完了するには、60〜90分かかります。

0. 概要: [動画 (1:41 mins)](https://youtu.be/8361HGR_O_s)
1. 前提条件: [lab](documentation/1-prereqs.md) and [動画 (2:58 mins)](https://youtu.be/c5CtqijWXL4) and[Windowsを含む動画](https://youtu.be/53XccO3NNn8)
2. オプション：Javaマイクロサービスをローカルで実行する: [lab](documentation/2-docker.md) and [動画 (3:51 mins)](https://youtu.be/4dT2jg6wGF4)
3. オプション：Javaの実装を理解する: [lab](documentation/3-java.md) and [動画 (9:09 mins)](https://www.youtube.com/watch?v=ugpYSPV9jAs)
4. 'oc' CLIを使ってOpenShiftへデプロイする: [lab](documentation/4-openshift.md) and [動画 (14:32 mins)](https://youtu.be/4MDfalo2Fg0)
5. 既存イメージファイルをOpenShiftへデプロイする: [lab](documentation/5-existing-image.md) and [動画 (7:09 mins)](https://youtu.be/JhxsS7l6DhA)
6. GitHubリポジトリのコードからのデプロイ: [lab](documentation/6-github.md) and [動画 (3:52 mins)](https://youtu.be/b3upMuZOpsY)
7. ソースからイメージファイルへのデプロイ: [lab](documentation/7-source-to-image.md) and [動画 (7:06 mins)](https://youtu.be/p6lVc6MDrcM)
8. LogDNAを使ったOpenShift on IBM Cloudでの分散ロギング: [lab](documentation/8-logdna-openshift.md)

最初のラボでは、必要なすべての前提条件をインストールする方法について説明します。 最も簡単なケースではDocker Desktopと他のすべてのツールを備えたイメージのみです。

Lab2と3では、Java EEとEclipse MicroProfileを使用してマイクロサービスを開発する方法について説明します。

最後の4つのラボでは、この特定のシナリオの長所と短所を使用して、アプリケーションをOpenShiftにデプロイする4つの異なる方法を説明します。

| Option | Dockerfile | yaml Files | Java Build | Docker Build |
| - | - | - | - | - |
| Lab 4: Kubernetes-like | required | required | OpenShift | OpenShift |
| Lab 5: Existing Image  | not required  | not required | N/A | N/A |
| Lab 6: Git Repo | required  | not required | OpenShift | OpenShift |
| Lab 7: Source to Image | not required | not required | Desktop | OpenShift |
