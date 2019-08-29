

### 2.1 Build the container and upload to the IBM Container Registry

1. Logon to the IBM Cloud Container Registry 

    ```sh
    $ cd authors-java-jee
    $ ibmcloud cr login
    ```

2. List you namespaces inside the IBM Cloud Container Registry 

    ```sh
    $ ibmcloud cr namespaces
    ```

    _Sample result outout:_

    ```sh
    $ Listing namespaces for account 'Thomas Südbröcker's Account' in registry 'de.icr.io'...
    $
    $ Namespace   
    $ cloud-native
    ```

3. Now upload the code and build the container image inside IBM Cloud Container Registry. We use the upper information we got from listing the namespaces.

    ```sh
    $ ibmcloud cr build -f Dockerfile --tag $REGISTRY/$REGISTRY_NAMESPACE/authors:2 .
    ```

    _Sample result values:_

    ```sh
    $ ibmcloud cr build -f Dockerfile --tag de.icr.io/cloud-native/authors:2 .
    ```

    _Optional:_ Verify the container upload in the IBM Cloud web UI.

    ![authors-java-container-image](images/authors-java-container-image.png)

4. List the container images to verify the upload.

    ```sh
    $ ibmcloud cr images
    ```

    _Sample result output:_

    ```sh
    $ REPOSITORY                        TAG   DIGEST         NAMESPACE      CREATED          SIZE     SECURITY STATUS   
    $ de.icr.io/cloud-native/articles   1     b5dc1f96a69a   cloud-native   1 day ago        273 MB   7 Issues   
    $ de.icr.io/cloud-native/authors    2     217b7716dce1   cloud-native   30 seconds ago   259 MB   7 Issues   
    ```

    Copy the REPOSITORY path for the uploaded **Authors** container image.
    In this case sample: ```de.icr.io/cloud-native/authors```

### 2.3 Deploy the container image

1. Open the ```../authors-java-jee/deployment/deployment.yaml```with a editor and replace the value for the image location with the path we got from the IBM Container Registry and just replace the ```authors:1``` text, and add following statement ```imagePullPolicy: Always``` and **save** the file.

    Before:
    ```yml
    image: authors:1
    ```

    Sample change:
    ```yml
    image: de.icr.io/cloud-native/authors:2
    imagePullPolicy: Always
    ```

2. Now we apply the deployment we will create the new **Authors** Pod.

    ```sh
    $ kubectl apply -f deployment/deployment.yaml
    ```

3. Now we apply the service we will create the new **Authors** Service.

    ```sh
    $ kubectl apply -f deployment/service.yaml
    ```

4. Get cluster (node) IP address

    ```sh
    $ clusterip=$(ibmcloud ks workers --cluster cloud-native | awk '/Ready/ {print $2;exit;}')
    $ echo $clusterip
    $ 159.122.172.162
    ```

5. Get nodeport.

    ```sh
    $ nodeport=$(kubectl get svc authors --ignore-not-found --output 'jsonpath={.spec.ports[*].nodePort}')
    $ echo $nodeport
    $ 30108
    ```

5. Open API explorer.

    ```sh
    $ open http://${clusterip}:${nodeport}/openapi/ui/
    ```

    Sample result in your browser:

    ![authors-java-openapi-explorer](images/authors-java-openapi-explorer.png)


6. Execute curl to test the **Authors** service.

    ```sh
    $ curl http://${clusterip}:${nodeport}/api/v1/getauthor?name=Niklas%20Heidloff
    ```

    Sample result:
    ```
    $ {"name":"Niklas Heidloff","twitter":"@nheidloff","blog":"http://heidloff.net"}
    ```

7. Execute following curl command to test the **HealthCheck** implementation for the **Authors** service.

    ```sh
    $ curl http://${clusterip}:${nodeport}/health
    $ {"checks":[{"data":{"authors":"ok"},"name":"authors","state":"UP"}],"outcome":"UP"} 
    ```

    Optional: We can also verify that call in the browser.

    ![authors-java-health](images/authors-java-health.png)

---

Now, we've finished the **Replace the Node.js Authors microservice with a simple Java implementation**.

**Congratulations** :thumbsup: and **greatest respect** :muscle:, you did the **extra mile** and you have finished this **hands-on workshop + optional lab** :-).

---

Resources:

* ['Simplest possible Microservice in Java'](../authors-java-jee/README.md)
* ['How to deploy a container to the IBM Cloud Kubernetes Service](https://suedbroecker.net/2019/03/05/how-to-deploy-a-container-to-the-ibm-cloud-kubernetes-service/)