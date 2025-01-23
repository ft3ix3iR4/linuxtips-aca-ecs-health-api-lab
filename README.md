# Lab do Health API
Repositório usado para subir o lab de microserviços do Health API no ECS usando o modulo criado em aula

## [v1] - Roteamento Interno e Externo

O Objetivo é subir um ambiente com comunicação distribuída entre vários microserviços internos e externos dentro da AWS 

![v1](.github/assets/health-api.png)

```bash
curl --location --request POST 'http://health.linuxtips.demo/calculator' \
--header 'Content-Type: application/json' \
--data-raw '{ 
   "age": 26,
   "weight": 90.0,
   "height": 1.77,
   "gender": "M", 
   "activity_intensity": "very_active"
} ' --silent | jq .

while true; do curl --location --request POST 'https://8gzb5qepdd.execute-api.us-east-1.amazonaws.com/dev/calculator' \
   --header 'Content-Type: application/json' \
   --header 'x-api-key: '\
   --data-raw '{ 
      "age": 26,
      "weight": 90.0,
      "height": 1.77,
      "gender": "M", 
      "activity_intensity": "very_active"
   } ' --silent -iv; echo; done
```

## [V2] - API Gateway e VPC Link para Exposição Externa

![v2](.github/assets/health-api-gateway.png)