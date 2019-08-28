# Deploying Java Microservices to OpenShift on IBM Cloud

This workshop demonstrates how to build a microservice with Java and how to deploy it to OpenShift on the IBM Cloud.

The microservice is kept as simple as possible, so that it can be used as a starting point for other microservices. The microservice has been developed with Java EE and Eclipse MicroProfile.

There are [various ways to deploy applications to OpenShift](http://heidloff.net/article/deploying-open-liberty-microservices-openshift/). This workshop explains how to deploy microservices using the OpenShift CLI (command line tool) 'oc' as well as 'binary builds'.


## Prerequisites

An [IBM Cloud account](https://cloud.ibm.com/registration) is needed. We will use the following IBM Cloud service in this hands-on workshop:

* [OpenShift on IBM Cloud](https://cloud.ibm.com/kubernetes/catalog/openshiftcluster)

In order to complete the workshop, you need to install [Docker Desktop](https://docs.docker.com/install/). Docker Desktop is available for Mac and Windows and the Docker Engine can be run natively on Linux.

Several other tools are needed. There are different options to install these tools.

### Tools - Option 1: Prebuilt Image

There is an image on DockerHub with all required tools. This option works for Mac, Linux and Windows. To get started as quickly as possible, use this image.

Run this command in a terminal:

git clone https://github.com/nheidloff/openshift-on-ibm-cloud-workshops.git
$ cd openshift-on-ibm-cloud-workshops

```
$ docker run -ti nheidloff/openshift-workshop-tools:v1
```

When the container has been started, run these commands to get the lastest version of the workshop:

```
$ git clone https://github.com/nheidloff/openshift-on-ibm-cloud-workshops.git
$ cd openshift-on-ibm-cloud-workshops
$ ROOT_FOLDER=$(pwd)
```

### Tools - Option 2: Install Tools on your Notebook

This approach only works for Mac and Linux (see this [article](https://suedbroecker.net/2019/08/27/definition-of-a-dockerfile-to-use-bash-scripts-on-a-windows-10-machine-for-our-cloud-native-starter-workshop/) for more).

Install the following tools:

- [oc](https://cloud.ibm.com/docs/containers?topic=containers-cs_cli_install#cli_oc)
- [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) 
- [curl](https://curl.haxx.se/download.html)
- [IBM Cloud CLI](https://cloud.ibm.com/docs/home/tools)
- [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
- Editor: For example [Visual Studio Code](https://code.visualstudio.com/) 

Get the code:

```
$ git clone https://github.com/nheidloff/openshift-on-ibm-cloud-workshops.git
$ cd openshift-on-ibm-cloud-workshops
$ ROOT_FOLDER=$(pwd)
```



## to be done


Part 1: Intro 5 mins
to be done: existing video with deployment options

Part 2: Simplest possible Java service deployed on OpenShift on IBM Cloud - 85 mins
We need to convert this IKS workshop to OpenShift: https://github.com/IBM/cloud-native-starter/blob/master/workshop/06-java-development.md

Part 3: Other deployment options (if we can finish this on time)
1. source to image
2. existing image from DockerHub


to be done