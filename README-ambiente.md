```shell
$ oc create clusterquota env-dev \
 			--project-label-selector environment=dev \
 			--hard pods=10 \
 			--hard services=5 \
 			--hard requests.cpu=2 \
 			--hard requests.memory="2Gi" \
 			--hard limits.cpu="3" \
 			--hard limits.memory="3Gi"
```

```shell
# atribuir label para o node (máquina)
$ oc get nodes --show-labels=true
oc label  node localhost environment=dev

# anotar o projeto
$ oc annotate ns $(oc project -q) openshift.io/node-selector='environment=dev'
```

```shell
$ oc describe clusterquota env-dev
Name:		env-dev
Created:	5 minutes ago
Labels:		<none>
Annotations:	<none>
Namespace Selector: []
Label Selector: environment=dev
AnnotationSelector: map[]
Resource	Used	Hard
--------	----	----
```



```
oc create clusterlimits
```



## Criação dos Projetos

```shell
oc new-project projeto-dev-01
oc new-project projeto-dev-02
oc new-project projeto-uat-01
oc new-project projeto-uat-02
oc new-project projeto-prd-01
oc new-project projeto-prd-02
```



## Definição das Quotas

```shell
oc project projeto-dev-01
oc apply -f templates/compute-resources.yaml
oc apply -f templates/object-counts-managed.yaml
oc apply -f templates/storage-resources.yaml
```

```shell
oc project projeto-dev-01
oc apply -f templates/core-object-counts.yaml
oc apply -f templates/openshift-object-counts.yaml
oc apply -f templates/compute-resources.yaml
oc apply -f templates/besteffort.yaml
oc apply -f templates/compute-resources-long-running.yaml
oc apply -f templates/compute-resources-time-bound.yaml
oc apply -f templates/storage-consumption.yaml
```



## Visão por Nodes

```shell
oc get nodes --show-labels
```



## Reference

- https://docs.openshift.com/container-platform/3.11/scaling_performance/cluster_limits.html