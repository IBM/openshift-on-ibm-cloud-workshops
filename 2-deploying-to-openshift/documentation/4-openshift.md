# Lab 4 - Deploying to OpenShift


In that lab we will work in the **OpenShift web console** and in the **OpenShift CLI**. The following image is an simplified overview of the topics of that lab. Have in mind, that [OpenShift](https://www.youtube.com/watch?v=5dwMrFxq8sU&feature=youtu.be) is a [Kubernetes](https://www.youtube.com/watch?v=4ht22ReBjno) platform.

![overview](images/lab-4-overview.png)

1. Build and save the container image

  * We will create a OpenShift project
  * We will define a [build config](https://docs.openshift.com/container-platform/3.9/dev_guide/builds/index.html) for OpenShift
  * We will build with the build Pod inside OpenShift and save container image to the internal [OpenShift container registry](https://docs.openshift.com/container-platform/3.9/install_config/registry/index.html#install-config-registry-overview)

2. Apply the yamls and expose the service

  * We will define and apply a deployment configuration to create a Pod with our microservice
  * We will define a service which routes requests to the Pod with our microservice
  * We will expose the service

The following image is a animation of the simplified steps above.

![overview gif](images/lab-4-overview.gif)


# 1. Build and save the container image

## Step 1: Create a Open Shift project

To work inside OpenShift we need a OpenShift project. 
Let us create one.

_Note:_ A [project allows](https://docs.openshift.com/container-platform/3.7/dev_guide/projects.html#overview) a community of users to organize and manage their content in isolation from other communities.

```
$ cd ${ROOT_FOLDER}/2-deploying-to-openshift
$ oc new-project cloud-native-starter
```

**Ensure** you are logged on to your **Open Shift** cluster.
[See details](https://github.com/nheidloff/openshift-on-ibm-cloud-workshops/blob/master/2-deploying-to-openshift/documentation/1-prereqs.md#verify-access-to-openshift-on-the-ibm-cloud)

## Step 2: Build and save the container in the Open Shift Container Registry

Now we want to build and save the container in the **Open Shift Container Registry**. 
We use these command to do that:

1. Defining a new build using binary and the Docker strategy ([more details](https://docs.openshift.com/container-platform/3.5/dev_guide/builds/build_inputs.html#binary-source) and [oc new-build documentation](https://docs.openshift.com/container-platform/3.9/cli_reference/basic_cli_operations.html#new-build))

```
$ oc new-build --name authors --binary --strategy docker
```

2. Starting the build process of OpenShift with our defined build configuration. ([oc start-build documentation](https://docs.openshift.com/container-platform/3.9/cli_reference/basic_cli_operations.html#start-build))

```
$ oc start-build authors --from-dir=.
```

## Step 3: Verify the build in the OpenShift web console


1. Select in **My Projects** the **default** project

  ![Select in My Projects the default project](images/os-registry-04.png)

2. Open **Build** in the menu and click **Build**

  ![Open Build in the menu and click Build](images/os-build-01.png)

3. Select **Last Build** 

  ![Select Last Build ](images/os-build-02.png)

4. Open **Logs** 

  ![Open Logs ](images/os-build-03.png)

5. Inspect the **Logs** 

  ![Inspect the **Logs**  ](images/os-build-04.png)

## Step 4: Verify the container image in the Open Shift Container Registry UI


1. Expand in **Overview** the **DEPLOYMENT registry-console** and click **Routes - External Traffic**

  ![Expand in Overview the DEPLOYMENT registry-console and click Routes - External Traffic](images/os-registry-05.png)

2. In the container registry you will find later the **authors** image and you can click on the latest label.

  ![In the container registry you will find later the authors image](images/os-registry-06.png)

# 2. Apply the deployment.yaml

The deployment will deploy the container to a Pod in Kubernetes.
For more details we use the [Kubernetes documentation](https://kubernetes.io/docs/concepts/workloads/pods/pod-overview/) for Pods.

> A Pod is the basic building block of Kubernetes–the smallest and simplest unit in the Kubernetes object model that you create or deploy. A Pod represents processes running on your Cluster .

Here is a simplified image for that topic. The Pod knows, because of the deployment, where the image is available, he has to instantiate.

![deployment](images/lab-4-deployment.png)

Let's start with the **deployment yaml**. For more details we use will the [Kubernetes documentation](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) for deployments.

Definition of the ```kind``` defines this is a ```Deployment``` configuration.

```yml
kind: Deployment
apiVersion: apps/v1beta1
metadata:
  name: authors
```

Inside the ```spec``` section, we give the deployment a app name and version label.

```yml
spec:
  ...
  template:
    metadata:
      labels:
        app: authors
        version: v1
```

Then we define a ```name``` for the container and we provide the concret container ```image``` location, e.g. where the container can be found in the **Container Registry**. 

The ```containerPort``` depends on the port definition inside our **Dockerfile** or better in our **server.xml**.

Now we should remember the usage of **HealthEndpoint** class for our **Authors**, here we see the ```livenessProbe``` definition.


```yml
spec:
      containers:
      - name: authors
        image: authors:1
        ports:
        - containerPort: 3000
        livenessProbe:
```

This is the full [deployment.yaml](../deployment/deployment.yaml) file.

```yaml
kind: Deployment
apiVersion: apps/v1beta1
metadata:
  name: authors
spec:
  replicas: 1
  template:
    metadata:
      labels:
        app: authors
        version: v1
    spec:
      containers:
      - name: authors
        image: docker-registry.default.svc:5000/cloud-native-starter/authors:latest
        ports:
        - containerPort: 3000
        livenessProbe:
          exec:
            command: ["sh", "-c", "curl -s http://localhost:3000/"]
          initialDelaySeconds: 20
        readinessProbe:
          exec:
            command: ["sh", "-c", "curl -s http://localhost:3000/health | grep -q authors"]
          initialDelaySeconds: 40
      restartPolicy: Always
```

## Step 1: Apply the deployment

1. Ensure you are in the ```{ROOT_FOLDER}/2-deploying-to-openshift/deployment```

  ```
  $ cd ${ROOT_FOLDER}/2-deploying-to-openshift/deployment
  ```

2. Apply the deployment to **OpenShift**

  ```
  $ oc apply -f deployment.yaml
  ```

## Step 2: Verify the deployment in **OpenShift**

1. Logon to **IBM Cloud web console** and open your **OpenShift web console**

2. Select the **Cloud-Native-Starter** project and examine the deployment

  ![Select the Cloud-Native-Starter project and examine the deployment](images/os-deployment-01.png)

3. Click on **#1** to open the details of the deployment

  ![Click on #1 to open the details of the deployment](images/os-deployment-02.png)

4. In the details you find the health check we defined before

  ![In the details you find the health check we defined before](images/os-deployment-03.png)

# 3. Apply the service.yaml

After the definition of the **Pod** we need to define how to access the Pod, therefor we use a **service** in Kubernetes. For more details we use the [Kubernetes documentation](https://kubernetes.io/docs/concepts/services-networking/service/) for service.

> A Kubernetes Service is an abstraction which defines a logical set of Pods and a policy by which to access them - sometimes called a micro-service. The set of Pods targeted by a Service is (usually) determined by a Label Selector.

In the service we map the **NodePort** of the cluster to the port 3000 of the **Authors** service running in the **authors** Pod, as we can see in the following simplified overview picture. 

![service](images/lab-4-service.png)

In the [service.yaml](../deployment/service-os.yaml) we find our selector to the Pod **authors**. If the service is deployed, it is possible that our **Articles** service can find the **Authors** service.

```yaml
kind: Service
apiVersion: v1
metadata:
  name: authors
  labels:
    app: authors
spec:
  selector:
    app: authors
  ports:
    - port: 3000
      name: http
  type: NodePort
---
```

## Step 1: Apply the deployment

1. Apply the service to **OpenShift**

  ```
  $ oc apply -f service.yaml
  ```

2. With oc [expose](https://docs.openshift.com/container-platform/3.6/dev_guide/routes.html) we create a route to our service in the OpenShift cluster. ([oc expose documentation](https://docs.openshift.com/container-platform/3.9/cli_reference/basic_cli_operations.html#expose))

  ```
  $ oc expose svc/authors
  ```

## Step 2: Test the microservice

1. Exeute the command, copy the URL and open the Swagger UI in browser

  ```
  $ echo http://$(oc get route authors -o jsonpath={.spec.host})/openapi/ui/
  $ http://authors-cloud-native-starter.openshift-devadv-eu-wor-160678-0001.us-south.containers.appdomain.cloud/openapi/ui/
  ```

The Swagger UI in your browser:

  ![Swagger UI](images/authors-swagger-ui.png)

1. Exeute the command verify the output

  ```
  $ curl -X GET "http://$(oc get route authors -o jsonpath={.spec.host})/api/v1/getauthor?name=Niklas%20Heidloff" -H "accept: application/json"
  ```

2. Output

  ```
  $ {"name":"Niklas Heidloff","twitter":"https://twitter.com/nheidloff","blog":"http://heidloff.net"}
  ```

## Step 3: Inspect the service in OpenShift

1. Logon to **IBM Cloud web console** and open your **OpenShift web console**

2. Select the **Cloud-Native-Starter** project

  ![Service](images/os-service-01.png)

3. Chose **Application** and then **Services** 

  ![Service](images/os-service-02.png)

4. Click on **Authors**

5. Examine the traffic and remember the simplified overview picture.

  ![Service](images/os-service-03.png)

---

__Continue with [Lab 5 - eploying existing Images from Docker Hub](./5-existing-image.md)__


