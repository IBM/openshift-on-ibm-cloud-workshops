# OpenShift on IBM Cloud Workshops

![logo](images/os_logo.png)

Red Hat OpenShift on IBM Cloud is an extension of the IBM Cloud Kubernetes Service, where IBM manages OpenShift Container Platform for you. 

With Red Hat OpenShift on IBM Cloud, developers have a fast and secure way to containerize and deploy enterprise workloads in Kubernetes clusters. OpenShift clusters build on Kubernetes container orchestration that offers consistency and flexibility for your development lifecycle operations.

This repository holds a series of workshops (currently 2) that should help you as a developer to become familiar with Red Hat OpenShift, how it can be deployed on the [IBM Cloud](https://cloud.ibm.com/docs/openshift?topic=openshift-getting-started), and how to deploy applications on and with OpenShift.

### Workshop 1: [Understanding OpenShift - For Developers](https://github.com/nheidloff/openshift-on-ibm-cloud-workshops/tree/master/1-understanding-openshift#understanding-openshift---for-developers)

In this workshop we will show you how to create your own OpenShift cluster on the IBM Cloud, and how to use the `oc`CLI and the OpenShift Web Console to deploy applications.

<kbd><img src="images/os_console.png" /></kbd>


### Workshop 2: [Deploying Java Microservices to OpenShift on IBM Cloud](https://github.com/nheidloff/openshift-on-ibm-cloud-workshops/tree/master/2-deploying-to-openshift#deploying-java-microservices-to-openshift-on-ibm-cloud)

This workshop demonstrates how to build a microservice with Java and how to deploy it to OpenShift on the IBM Cloud.

The microservice is kept as simple as possible, so that it can be used as a starting point for other microservices. The microservice has been developed with Java EE and Eclipse MicroProfile.

<kbd><img src="images/workshop-2.jpg" /></kbd>

> __IMPORTANT: An [IBM Cloud account](https://cloud.ibm.com/registration) is needed for these workshops! A free IBM Cloud Lite account is not sufficient, you cannot create an OpenShift cluster with a lite account.__


## Other Resources

There are many good tutorials on the Red Hat OpenShift [Interactive Learning Portal](https://learn.openshift.com/).

The IBM Developer Website has its own section on [Red Hat OpenShift on IBM Cloud](https://developer.ibm.com/components/redhat-openshift-ibm-cloud/).

Check this IBM Cloud Solution Tutorial: [Scalable web application on OpenShift](https://cloud.ibm.com/docs/tutorials?topic=solution-tutorials-scalable-webapp-openshift).

Our [Cloud Native Starter](https://github.com/IBM/cloud-native-starter) project on GitHub has a section on [how to deploy on OpenShift](https://github.com/IBM/cloud-native-starter/blob/master/documentation/OpenShiftIKSDeployment.md#deploy-cloud-native-starter-on-openshift-on-ibm-cloud).