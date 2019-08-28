# Deploying Java Microservices to OpenShift on IBM Cloud

This workshop demonstrates how to build a microservice with Java and how to deploy it to OpenShift on the IBM Cloud.

The microservice is kept as simple as possible, so that it can be used as a starting point for other microservices. The microservice has been developed with Java EE and Eclipse MicroProfile.

There are [various ways to deploy applications to OpenShift](http://heidloff.net/article/deploying-open-liberty-microservices-openshift/). This workshop explains how to deploy microservices using the OpenShift CLI (command line tool) 'oc' as well as 'binary builds'.




## Prerequisites

## 1. IBM Cloud Services

We will use the following IBM Cloud service in this hands-on workshop:

* [OpenShift on IBM Cloud](https://cloud.ibm.com/kubernetes/catalog/openshiftcluster)


## 2. Tools on your laptop

In order to complete the workshop, you will need the following tools installed on your laptop:

- IDE or Editor: [Visual Studio Code](https://code.visualstudio.com/) for example 
- [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) 
- [curl](https://curl.haxx.se/download.html)
- [IBM Cloud CLI](https://cloud.ibm.com/docs/home/tools)
- [Docker](https://docs.docker.com/v17.12/install/)
- [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)


### 2.1 Options for Windows

For Windows, you will need access to a Unix shell because you will execute predefined bash scripts and other CLI commands. 

You have different options:

1. [Use a workshop Docker image for Window 10](00-prerequisites-windows-10.md)
    
    We tested this option on a Windows 10 machine and documented it.

2. [Windows Subsystem for Linux Installation Guide for Windows 10](https://docs.microsoft.com/en-us/windows/wsl/install-win10)

3. IBM Docker image

    There is a Docker image provided by IBM that contains most of the CLI tools needed
    
    * [Using IBM Cloud Developer Tools from a Docker Container](https://cloud.ibm.com/docs/cli?topic=cloud-cli-using-idt-from-docker). 
    
    _Note:_ You need to share the downloaded GitHub repo on your Windows filesystem with the running Docker image.

4. Virtual Box

    You can also use [VirtualBox](https://www.virtualbox.org) or [Hyper-V](https://docs.microsoft.com/de-de/virtualization/hyper-v-on-windows/about/) to create an [Ubuntu](https://www.osboxes.org/ubuntu/) VM and run the workshop directly in the VM in a Linux environment.





## to be done


Part 1: Intro 5 mins
to be done: existing video with deployment options

Part 2: Simplest possible Java service deployed on OpenShift on IBM Cloud - 85 mins
We need to convert this IKS workshop to OpenShift: https://github.com/IBM/cloud-native-starter/blob/master/workshop/06-java-development.md

Part 3: Other deployment options (if we can finish this on time)
1. source to image
2. existing image from DockerHub


to be done