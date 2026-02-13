###Como rodar na sua máquina (Local)
Para subir a aplicação inteira com um comando só, usamos o Docker Compose:

Entre na pasta do projeto.

Digite no terminal: docker compose up -d (o build vai ser feito na hora).

Para conferir se subio tudo certo, use: docker ps.


Nota: Os serviços de Gateway, Pedidos e Estoque já sobem juntos com o banco PostgreSql.



###Rodando no Kubernetes (K8s)
O ambiente de produção foi desenhado para rodar em cluster. Os arquivos de configuração estão na pasta /k8s.

Aplicar as configs: kubectl apply -f k8s/

Checar os pods: kubectl get pods

Usamos ConfigMaps e Secrets para as senhas e configs de ambiente, conforme as boas prátcas.



###CI/CD e Infra

Pipeline: Tem um workflow no GitHub Actions que faz o build e validações básicas de lint e scan toda vez que tem push na main.


Terraform: Tem um esqueleto de código na pasta /terraform pra mostrar como a infra pode ser repoduzida.


Escala: Configuramos a lógica de HPA para aguentar os picos de acesso na campanha da loja.



###Monitoramento e Tracing
Para a parte de observabilidade avançada, a proposta é usar:

Métricas: Prometheus.


Logs: Coleta via stdout pelo Kubernetes.


Tracing: OpenTelemetry + Jaeger para achar falhas entre os microsserviços.



###Estratégia de Deploy
Escolhemos o Rolling Update. Assim, o site não fica fora do ar enquando a gente sobe uma versão nova, reduzindo o risco de erro que a empresa tinha antes.