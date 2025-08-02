# Cloud Computing com AWS
---

### O que é Cloud?
- Você acessa servidor, banco de dados na nuvem por meio da internet, pagando pelo uso.

### Benefícios:
- Despesas variáveis, não precisa adivinhas a capacidade, economia de escala (mais usuários + barato), aumenta a velocidade e agilidade, alcance global.

### Modelos de serviço:
- IaaS - básico, você configura e gerencia tudo (ex: Amazon EC2)
- PaaS - sem infraestrutura (ex: Elastic Beanstalk)
- SaaS - produto completo, executado e gerenciado pelo provedor, apenas utiliza (ex:Gmail)

 <img width="635" height="497" alt="image" src="https://github.com/user-attachments/assets/e3c37141-9ec6-4c3e-8470-50fc59a76a0e" />

## Modelos de implantação:
- On-premise, Hybrid e Cloud

---

# Infraestrutura Global AWS

## O que é?
- Infraestrutura de datacenter em todo mundo que fornece os diversos serviços que você pode utilizar na AWS
- Composto por Regiões e Zonas de disponibilidade
   - Regiões:
     > Locais onde são hospedados os data centers
     > cada Região possuem locais isolados chamados de Zonas de Disponibilidade
     > Isolamento de Dados
     > Regulação de dados local
     > conectadas com rede de alta velocidade
     
   - Disponibilidade:
     > Também chamads de AZs (Availability Zones)
     > Agrupamento de datacenters isolados dentro de uma Região
     > Rede, energia e conectividade redundantes
     > Próximas o suficiente para manter baixa latência, longe o suficiente para evitar que um desastre afete mais de uma AZ
     > Recomendações: Execute pelo menos em duas AZs
   
- Vantagens: Alta disponibilidade, Tolerância e falhas

<img width="1147" height="557" alt="image" src="https://github.com/user-attachments/assets/2448e67e-044a-4279-a757-866263af8a9b" />

