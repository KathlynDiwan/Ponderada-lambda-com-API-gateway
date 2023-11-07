## Ponderada Lambda com API gateway

# Configuração do lambda
O AWS Lambda é um serviço de computação essencial que possibilita a execução de código em resposta a eventos, eliminando a complexidade de gerenciar servidores. Sua importância é inegável, pois simplifica significativamente a criação de serviços, desempenhando um papel central na construção de sistemas eficientes e escaláveis. Este serviço oferece benefícios substanciais, incluindo custos reduzidos, dimensionamento automático e uma integração perfeita com uma variedade de outros serviços AWS.

1. Abrir o AWS Academy
2. Para criar o lambda novo, preciso pesquisar dentro dos servicos da AWS por "Lambda" e criar a função com um nome (kathyFunction)
3. Escolha o tempo de execução --> o padrão que esta na AWS é o node, mas escolheremos o python , pelo fato de ele ser mais perfomático.
4. Depois disso, escolherei a arquitetura ideal do meu processo  selecionando o Lab Role.
5. Adicionarei um trigger (gatilho),--> API Gateway
7. Criar um novo API Gateway com segurança aberta (Open) e mantenha-o como uma REST API.

![image](https://github.com/KathlynDiwan/Ponderada-lambda-com-API-gateway/assets/99209712/f08e6c88-c6ba-483e-9797-3dbcc17d7900)
Imagem 1: Overview da função: kathyFunction

Dessa forma, terei uma arquitetura que estara se comunicando dentro da propria AWS. Com isso, dentro do Lambda, vou abrir o codigo lambda que ja contem uma funcao padrão chamada funcao_handler, mas que eu tenho a possibilidade de criar outras. 


# Implementação do endpoint REST 
A implementação REST refere-se a um estilo de arquitetura com práticas escaláveis, e eficientes. 

# Autenticação 
Para realizar a autenticação, criei um token chamado "Kathy", que deve ser inserido no sistema. Quando os testes são executados, se o token inserido for "Kathy", o sistema retornará uma mensagem indicando que a autenticação foi bem-sucedida. No entanto, se o token inserido não corresponder ao "Kathy" que defini, o sistema enviará uma mensagem informando que ocorreu uma falha no processo de autenticação. Na seção de testes unitários, apresentei exemplos disso.

# Código Lambda function 

![image](https://github.com/KathlynDiwan/Ponderada-lambda-com-API-gateway/assets/99209712/3b9d91d5-15e8-4852-bf62-481cfb1a0c18)

import json

def lambda_handler(event, context):
    if "headers" in event and "Authorization" in event["headers"]:
        authorization_header = event["headers"]["Authorization"].replace("Bearer ", "Kathy")
        token = "Kathy"
        
        if authorization_header == token: ##se inserir meu token correto, autenticacão vsi ser realizada
            response = {
                'statusCode': 500,
                'body': json.dumps('Autenticacao realizada!')
            }
        else:
            response = {
                'statusCode': 200,
                'body': json.dumps('Falha na autenticacao. O nome inserido está incorreto, e nao corresponde ao tojen')
            }
 

    return response

# Testes unitários realizados 
Criei 2 testes distintos para testar o meu código JSON e a questão da identificação. 

1. Esse primeiro exemplo se diz a respeito da **Autenticação realizada com sucesso***
Nesse caso criei esse evento de teste com o token correto --> Kathy
![image](https://github.com/KathlynDiwan/Ponderada-lambda-com-API-gateway/assets/99209712/a321be23-87c7-4afb-a4df-24356db635b0)
Abaixo pode ser visto o resultado e mensagem de sucesso enviada!
![image](https://github.com/KathlynDiwan/Ponderada-lambda-com-API-gateway/assets/99209712/ceecba7b-c412-4a50-8665-81b76351e208)

  
2. Nessa etapa, criei um teste de **Autenticação não realizada**
Nesse caso criei esse evento de teste com o token incorreto --> "Qualquer outro nome" se referindo que qualquer outra escirta além de kathy daria erro
![image](https://github.com/KathlynDiwan/Ponderada-lambda-com-API-gateway/assets/99209712/4c2f6f44-f6b9-4f1b-89bd-459a4aa0b7fa)
Abaixo pode ser visto o resultado e mensagem de erro enviada!
![image](https://github.com/KathlynDiwan/Ponderada-lambda-com-API-gateway/assets/99209712/1a63b108-c33c-4497-831c-4e4efa08692f)

