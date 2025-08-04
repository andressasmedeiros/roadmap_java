## REST e RESTful

## Primeiro vamos entender o que é uma API?
- é uma Aplicação para servir dados de mandeira padronizada seguindo alguns protocolo de comunicação (exemplo mais usado HTTP)
- Serve para receber e processar dados em serviços e responder para outras aplicações

<img width="440" height="631" alt="image" src="https://github.com/user-attachments/assets/1f9b6bea-037f-453c-a164-269993a6b6bb" />

## Características de uma aplicação
- Ter protocolos de comunicação rígiso tanjto para responder (response) coisas, quanto para requisições (request).
- HTTP - sempre serve algum conteúdo (content) seguindo os padrões de protocolo adotado

## Padrões de arquitetura REST (Representational State Transfer)
- É você pegar algum conteúdo que está dentro da aplicação backend e transferir para o seu front
- Características cliente x servidor
- Front e Back separados em tecnologias diferentes
- Comunicação Stateless (estado da comunicação)
- Cache (pegar requests parecidos e manda a mesma informação)-(ter a possibilidade)
- Interface uniforme
- Sistema de camadas (as pastas organizadas)

<img width="848" height="528" alt="image" src="https://github.com/user-attachments/assets/fab57061-647d-4f45-b419-7b0eff8e08cb" />

- Quando você usa algumas dessas características chamamos de REST e quando usamos todas as 5 chamamos de RESTful

## Principais métodos HTTP utilizados em REST
- GET: Obter informações de um recurso.
- POST: Criar um novo recurso.
- PUT: Atualizar completamente um recurso existente
- PATCH: Atualizar parcialmente um recurso.
- DELETE: Remover um recurso.

- Exemplos:
```java
GET /usuarios        # Lista todos os usuários
GET /usuarios/1      # Obtém dados do usuário com ID 1
POST /usuarios       # Cria um novo usuário
PUT /usuarios/1      # Atualiza os dados do usuário 1
DELETE /usuarios/1   # Deleta o usuário 1
```

## Boas prtáticas em APIs REST
- Utilizar nomes de recursos no plural (/usuarios e não /usuario)
- Usar status codes HTTP corretamente:
  - 200 OK → Sucesso
  - 201 Created → Criado com sucesso
  - 400 Bad Request → Erro do cliente
  - 404 Not Found → Recurso não encontrado
  - 500 Internal Server Error → Erro interno no servidor
- Versionamento da API (/api/v1/usuarios).
- Utilizar JSON como formato padrão de resposta.
- Retornar mensagens de erro claras e padronizadas.

## Exemplo de Estrutura de Resposta JSON
```json
{
  "data": {
    "id": 1,
    "nome": "João Silva",
    "email": "joao@email.com"
  },
  "status": 200,
  "message": "Usuário encontrado com sucesso"
}
```
## Benefícios de Usar REST
- Escalabilidade da aplicação.
- Facilidade de integração entre diferentes sistemas.
- Uso amplo do protocolo HTTP (sem necessidade de padrões proprietários).
- Compatível com diversas linguagens e frameworks.

## Projeto que utilizei uma API RESTful
https://github.com/andressasmedeiros/gerenciamento_farmacia/tree/main/api


---
> ⚠️ **Observação:** Este módulo de estudos foi desenvolvido com base no curso disponibilizado pela plataforma DIO. Algumas imagens e conteúdos utilizados pertencem à plataforma e são empregados aqui exclusivamente para fins didáticos, visando a fixação do meu aprendizado.
