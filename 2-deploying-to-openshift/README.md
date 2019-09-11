# Deploying Java Microservices to OpenShift on IBM Cloud

This workshop demonstrates how to build a microservice with Java and how to deploy it to OpenShift on the IBM Cloud.

The microservice is kept as simple as possible, so that it can be used as a starting point for other microservices. The microservice has been developed with Java EE and [Eclipse MicroProfile](https://microprofile.io/).

There are [various ways to deploy applications to OpenShift](http://heidloff.net/article/deploying-open-liberty-microservices-openshift/). The options have different advantages and disadvantages which are explained in the following labs.

## Labs

This workshop has seven labs. It should take between 60 and 90 minutues to complete the workshop.

0. [Overview video (1:41 mins)](https://youtu.be/8361HGR_O_s)
1. Installing prerequisites: [lab](documentation/1-prereqs.md) and [video (2:58 mins)](https://youtu.be/c5CtqijWXL4)
2. Running the Java microservice locally: [lab](documentation/2-docker.md) and [video (3:51 mins)](https://youtu.be/4dT2jg6wGF4)
3. Understanding the Java implementation: [lab](documentation/3-java.md) and [video (9:09 mins)](https://www.youtube.com/watch?v=ugpYSPV9jAs)
4. Deploying to OpenShift via 'oc' CLI: [lab](documentation/4-openshift.md) and [video (14:32 mins)](https://youtu.be/4MDfalo2Fg0)
5. Deploying existing images to OpenShift: [lab](documentation/5-existing-image.md) and [video (7:09 mins)](https://youtu.be/JhxsS7l6DhA)
6. Deployments of code in GitHub repos: [lab](documentation/6-github.md) and [video (3:52 mins)](https://youtu.be/b3upMuZOpsY)
7. Source to Image deployments: [lab](documentation/7-source-to-image.md) and [video (7:06 mins)](https://youtu.be/p6lVc6MDrcM)

The first lab describes how to install all required prerequisites. In the easiest case this is only Docker Desktop and an image with all other tools.

Lab 2 and 3 describe how to develop a microservice with Java EE and Eclipse MicroProfile.

The last four labs explain four different ways to deploy applications to OpenShift with their pros and cons in this specific scenario:

| Option | Dockerfile | yaml Files | Java Build | Docker Build |
| - | - | - | - | - |
| Lab 4: Kubernetes-like | required | required | OpenShift | OpenShift |
| Lab 5: Existing Image  | not required  | not required | N/A | N/A |
| Lab 6: Git Repo | required  | not required | OpenShift | OpenShift |
| Lab 7: Source to Image | not required | not required | Desktop | OpenShift |
