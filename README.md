# OCP Cluster Configuration with GitOps example
 
This repository serves as an example of how ArgoCD can be used to configure an OpenShift Cluster.
 
In this example, the projects (Applications)  are separated by categories. Another option would be to separate the CRD declaration by namespace (Having one folder by namespace)
 
The label **argocd.argoproj.io/sync-options: Prune=false** has been added to some of the resources, stops ArgoCD from deleting global cluster configuration resources, when auto-sync is enabled. 
 
###### Api Configuration
 
CRDs that configure the API default certificate. 
 
```bash
argocd app create api-config --repo https://github.com/maemmanu/argocd-day2.git \
--path=api-config --dest-server=https://kubernetes.default.svc
```
 
###### Identity Provider
 
CRDs that configure an HTPasswd Identity Provider. 
 
```bash
argocd app create identity-provider --repo https://github.com/maemmanu/argocd-day2.git \
--path=identity-provider --dest-server=https://kubernetes.default.svc
```
 
###### Infrastructure Nodes
 
Machineset CRD to create infrastructure nodes. 
 
```bash
argocd app create infra-nodes --repo https://github.com/maemmanu/argocd-day2.git \
--path=infra-nodes --dest-server=https://kubernetes.default.svc
```
 
###### Ingress Config
 
Ingress Certificate configuration.  
 
```bash
argocd app create ingress-config --repo https://github.com/maemmanu/argocd-day2.git \
--path=ingress-config --dest-server=https://kubernetes.default.svc
```
 
###### Logging
 
Installation of Cluster Logging Operator and Elasticsearch and Configuration of the logging stack.
 
```bash
argocd app create logging --repo https://github.com/maemmanu/argocd-day2.git \
--path=logging --dest-server=https://kubernetes.default.svc
```
###### Project Request
 
Configuration of a Project Request Template that includes the creation of Quotas, Limit Ranges and Network Policies upon the creation of a new project
 
```bash
argocd app create project-request --repo https://github.com/maemmanu/argocd-day2.git \
--path=project-request --dest-server=https://kubernetes.default.svc
```

