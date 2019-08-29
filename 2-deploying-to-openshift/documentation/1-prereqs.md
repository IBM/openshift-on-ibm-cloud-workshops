# Lab 1 - Install Prerequisites

## Access to the IBM Cloud

An [IBM Cloud account](https://cloud.ibm.com/registration) is needed. 

Note: In order to run this workshop an IBM Cloud Lite account is not sufficient. This tutorial may incur costs. Use the [Pricing Calculator](https://cloud.ibm.com/estimator/review) to generate a cost estimate based on your projected usage.

We will use the following IBM Cloud service in this hands-on workshop:

* [OpenShift on IBM Cloud](https://cloud.ibm.com/kubernetes/catalog/openshiftcluster)

Follow the [instructions](../../1-understanding-openshift#part-2-create-cluster-on-the-ibm-cloud) from the first workshop to set up an OpenShift cluster.

## Tools

In order to complete the workshop, you need to install [Docker Desktop](https://docs.docker.com/install/). Docker Desktop is available for Mac and Windows and the Docker Engine can be run natively on Linux.

Several other tools are needed. There are different options to install these tools.

### Tools - Option 1: Prebuilt Image with Code in Container

There is an image on DockerHub with all required tools. This option works for Mac, Linux and Windows. To get started as quickly as possible, use this image.

Run this command in a terminal:

```
$ docker run -ti nheidloff/openshift-workshop-tools:v1
```

After the container has been started, run these commands in the container to get the lastest version of the workshop:

```
$ git clone https://github.com/nheidloff/openshift-on-ibm-cloud-workshops.git
$ cd openshift-on-ibm-cloud-workshops
$ ROOT_FOLDER=$(pwd)
```

_Note:_ For the docker and java lab you also need to download or clone the project on your local PC.

### Tools - Option 2: Prebuilt Image with local Code

In order to use local IDEs and editors to modify code and configuraton files, Docker volumes can be used. This option  works only for Mac and Linux.

Run these commands in a terminal:

```
$ git clone https://github.com/nheidloff/openshift-on-ibm-cloud-workshops.git
$ cd openshift-on-ibm-cloud-workshops
$ ROOT_FOLDER=$(pwd)
$ docker run -v $ROOT_FOLDER/:/cloud-native-starter -it --rm nheidloff/openshift-workshop-tools:v1
```

### Tools - Option 3: Install Tools on your Notebook

This approach works only for Mac and Linux (see this [article](https://suedbroecker.net/2019/08/27/definition-of-a-dockerfile-to-use-bash-scripts-on-a-windows-10-machine-for-our-cloud-native-starter-workshop/) for more).

Install the following tools:

- [oc](https://cloud.ibm.com/docs/containers?topic=containers-cs_cli_install#cli_oc)
- [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
- [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) 
- [curl](https://curl.haxx.se/download.html)
- Optional: [IBM Cloud CLI](https://cloud.ibm.com/docs/home/tools)
- Optional: Editor, for example [Visual Studio Code](https://code.visualstudio.com/) 

Get the code:

```
$ git clone https://github.com/nheidloff/openshift-on-ibm-cloud-workshops.git
$ cd openshift-on-ibm-cloud-workshops
$ ROOT_FOLDER=$(pwd)
```

## Verify Access to OpenShift on the IBM Cloud

After you've created a new cluster, open the OpenShift console. From the dropdown menu in the upper right of the page, click 'Copy Login Command'. Paste the copied command in your terminal.

1. Verify 'oc' CLI

```
$ oc login https://c1-e.us-east.containers.cloud.ibm.com:23967 --token=xxxxxx'
$ oc get istag
```

2. Verify 'kubectl' CLI

```
$ kubectl get pods
```
