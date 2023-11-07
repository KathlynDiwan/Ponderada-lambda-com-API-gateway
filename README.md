# Ponderada Lambda com API gateway

Configuração do lambda
O AWS Lambda é um serviço de computação essencial que possibilita a execução de código em resposta a eventos, eliminando a complexidade de gerenciar servidores. Sua importância é inegável, pois simplifica significativamente a criação de serviços, desempenhando um papel central na construção de sistemas eficientes e escaláveis. Este serviço oferece benefícios substanciais, incluindo custos reduzidos, dimensionamento automático e uma integração perfeita com uma variedade de outros serviços AWS.

1. Abrir o AWS Academy
2. Para criar o lambda novo, preciso pesquisar dentro dos servicos da AWS por "Lambda" e criar a função com um nome (kathyFunction)
3. Escolha o tempo de execução --> o padrão que esta na AWS é o node, mas escolheremos o python , por conta da ponderada pelo fato de ele ser mais perfomatico.
4. Depois disso, escolherei a arquitetura ideal do meu processo --> na etapa de permissão escolherei a função de selecionar uma função já exixstente, e na hora de seelcionar escolherei o Lab Role, que é um ambiente de aprendizagem.
5. Adicionar um trigger (gatilho), no caso do nosso autoestudo iremos adicionar um API Gateway
6. O gatilho será criado e você devera entrar no trigger e clicar no link do "API Gateway" (imagem x) 
7. Criar um novo API Gateway com segurança aberta (Open) e mantenha-o como uma REST API.

![image](https://github.com/KathlynDiwan/Ponderada-lambda-com-API-gateway/assets/99209712/f08e6c88-c6ba-483e-9797-3dbcc17d7900)
Imagem 1: Overview da função: kathyFunction

Dessa forma, terei uma arquitetura que estara se comunicando dentro da propria AWS. Com isso, dentro do Lambda, vou abrir o codigo lambda que ja contem uma funcao padrão chamada funcao_handler, mas que eu tenho a possibilidade de criar outras. 


Implementação do endpoint REST 
A implementação REST refere-se a um estilo de arquitetura com práticas escaláveis, e eficientes. 

Autenticação 

Utilização de DRY e classes

Testes unitários realizados 
Foi se reaolizado um teste com o intuito de conseguir testar a função lambda_handler com as alterações ajustes e incrementos que foi feito a aprtir do enunciado dessa ponderada. 
(inserir imagem) 
