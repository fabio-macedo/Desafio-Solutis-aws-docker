# Desafio-Solutis-aws-docker
  Explicação simplificada sobre como configurar o LocalStack e simular os serviços AWS, como SQS, em integração com uma aplicação JAVA
## Pré-requisitos

* Docker
* AWS CLI
* JAVA: necessário haver o JDK instalado para compilar os códigos JAVA

  # Passo a passo

  1 - Primeiramente inicie um terminal ou PowerShell e execute o seguinte comando abaixo, para iniciar o LocalStack em um container Docker:
  
   ```
   docker run --rm -it -e SERVICES=sqs -p 4566:4566 localstack/localstack
  ```
  2 - Verifique se o container está de fato sendo executado
  ```
  docker ps
  ```
![container em execucao](https://github.com/user-attachments/assets/424755cd-574d-4bd6-b3a1-3a151d24a8de)


3 - Configurando as credenciais do AWS
```
aws configure
```

![aws configure](https://github.com/user-attachments/assets/421db18a-f9d9-46dd-b956-f179c49e5c17)

4 - Verificar se as mensagens estão em fila
```
aws --endpoint-url=http://localhost:4566 sqs receive-message --queue-url http://sqs.us-east-1.localhost.localstack.cloud:4566/000000000000/minha-fila --max-number-of-messages 1 --wait-time-seconds 10
```

![mensagens fila 1](https://github.com/user-attachments/assets/999f56ca-3593-4cce-be89-e2703ce8f263)


5 - Consumir pelo programa - 'SqsConsumer'


![CONSUMER](https://github.com/user-attachments/assets/9f93ac9f-6e50-4d41-8d04-2007cb130446)






