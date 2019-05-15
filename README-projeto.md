## Responder para Projeto

### Tipos de <u>Quotas</u>

#### 	compute-resources

- Qual é total de Recursos disponível?

  - 5Gi
  - 4 Cores

  #### object-counts-managed

- Quanto é grande para um projeto? 

  - *Ou seja, Pod* 20, 30, 40, 100?

  #### storage-resources

- Qual é total de Recursos disponível?

  - 2 Tb
  - Velocidade

### Como dividir/priorizar os projetos

- um SISTEMA  ***pode*** ser composto de vários projetos
  - esta informação é obtida no pré-projeto? Componentes? —> no planejamento
  - considerando reuso de recurso/ajustes/, sabe-se do <u>impacto</u> a ser gerado?
- há critérios claros para priorizar o projeto (ou seja, como dizer que o projeto X tem apenas 10% dos recursos, ou 80%) —> não será atuando agora.
- o que acontece quando acaba o recurso daquele projeto, mas há espaço no ambiente? 
  - será feito uma redistribuição?
  - será acrescentado novos recursos apenas para a nova aplicação?



## Definição

### Pod

- is in a <u>terminal</u> state if `status.phase in (Failed, Succeeded)` is true.

#### Pod Phases

1. *Pending*: The API Server has created a pod resource and stored it in etcd, but the pod has not been scheduled yet, nor have container images been pulled from the registry.
2. *Running*: The pod has been scheduled to a node and all containers have been created by the kubelet.
3. ***Succeeded***: All containers in the pod have terminated successfully and will not be restarted.
4. ***Failed***: All containers in the pod have terminated. At least one container has terminated in failure.
5. *Unknown*: The API Server was unable to query the state of the pod, typically due to an error in communicating with the kubelet.