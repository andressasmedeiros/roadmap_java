# Engenharia de Prompts

## o que é a engenharia de prompts
- A Engenharia de Prompt é a prática de criar instruções claras e estruturadas para modelos de linguagem, visando obter respostas mais úteis, precisas e alinhadas com o objetivo desejado.
Um bom prompt fornece contexto, direção e formato esperado, permitindo que a IA compreenda melhor a tarefa.

## Componentes Essenciais de um Prompt
- Instruções: Definem a tarefa (ex.: "Resuma o texto abaixo em 3 frases objetivas.")
- Exemplos (Few-shot Learning): Pares de entrada/saída para guiar o modelo.
- Contexto ou Configuração: Define papel da IA e cenário de uso.
- Restrições ou Limitações: Limita escopo, extensão ou conteúdo da resposta.
- Conteúdo Principal: Texto ou dados a serem processados.
- Indicações: Estímulos para guiar o formato da resposta ("Liste pontos principais", "Responda em um parágrafo").
- Formato de Saída: Define estrutura da resposta (JSON, lista, tópicos claros).
- Conteúdo de Suporte: Dados extras, datas ou preferências relevantes.

## Técnicas de Engenharia de Prompt
> Com base nos prints anexados:

- Instruções Claras: Orientações objetivas no início do prompt.
- Preparar a Saída: Palavras ou frases finais para moldar a resposta.
- Solicitação de Cadeia de Pensamento: Força um raciocínio passo a passo.
- Especificar Estrutura de Saída: Define formato (JSON, tabela, lista).
- Repetir Instruções no Final: Reforça a tarefa para evitar desvios.
- Dividir a Tarefa: Quebra problemas complexos em etapas.
- Adicionar Sintaxe Clara: Usa listas, tabelas ou títulos para clareza.
- Guardrails: Limita respostas para evitar conteúdos irrelevantes ou prejudiciais.

---

###  Abordagem RGC (Role, Goal, Context)
- Role (Papel): Define o papel que a IA deve assumir.
   > Ex.: "Você é um professor de matemática especializado em álgebra."
- Goal (Objetivo): Explica a finalidade da interação.
   > Ex.: "Explique o teorema de Pitágoras para iniciantes."
- Context (Contexto): Fornece informações adicionais para ajudar a resposta.
   > Ex.: "O público-alvo são alunos de 13 anos com conhecimento básico em geometria."
 
 ---
 
### Target (Público-Alvo)
- Definir para quem é direcionada a resposta melhora a relevância do resultado.
  > Exemplo: "Crie um texto motivacional sobre disciplina, direcionado para atletas iniciantes."

---

### Estrutura TSL (Tone, Style, Length)
- Permite ajustar a personalidade e formato da resposta.
   - Tone (Tom): Formal, amigável, técnico, motivacional.
   - Style (Estilo): Narrativo, instrutivo, resumido, lista.
   - Length (Extensão): Número de palavras, frases ou parágrafos.
     > Exemplo: "Explique como funciona a energia solar em tom amigável, estilo de lista, com até 100 palavras."

---

### Divisão de Tarefas (Task Splits)
- Para prompts complexos, dividir a solicitação em etapas aumenta a clareza e a qualidade do resultado.
  > Exemplo:
  > 1. "Liste as causas do aquecimento global."
  > 2. "Explique cada causa em um parágrafo separado."
  > 3. "Sugira soluções práticas para mitigar esses problemas."

---

### ABA – Ask Before Answer
- Técnica para garantir que a IA entenda a necessidade antes de responder, solicitando esclarecimentos quando necessário.
  > Exemplo: "Se precisar de mais detalhes sobre meu objetivo, pergunte antes de responder."

---

### Exemplos de Prompts Eficientes
- RGC + TSL:
  > "Você é um consultor de marketing (Role). Quero criar um post para Instagram sobre produtividade (Goal). O público-alvo são empreendedores iniciantes (Context). Use um tom inspirador, estilo lista, até 80 palavras."
- Task Split:
  > 1) Liste os principais benefícios da IA na saúde.
  > 2) Dê exemplos reais.
  > 3) Finalize com possíveis riscos.
- Formato Específico:
  > "Responda em JSON com os campos: beneficio, exemplo, risco."

---
##  Boas Práticas Gerais
- Comece com instruções claras e diretas.
- Forneça contexto suficiente para reduzir ambiguidades.
- Use exemplos quando possível.
- Especifique formato e limite de resposta.
- Reforce instruções no final para evitar desvios.
- Utilize ABA para garantir que a IA entenda antes de gerar uma resposta.
- Teste variações do prompt e refine até obter o resultado ideal.

---
# Segue abaixo prints de um mapa mental sobre técnicas de engenharia de prompts e componentes de um prompt.

<img width="1071" height="794" alt="image" src="https://github.com/user-attachments/assets/44e3577d-62a2-4149-a675-633d66794a54" /><br>
<img width="1069" height="799" alt="image" src="https://github.com/user-attachments/assets/27c60796-51c4-49a3-870f-15d382ac123f" /><br>

---

<img width="1079" height="803" alt="image" src="https://github.com/user-attachments/assets/6aed2ca3-b4fc-40df-bb5e-7f028e66af81" /><br>
<img width="1077" height="782" alt="image" src="https://github.com/user-attachments/assets/30b05417-854c-4b66-95ab-f9113f9a5867" />
<br>


---
> ⚠️ **Observação:** Este módulo de estudos foi desenvolvido com base no curso disponibilizado pela plataforma DIO. Algumas imagens e conteúdos utilizados pertencem à plataforma e são empregados aqui exclusivamente para fins didáticos, visando a fixação do meu aprendizado.

