[日本語はこちら - Japanese version](./README-ja.md)

# OpenShift on IBM Cloud Workshops

![logo](images/os_logo.png)

[Red Hat OpenShift on IBM Cloud](https://cloud.ibm.com/docs/openshift?topic=openshift-why_openshift) is an extension of the IBM Cloud Kubernetes Service, where IBM manages OpenShift Container Platform for you. 

With Red Hat OpenShift on IBM Cloud developers have a fast and secure way to containerize and deploy enterprise workloads in Kubernetes clusters. OpenShift clusters build on Kubernetes container orchestration that offers consistency and flexibility for your development lifecycle operations.

This repository holds a series of workshops that help you as a developer to become familiar with Red Hat OpenShift, how it can be deployed on the IBM Cloud, and how to deploy applications on and with OpenShift.

In order to run these workshops, you need an [IBM Cloud account](https://cloud.ibm.com/registration).

## Workshop 1: [Understanding OpenShift](1-understanding-openshift/README.md#understanding-openshift)

In this workshop we will show you how to create your own OpenShift cluster on the IBM Cloud, how to use the `oc` CLI (command line interface) and how to use the OpenShift Web Console to deploy applications.

* Duration: 60 - 90 minutes
* Audience: Beginner

<kbd><img src="images/workshop-1.png" /></kbd>

**Labs**

0. [Overview video (3:42 mins)](https://youtu.be/cotKSI-S1Ng)
1. Introduction: [video (2:04 mins)](https://www.youtube.com/watch?v=hdwDMsDF9J8) and [video (5:45 mins)](https://www.youtube.com/watch?v=l4Vrj7mkxhQ)
2. Create an OpenShift cluster on the IBM Cloud: [lab](1-understanding-openshift/Part2.md) and [video (3:17 mins)](https://youtu.be/9xgqDP2B3WI)
3. Getting started with OpenShift for developers: [lab](https://learn.openshift.com/introduction/getting-started/) and [video (12:38 mins)](https://www.youtube.com/watch?v=boJOI0DgSTc&list=PL0Mrq9ES4ERfGpB0K5PHYmvl2xV60GSQz&index=4&t=0s)
4. Deploying applications from images: [lab](https://learn.openshift.com/introduction/deploying-images/) and [video (9:00 mins)](https://www.youtube.com/watch?v=v_j3TiurPQc&list=PL0Mrq9ES4ERfGpB0K5PHYmvl2xV60GSQz&index=5&t=0s)
5. Deploying applications from source: [lab](https://learn.openshift.com/introduction/deploying-python/) and [video (10:28 mins)](https://www.youtube.com/watch?v=2CtThlhgOYs&list=PL0Mrq9ES4ERfGpB0K5PHYmvl2xV60GSQz&index=6&t=0s)
6. Deploy an application on OpenShift on the IBM Cloud: [lab](1-understanding-openshift/Part4.md) and [video (14:20 mins)](https://www.youtube.com/watch?v=7XBbuPjsUqU&list=PL0Mrq9ES4ERfGpB0K5PHYmvl2xV60GSQz&index=7&t=0s)

---

## Workshop 2: [Deploying Java Microservices to OpenShift on IBM Cloud](https://github.com/nheidloff/openshift-on-ibm-cloud-workshops/tree/master/2-deploying-to-openshift#deploying-java-microservices-to-openshift-on-ibm-cloud)

This workshop demonstrates how to build a microservice with Java and how to deploy it to OpenShift on the IBM Cloud.

The microservice is kept as simple as possible, so that it can be used as a starting point for other microservices. The microservice has been developed with Java EE and Eclipse MicroProfile.

* Duration: 60 - 90 minutes
* Audience: Intermediate

<kbd><img src="images/workshop-2.png" /></kbd>

**Labs**

0. [Overview video (1:41 mins)](https://youtu.be/8361HGR_O_s)
1. Installing prerequisites: [lab](2-deploying-to-openshift/documentation/1-prereqs.md) and [video (2:58 mins)](https://youtu.be/c5CtqijWXL4) and the [video including windows (4:11 mins)](https://youtu.be/53XccO3NNn8)
2. Running the Java microservice locally: [lab](2-deploying-to-openshift/documentation/2-docker.md) and [video (3:51 mins)](https://youtu.be/4dT2jg6wGF4)
3. Understanding the Java implementation: [lab](2-deploying-to-openshift/documentation/3-java.md) and [video (9:09 mins)](https://www.youtube.com/watch?v=ugpYSPV9jAs)
4. Deploying to OpenShift via 'oc' CLI: [lab](2-deploying-to-openshift/documentation/4-openshift.md) and [video (14:32 mins)](https://youtu.be/4MDfalo2Fg0)
5. Deploying existing images to OpenShift: [lab](2-deploying-to-openshift/documentation/5-existing-image.md) and [video (7:09 mins)](https://youtu.be/JhxsS7l6DhA)
6. Deployments of code in GitHub repos: [lab](2-deploying-to-openshift/documentation/6-github.md) and [video (3:52 mins)](https://youtu.be/b3upMuZOpsY)
7. Source to Image deployments: [lab](2-deploying-to-openshift/documentation/7-source-to-image.md) and [video (7:06 mins)](https://youtu.be/p6lVc6MDrcM)

---

## Resources and next Steps

* There are many good tutorials on the Red Hat OpenShift [Interactive Learning Portal](https://learn.openshift.com/).

* The IBM Developer Website has its own section on [Red Hat OpenShift on IBM Cloud](https://developer.ibm.com/components/redhat-openshift-ibm-cloud/).

* Our [Cloud Native Starter](https://github.com/IBM/cloud-native-starter) project on GitHub has a section on [how to deploy on OpenShift](https://github.com/IBM/cloud-native-starter/blob/master/documentation/OpenShiftIKSDeployment.md#deploy-cloud-native-starter-on-openshift-on-ibm-cloud).

* Check this IBM Cloud solution tutorial: [Scalable web application on OpenShift](https://cloud.ibm.com/docs/tutorials?topic=solution-tutorials-scalable-webapp-openshift).

