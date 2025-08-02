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