## Pontos de presença
- Também chamados de Edge Locations, Locais de Borda ou Redes de Borda
- Funcionam como pontos específicos pelo globo para distribuir conteúdo de forma rápida
- Exemplos de serviços que se encontram nos locais de borda: Route 53 (DNS), Cloud Front (CDN)
  > Amazon CloudFront (Serviço de entrega de conteúdo (CDN)
  > Melhora a performance do seu serviço
  > Provê conteúdo o mais próximo possível do usuário
  > Amaxon Route 53 (Serviço DNS) Ajuda os clientes a redirecionar corretamente as requisições

<img width="919" height="513" alt="image" src="https://github.com/user-attachments/assets/20097ba3-3e89-437b-b502-ac5317a502f2" />

## Provisionamento de recursos AWS
- Console de gerenciamento
  - Via portal web com login e senha
- AWS CLI
  - Instala o pacote no seu computador e usa via linha de comando
- AWS SDKs
  - API, Microserviços (possui versões em várias linguagens)
 
---

# Computação em AWS

## Elastic Compute Cloud - EC2
- Capacidade computacional segura e redimensionável
- Computação: CPU, Memória, Rede, Armazenamento, Sistema operacional
- Definição de preço conforme uso e modalidades específicas a necessidade
- Instância com tipos otimizados para sua atividade
- Servidor virtual na nuvem AWS
- Possui configuração de memória, CPU, disco, rede e sistema
- Tipos de instância:
  - Uso Geral
    > Equilíbrio de recursos de computação, memória e rede
    > Indicado para servidores de aplicativo, jogo, backend, banco de dados pequenos
  - Otimizadas para computação
    > Mesmo uso do anterior mas que exija mais performance
    > Ideal também para processamento em lote
  - Otimizadas para memória
    > Projeto para alto desempenho no processamento de grandes quantidades de memória e processamento em tempo real de dados
  - Computação acelerada
    > Processaemnto científico, Gráficos, padrões de dados etc
  - Otimizadas para armazenamento
    > Ideal para trabalhos que exigem acesso de leitura e gravação com grande volume de dados

<img width="992" height="522" alt="image" src="https://github.com/user-attachments/assets/acc5ae5b-1e41-4138-baae-c72c976a9202" />  


## Amazon EC2 AutoScaling
- Provê escalabilidade horizontal para seus serviços
- Melhor tolerância a falhas com identificação de instâncias indiposnpiveis e implantação multi-AZ
- Melhor gerenciamento de custos


##Elastic Load Balancing - ELB
- É um balanceamento de carga de aplicação, gateway e rede
  > Um algoritmo que decide pra onde ele vai enviar uma determinada requisição
- Escala de forma automática, sem custos


## Serviços de mensageria
- SQS (Simple Queue Service) - se comunicam de forma assíncrona e funciona em forma de fila (lê, processa e apaga da fila em ordem)
- SNS (Simple Notification Service) - se comunica em tópicos, com ms que tenham interesse nessas mensagens dos tópicos



# <img width="445" height="169" alt="image" src="https://github.com/user-attachments/assets/9a37b176-9562-4908-895d-821520048acb" /><br>
<img width="499" height="281" alt="image" src="https://github.com/user-attachments/assets/8907e8dc-d05c-445d-9cec-1fee72b20fb8" />

## Computação sem servidor
- Também chamamos de "Servless"
- Significa que o código é executado em servidores sem que você precise provisionar ou gerenciar esses servidores
- Capacidade automaticamente ajustada pelo serviço, sem necessidade de nenhuma configuração
  - AWS Lambda
    > Execução de código sem provisionar servidores
    > Código organizado em funções
    > Escolha da linguagem de programação
    > Executa a partir de eventos ou chamadas diretas a API do Lambda
  - O custo é por tempo de CPU

## Containers em AWS
- ECR - Elastic Container Registry
<img width="1113" height="297" alt="image" src="https://github.com/user-attachments/assets/591f5e6e-c5a2-4ccf-9e4d-7cb3fb3d6cf6" /><br>

- ECS - Elastic Container Servie
<img width="775" height="340" alt="image" src="https://github.com/user-attachments/assets/3fd7a6da-4299-4eff-8259-221b1e949f8b" /><br>

- EKS - Elastic Kubernates Service
<img width="934" height="349" alt="image" src="https://github.com/user-attachments/assets/f310a2b4-ade5-403f-a9f2-3e4622888b13" /><br>

- AWS Fargate
<img width="2334" height="948" alt="image" src="https://github.com/user-attachments/assets/aba10bca-0d05-4569-bc5c-475f12bfd3e6" /><br>
---

# Redes em AWS

## Amazon VPC
- Seria tipo um escritório na nuvem
- VPC: Virtual Private Cloud
- Permite construir e configurar redes virtuais na AWS
- Sub-redes: privadas e públicas
- "Tudo começa dentro de um VPC"

## Conectividade com AWS
- Conectar a VPC a sub-redes públicas e privadas (gateway da internet e gatewae privado virtual)
- AWS Direct Connect é uma conexão dedicada

## Sub-redes e listas de controle de acesso
- Network ACLs
  - É uma configuração que prove controle do que entra e do que sai
  - Comportamento Stateless
  - Por padrão, permite todo tráfego de entrada e saída (precisa ajusatar)
- Grupos de segurança
  - Controle tráfego de entrada e saída de instância EC2
  - Comportamento Stateful
  - Por padrão, nega todo tráfego de entrada e permite todo tráfego de saída (precisa ajusatar)
 
<img width="726" height="384" alt="image" src="https://github.com/user-attachments/assets/44cc857e-97c4-4419-b317-d93cb5354bb3" /><br>


---
> ⚠️ **Observação:** Este módulo de estudos foi desenvolvido com base no curso disponibilizado pela plataforma DIO. Algumas imagens e conteúdos utilizados pertencem à plataforma e são empregados aqui exclusivamente para fins didáticos, visando a fixação do meu aprendizado.
