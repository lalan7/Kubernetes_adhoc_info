# Kubernetes_adhoc_info

Nice layout about kube

http://k8s.info/cs.html#ao

Minikube simple step by step:

http://sharepointoscar.com/2017-04-12-deploy-a-static-site-using-an-nginx-docker-container-to-a-local-kubernetes-minikube-instance/

Minikube: to access API 

```
$ APISERVER=$(kubectl config view | grep server | cut -f 2- -d ":" | tr -d " ")
$ TOKEN=$(kubectl describe secret $(kubectl get secrets | grep default | cut -f1 -d ' ') | grep -E '^token' | cut -f2 -d':' | tr -d '\t')
$ curl $APISERVER/api --header "Authorization: Bearer $TOKEN" --insecure
{
  "kind": "APIVersions",
  "versions": [
    "v1"
  ],
  "serverAddressByClientCIDRs": [
    {
      "clientCIDR": "0.0.0.0/0",
      "serverAddress": "10.0.1.149:443"
    }
  ]
}

```