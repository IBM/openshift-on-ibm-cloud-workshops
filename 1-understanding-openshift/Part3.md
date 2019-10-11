[日本語はこちら - Japanese version](./Part3-ja.md)


## Part 3: Red Hat tutorials 

We will use the time while you are waiting for your OpenShift cluster to get ready. There is a lot of really good material at the Red Hat OpenShift [Interactive Learning Portal](https://learn.openshift.com/). You get access to a real OpenShift system during these tutorials.

1) [Getting Started with OpenShift for Developers](https://learn.openshift.com/introduction/getting-started/):
In this tutorial you will learn the fundamentals:
   * Basics of the OpenShift platform and the Learning Portal environment (Katacoda)
   * Using the `oc`CLI and the Web Console
   * What is a project? Creating a project in OpenShift
   * Deploying an app from a Docker image
   * Scaling an app, self-healing
   * What is a Route? Creating a Route
   * Using Source-to-Image to create an app


2) [Deploying Applications From Images](https://learn.openshift.com/introduction/deploying-images/):
This tutorial is about deploying an application from an existing image (from Docker Hub) and how OpenShift creates a deployment on Kubernetes without the developer touching any YAML files. It includes:

   * Creating a Project
   * Deploy a Docker image from the Web Console
   * Create an external Route
   * Delete an application (everything) from the command line using labels
   * Deploy a Docker image from the command line
   * Import an application image, work with image streams


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


__Continue with [Part 4: Deploy an application on OpenShift on the IBM Cloud](https://github.com/nheidloff/openshift-on-ibm-cloud-workshops/blob/master/1-understanding-openshift/Part4.md#part-4-deploy-an-application-on-openshift-on-the-ibm-cloud)__
