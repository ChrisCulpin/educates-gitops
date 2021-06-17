Educates
========

This repository holds the master resource files for deploying the Educates operator and training environment for a production environment. The resource files are bound to specific tagged versions of the Educates operator and associated components. By using these resource files you ensure that any subsequent updates to Educates will not affect your current deployment.

For more comprehesive documentation on how to deploy and use Educates, see:

* https://docs.edukates.io/

### Deploy it using ArgoCD

Create an application on you ArgoCD Server:

```
argocd app create educates-operator --sync-policy auto \
    --repo https://github.com/educates/educates-gitops.git \ 
    --revision gitops --path v1 --dest-namespace eduk8s \
    --dest-server https://l4lk70lb74sd307ii9hj5px8iukm-k8s-1912902137.us-east-1.elb.amazonaws.com:443 
```

Deploy sample workshop:

```
argocd app create lab-markdown-sample --sync-policy auto \
    --repo https://github.com/educates/lab-markdown-sample.git \
    --path resources \
    --dest-server https://l4lk70lb74sd307ii9hj5px8iukm-k8s-1912902137.us-east-1.elb.amazonaws.com:443
```