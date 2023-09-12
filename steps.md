# Install ARGOcd

```bash
$ minikube start --driver=docker --nodes 2
$ minikube addons enable ingress
$ kubectl create namespace argocd
$ kubectl apply -n argocd -f argocd/install.yaml
# Ref.: https://argo-cd.readthedocs.io/en/stable/operator-manual/ingress/#option-2-ssl-termination-at-ingress-controller
$ kubectl apply -f argocd/https-ingress.yml
$ kubectl apply -f argocd/grpc-ingress.yml
$ PASS=$(argocd admin initial-password -n argocd | head -1)
$ argocd login \
    --insecure \
    --username admin \
    --password ${PASS} \
    --grpc-web \
    argocd.info
$ minikube start --driver=docker --nodes 2 --profile gitops
$ kubectl config get-contexts -o name
$ argocd cluster add gitops --insecure
$ kubectl config set-context --current --namespace=argocd
$ argocd app create guestbook \
    --repo https://github.com/argoproj/argocd-example-apps.git \
    --path guestbook \
    --dest-server https://kubernetes.default.svc \
    --dest-namespace default
```

# Backstage in Kubernetes

```bash
kubectl create namespace backstage





```
