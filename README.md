## Responder

### compute-resources

- Qual é total de Recursos disponível?
  - 5Gi
  - 4 Cores

### object-counts-managed

- Quanto é grande para um projeto? 
  - *Ou seja, Pod* 20, 30, 40, 100?

### storage-resources

- Qual é total de Recursos disponível?
  - 2 Tb
  - Velocidade



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



## Definição

### Pod

- is in a <u>terminal</u> state if `status.phase in (Failed, Succeeded)` is true.

#### Pod Phases

- *Pending*: The API Server has created a pod resource and stored it in etcd, but the pod has not been scheduled yet, nor have container images been pulled from the registry.
- *Running*: The pod has been scheduled to a node and all containers have been created by the kubelet.
- ***Succeeded***: All containers in the pod have terminated successfully and will not be restarted.
- ***Failed***: All containers in the pod have terminated. At least one container has terminated in failure.
- *Unknown*: The API Server was unable to query the state of the pod, typically due to an error in communicating with the kubelet.