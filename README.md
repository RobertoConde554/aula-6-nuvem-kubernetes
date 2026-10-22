# aula-6-nuvem-kubernetes



# Aula 6 - Computação em Nuvem Kubernetes

## O que foi feito:
- Criamos um ConfigMap para servir uma página HTML no Nginx sem precisar rebuildar a imagem.
- Criamos um PV (PersistentVolume) e um PVC (PersistentVolumeClaim) no modo manual usando hostPath.
- Testamos a persistência: gravamos um arquivo, deletamos o Pod, criamos outro e o arquivo continuou lá.

## Como rodar:
Ambiente usado: Killercoda (Kubernetes Playground)
Aplica tudo na ordem:
kubectl apply -f configmap.yaml
kubectl apply -f pod-web.yaml
kubectl apply -f pv.yaml
kubectl apply -f pvc.yaml
kubectl apply -f pod-dados.yaml

## Teste de persistência:
kubectl exec pod-dados -- sh -c 'echo "Dado persistente da Aula 6" > /dados/mensagem.txt'
kubectl delete pod pod-dados
kubectl apply -f pod-dados-2.yaml
kubectl exec pod-dados-2 -- cat /dados/mensagem.txt

## Limpeza:
kubectl delete -f .
