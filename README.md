# Kubernetes Microservices Load Testing Toolkit 🚀

Scripts para gerar tráfego em ambientes Kubernetes na aplicação **Online Boutique** (Google Cloud). Compatível com Locust, K6, JMeter e Artillery.

![Load Testing](https://img.shields.io/badge/Load_Testing-Toolkit-blue) 
![Kubernetes](https://img.shields.io/badge/Platform-Kubernetes-purple)

## Pré-requisitos ⚙️

- Cluster Kubernetes com a aplicação [Online Boutique](https://github.com/GoogleCloudPlatform/microservices-demo) implantada
- `kubectl` configurado para acesso ao cluster
- Ferramentas instaladas:
  - [Locust](https://locust.io/) (Python)
  - [k6](https://k6.io/) (JS)
  - [JMeter](https://jmeter.apache.org/) (Java)
  - [Artillery](https://artillery.io/) (Node.js)

## Estrutura do Repositório 📂

## Como Executar 🛠️

### Locust
```bash
# Executar localmente
locust -f locust/locustfile.py --host=<URL_DA_APLICACAO>

# Implantar no Kubernetes (modo distribuído)
kubectl apply -f locust/locust-master-deployment.yaml
kubectl apply -f locust/locust-worker-deployment.yaml


```
# K6
## Teste local
k6 run --vus 100 --duration 300s k6/script.js

# Jmeter
## Executar plano de teste
jmeter -n -t jmeter/test_plan.jmx -l results.jtl

## Gerar relatório HTML
jmeter -g results.jtl -o dashboard/

# Execução no cluster (via Job do Kubernetes)
kubectl apply -f k6/k8s-deployment.yaml

# Artillary
## Teste rápido
artillery run --environment production artillery/load-test.yaml

## Execução contínua
artillery run-artillery/load-test.yaml --count 10 -n 500




