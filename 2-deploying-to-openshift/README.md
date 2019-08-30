# Deploying Java Microservices to OpenShift on IBM Cloud

This workshop demonstrates how to build a microservice with Java and how to deploy it to OpenShift on the IBM Cloud.

The microservice is kept as simple as possible, so that it can be used as a starting point for other microservices. The microservice has been developed with Java EE and [Eclipse MicroProfile](https://microprofile.io/).

There are [various ways to deploy applications to OpenShift](http://heidloff.net/article/deploying-open-liberty-microservices-openshift/). The options have different advantages and disadvantages which are explained in the following labs.

## Labs

This workshop has four labs. It should take between 60 and 90 minutues to complete the workshop.

1. [Installing prerequisites](documentation/1-prereqs.md)
2. [Running the Java microservice locally](documentation/2-docker.md)
3. [Understanding the Java implementation](documentation/3-java.md)
4. [Deploying to OpenShift via 'oc' CLI](documentation/4-openshift.md)
5. [Deploying existing Images to OpenShift](documentation/5-existing-image.md)
6. [Deployments of Code in GitHub Repos](documentation/6-github.md)
7. [Source to Image Deployments](documentation/7-source-to-image.md)