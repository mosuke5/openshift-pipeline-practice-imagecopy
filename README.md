
```
oc new-project platform-operation
oc new-project user1-application

git clone xxxx


oc create sa imagecopy-job
serviceaccount/imagecopy-job created

oc get secret | grep imagecopy
imagecopy-job-dockercfg-45899   kubernetes.io/dockercfg               1      13s
imagecopy-job-token-gwzkq       kubernetes.io/service-account-token   4      13s
imagecopy-job-token-swfg7       kubernetes.io/service-account-token   4      13s

secret

oc policy add-role-to-user edit system:serviceaccount:platform-operation:imagecopy-job -n user1-application
clusterrole.rbac.authorization.k8s.io/edit added: "system:serviceaccount:platform-operation:imagecopy-job"
```
