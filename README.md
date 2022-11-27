### Basic Helm Chart for the application : https://github.com/naren4b/my-app
```
# set the values 
helm install my-app . -n demo
helm list 
```
# Check the ingress 
```
kubectl get ing -n demo
```
# Uninstall 
```
helm uninstall my-app
```
# helm Charts packaging 
```
chartVersion=1.1.0
chartmuseumURL=http://chartmuseum.127.0.0.1.nip.io
userid=curator
password=mypassword

helm package --version=${chartVersion} . -d release
curl --data-binary "@release/myApp-${chartVersion}.tgz" ${chartmuseumURL}/api/charts --insecure -u ${userid}:${password}
curl ${chartmuseumURL}/api/charts/myApp/${chartVersion}  --insecure -u ${userid}:${password}
```