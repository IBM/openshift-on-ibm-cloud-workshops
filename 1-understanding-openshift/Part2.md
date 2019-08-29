## Part 2: Create an OpenShift cluster on the IBM Cloud

To create your own OpenShift Cluster on IBM Cloud follow these steps. 

__Note:__ This is not available with an IBM Cloud Lite Account!

1. Log on to the IBM Cloud, go to the Catalog, open the category "Containers" and select "Red Hat OpenShift Cluster"

![OS Catalog](images/os_cloud_catalog.png)

2. In the next dialog simply click "Create"

3. Fill out the form with
   * a name (1)
   * a region (2) like North America or Central Europe
   * single zone is perfect for this workshop (3)
   * a datacenter of your choice (4)

![OS Create 1g](images/os_create_cluster1.png)

4. Continue with the form:
    * "Public endpoint only" will do (1)
    * Machine type: Virtual - shared (2)
    * and the smallest flavor (3)

![OS Create 1g](images/os_create_cluster2.png)   

5. Finish:
   * Reduce the number of nodes to 1 (1)
   * Click "Create Cluster" (2)

![OS Create 1g](images/os_create_cluster3.png)  

The creation of the cluster takes at least 20 minutes, __during this time continue with Part 3 of this workshop doing some hands-on exercises.__


__Continue with [Part 3: Red Hat tutorials](Part3.md)__
