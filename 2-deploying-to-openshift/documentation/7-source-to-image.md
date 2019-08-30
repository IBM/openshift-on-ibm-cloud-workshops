# Lab 7 - Source to Image Deployments

=============================================

# UNDER CONSTRUCTION

=============================================


OpenShift allows developers to deploy applications without having to understand Docker and Kubernetes in depth. Similarily to the Cloud Foundry 'cf push' experience, developers can deploy applications easily via terminal commands and without having to build Docker images. In order to do this [Source-to-Image](https://github.com/openshift/source-to-image) is used.

Source-to-Image (S2I) is a toolkit for building reproducible container images from source code. S2I produces ready-to-run images by injecting source code into a container image.

In order to use S2I, builder images are needed. These builder images create the actual images with the applications. The builder images are similar to Cloud Foundry buildpacks.

## Deployment of the Open Liberty Builder Image

OpenShift provides several builder images out of the box, for example for Node.js and Wildfly applications. In order to support other runtimes, for example Open Liberty, custom builder images can be built and deployed. Since this workshop uses Open Liberty, we will use a [builder image for Open Liberty](https://github.com/nheidloff/s2i-open-liberty) which needs to be deployed before the actual Open Liberty microservice can be deployed.

In a terminal invoke the following commands to deploy the builder image. Make sure Docker is running on your desktop.

```
$ oc login https://c1-e.us-east.containers.cloud.ibm.com:23967 --token=xxxxxx
$ cd ${ROOT_FOLDER}/2-deploying-to-openshift
$ oc new-project no-docker-and-yaml-files
$ docker login -u developer -p $(oc whoami -t) $(minishift openshift registry)
$ docker pull nheidloff/s2i-open-liberty:latest 
$ docker tag nheidloff/s2i-open-liberty:latest docker-registry.default.svc:5000/no-docker-and-yaml-files/s2i-open-liberty:latest
$ docker push docker-registry.default.svc:5000/no-docker-and-yaml-files/s2i-open-liberty:latest
```

## Deployment of the Microservice

```
$ cd ${ROOT_FOLDER}/sample
$ mvn package
$ cp liberty/server.xml server.xml
$ oc new-app s2i-open-liberty:latest~/. --name=authors
$ oc start-build --from-dir . authors 
$ oc expose svc/authors
$ open http://authors-cloud-native-starter.$(minishift ip).nip.io/openapi/ui/
$ curl -X GET "http://authors-cloud-native-starter.$(minishift ip).nip.io/api/v1/getauthor?name=Niklas%20Heidloff" -H "accept: application/json"
```

**File Structure**

To use “s2i” or “oc new-app/oc start-build” you need to build the application with Maven. The server configuration file and the war file need to be in these directories:

server.xml in the root directory
*.war file in the target directory

