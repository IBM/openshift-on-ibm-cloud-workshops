# Lab 2 - Running the Java Microservice locally

In this workshop we'll use a microservice that has been implemented with Java EE and [Eclipse MicroProfile](https://microprofile.io/).

The microservice has been kept as simple as possible, so that it can be used as a starting point for other microservices. It contains the following functionality:

* Image with OpenJ9, OpenJDK, Open Liberty and MicroProfile: [Dockerfile](../../Dockerfile)
* Maven project: [pom.xml](../../pom.xml)
* Open Liberty server configuration: [server.xml](../../liberty/server.xml)
* Health endpoint: [HealthEndpoint.java](../../src/main/java/com/ibm/authors/HealthEndpoint.java)
* Kubernetes yaml files: [deployment.yaml](../../deployment/deployment.yaml) and [service.yaml](../../deployment/service.yaml)
* Sample REST GET endpoint: [AuthorsApplication.java](../../src/main/java/com/ibm/authors/AuthorsApplication.java), [GetAuthor.java](../../src/main/java/com/ibm/authors/GetAuthor.java) and [Author.java](../../src/main/java/com/ibm/authors/Author.java)

Note: If you want to use this code for your own microservice, remove the three Java files for the REST GET endpoint and rename the service in the pom.xml file and the yaml files.

This service provides a REST API 'getauthor'. Normally we would implement also a database access, but in our case, we will only return sample data information. That sounds not a lot, but with this small sample we touch following topics:

•	Usage of [Maven](https://maven.apache.org/) for Java 

•	Configuration of an [OpenLiberty Server](https://openliberty.io)

•	Implementation of a [REST GET endpoint with MicroProfile](https://openliberty.io/blog/2018/01/31/mpRestClient.html)

•	[Health check](https://openliberty.io/guides/kubernetes-microprofile-health.html#adding-a-health-check-to-the-inventory-microservice) implementation using a MicroProfile for Kubernetes 

•	Definition of a [Dockerfile](https://docs.docker.com/engine/reference/builder/) with the reuse for existing containers from the [Dockerhub](https://hub.docker.com)

## Definition of the Image

For the image we use a stack of open source components to run the Java microservice on Open Liberty.

* OpenJ9 0.12.1
* OpenJDK 8u202-b08 from AdoptOpenJDK
* Open Liberty 18.0.0.4
* MicroProfile 2.1

Read the article [How to build and run a Hello World Java Microservice](http://heidloff.net/article/how-to-build-and-run-a-hello-world-java-microservice/) to learn more.

With the [Dockerfile](authors-java-jee/Dockerfile), we define the  how to build a container. For detailed information we use the [Dockerfile documentation](https://docs.docker.com/engine/reference/builder/)

If we build a container, we usually start with an existing container image, which contains a minimum on configuration we need, for example: the OS, the Java version or even more. Therefore we examine [HockerHub](https://hub.docker.com/search?q=maven&type=image&image_filter=official) or we search in the internet, to find a starting point which fits to our needs. 

Inside the Dockerfile we use **two stages** to build the container image. The reason for the two stages is, we have the objective to be **independed** of local environment settings, when we build our production services. With this concept, we don't have to ensure that **Java** and **Maven** (or wrong versions of them) is installed on the local machine of the developers.

In short words one container is only responsible to build the microservice, let us call this container **build environment container** and the other container will contain the microservice, we call this the **production** container.


* **Build environment container**

In the following Dockerfile extract, we can see how we create our **build environment container** based on the maven 3.5 image from the [dockerhub](https://hub.docker.com/_/maven/).

Here we use the **pom** file, we defined before, to build our **Authors service** with ```RUN mvn -f /usr/src/app/pom.xml clean package```.

```dockerfile
FROM maven:3.5-jdk-8 as BUILD
 
COPY src /usr/src/app/src
COPY pom.xml /usr/src/app
RUN mvn -f /usr/src/app/pom.xml clean package
```

* **Production container**

The starting point for the our **Production container** is the [OpenLiberty container](https://hub.docker.com/_/open-liberty).

We copy the **Authors service** code with the **server.xml** for the OpenLiberty server to this container.

_REMEMBER:_ The **service.xml** contains the ports we use for our **Authors service**.

```dockerfile
FROM openliberty/open-liberty:microProfile2-java8-openj9 

COPY liberty/server.xml /config/
COPY --from=BUILD /usr/src/app/target/authors.war /config/apps/
```
---

## Run the Container locally

```
$ cd ${ROOT_FOLDER}/2-deploying-to-openshift
$ mvn package
$ docker build -t authors .
$ docker run -i --rm -p 3000:3000 authors
$ open http://localhost:3000/openapi/ui/
```