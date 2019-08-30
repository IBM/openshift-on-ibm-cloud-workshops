# Lab 6 - Deployments of Code in GitHub Repos

=============================================

# UNDER CONSTRUCTION

=============================================

```
$ oc login -u developer -p developer
$ oc new-project server-side-build
$ oc new-app https://github.com/nheidloff/cloud-native-starter --context-dir=authors-java-jee
$ oc expose svc/server-side-build
$ curl -X GET "http://cloud-native-starter-server-side-build.$(minishift ip).nip.io/api/v1/getauthor?name=Niklas%20Heidloff" -H "accept: application/json"
```