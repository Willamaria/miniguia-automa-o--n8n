# ⚡ Miniguia de Estudos: Automação de Workflows no Dia a Dia com n8n

> **Desafio de Projeto DIO:** *Treinando uma IA de Aprendizagem: Explore o Poder do NotebookLM*  
> **Autor:** William Silva Assis  
> **Ferramentas Utilizadas:** Google NotebookLM, n8n, GitHub, Markdown
> https://notebook.google.com/notebook/3aa82d1a-b6e0-4dc8-acbb-87386c497419?authuser=1

---

## 🎯 1. Contexto e Objetivos

### Contexto
A automação de processos repetitivos é uma das habilidades mais demandadas no mercado atual. O **n8n** é uma plataforma *node-based* de automação de workflows que permite integrar APIs, serviços de IA, bancos de dados e ferramentas de comunicação de forma flexível e eficiente.

Este repositório documenta a criação de um Caderno Temático no **NotebookLM** focado no estudo prático de automação de processos do dia a dia e orquestração de rotinas utilizando n8n.

### Objetivos de Estudo
- **Compreender** os blocos fundamentais de um workflow no n8n (Triggers, Nodes de Ação, Webhooks, Condicionais e Manipulação de Dados).
- **Mapear** casos de uso do dia a dia (ex: integração de formulários, notificações, disparo de e-mails, consumo de APIs e agentes de IA).
- **Documentar** testes de engenharia de prompts e *troubleshooting* usando o NotebookLM como assistente de estudo.
- **Criar** um guia prático e reutilizável de conceitos e prompts para acelerar a construção de automações reais.

---

## 🔗 2. Curadoria de Fontes

Para alimentar o NotebookLM com documentação oficial e de qualidade sobre n8n e automação, foram selecionadas as seguintes fontes abertas:

1. **Documentação Oficial do n8n (Core Concepts):** *Workflows, Nodes, Triggers & Expressions* (Guias técnicos de conceitos básicos).
2. **Documentação Oficial de Data Transformation:** *Using JavaScript/Python Code Nodes in n8n* (Guia de manipulação de JSON e dados).
3. **Tutorial de Webhooks & HTTP Request:** *Connecting External Services via REST APIs in n8n* (Artigo técnico de integração).
4. **Guia de boas práticas de Error Handling:** *Handling Errors, Retries & Sub-workflows in n8n* (PDF/Documentação de resiliência em automações).

---

## 🧪 3. Engenharia de Prompts & "Cicatrizes" (Troubleshooting)

Documentação dos testes de prompts realizados no NotebookLM para extrair o funcionamento técnico do n8n.

### Prompt 1: Diferenciação de Conceitos Chave
- **Prompt Utilizado:**  
  `"Com base nos documentos carregados, explique a diferença prática entre um 'Trigger Node' e um 'Action Node' no n8n, e dê um exemplo real de fluxo usando ambos."`
- **Resultado da IA:**  
  A IA identificou que o Trigger é o gatilho que inicia o fluxo (ex: recebimento de webhook ou cron/agendamento) enquanto os Action Nodes executam tarefas sequenciais (ex: enviar mensagem no Telegram ou salvar banco de dados).
- **Aprendizado / Troubleshooting:**  
  A primeira resposta foi abstrata. Ao pedir *"dê um exemplo real de fluxo usando ambos"*, a IA gerou um cenário prático (Receber formulário → Tratar dados → Enviar e-mail) facilitando a fixação.

### Prompt 2: Manipulação e Estrutura de Dados (JSON / Data Mapping)
- **Prompt Utilizado:**  
  `"Como o n8n lida com itens e dados em formato JSON? Resuma a lógica de passagem de dados de um nó para outro em 3 tópicos diretos."`
- **Resultado da IA:**  
  A IA explicou: (1) Cada nó recebe um array de objetos JSON; (2) As expressões utilizam a sintaxe `$json` para acessar campos; (3) Se um nó retornar múltiplos itens, os nós seguintes serão executados para cada item por padrão.
- **Aprendizado / Troubleshooting:**  
  Por ser um tema técnico, o retorno inicial trouxe código complexo. Restringir a resposta a *"3 tópicos diretos focado na lógica"* ajudou a criar uma explicação mais didática.

### Prompt 3: Resolução de Erros e Boas Práticas (Troubleshooting)
- **Prompt Utilizado:**  
  `"Se uma requisição HTTP Request falhar dentro de um workflow do n8n, quais são as estratégias recomendadas na documentação para tratar o erro sem interromper todo o fluxo?"`
- **Resultado da IA:**  
  O NotebookLM listou o uso da opção *Continue On Fail*, uso do nó *Error Trigger* para captura global e a separação em *Sub-workflows*.
- **Aprendizado / Troubleshooting:**  
  O NotebookLM tendeu a omitir o nó de retentativas. Foi necessário fazer um prompt de acompanhamento: *"E como funcionam as retentativas automáticas (Retry on Fail) nas configurações do próprio nó?"*.

---

## 📖 4. Miniguia de Estudo (Entrega Final)

### 4.1. Resumo Estruturado do Assunto

1. **O que é o n8n?**  
   Uma ferramenta de automação de workflows *fair-code* baseada em nós (*nodes*), focada em conectar serviços web, APIs e rotinas com pouca ou nenhuma necessidade de código tradicional.

2. **Anatomia de um Workflow no n8n:**
   - **Trigger (Gatilho):** O evento que dispara a execução (ex: Horário agendado, Webhook recebido, Novo e-mail).
   - **Nodes de Ação:** Executam operações (ex: HTTP Request, Google Sheets, Slack, OpenAI).
   - **Nodes de Controle de Fluxo:** Direcionam os dados (ex: `If`, `Switch`, `Merge`, `Loop`).

3. **Automação no Dia a Dia:**
   - Coleta automática de leads de formulários e envio para CRM/Planilhas.
   - Notificações automáticas em canais de equipe (Slack/Discord/Telegram).
   - Leitura de e-mails, extração de anexos e organização em nuvem.
   - Chamadas a APIs de Inteligência Artificial para resumos e classificação automatizada de texto.

---

### 4.2. Glossário de Conceitos Aprendidos

| Termo | Definição Rápida |
| :--- | :--- |
| **Workflow** | Sequência de passos (nós) conectados que realizam um processo automatizado completo. |
| **Trigger** | Nó inicial de um fluxo que escuta um evento ou executa em intervalos programados. |
| **Webhook** | Método de comunicação HTTP em tempo real entre dois sistemas para disparar um evento. |
| **JSON (JavaScript Object Notation)** | Formato leve de troca de dados utilizado internamente pelo n8n entre os nós. |
| **Data Mapping** | Ato de arrastar ou mapear variáveis do nó anterior (`$json["campo"]`) para o nó seguinte. |
| **Error Trigger** | Nó especial ativado automaticamente quando ocorre uma falha não tratada em qualquer ponto do fluxo. |

---

### 4.3. Prompts Reutilizáveis para Estudo e Aplicação no n8n

Estes prompts foram desenvolvidos para você colar no NotebookLM sempre que estiver estudando ou construindo um novo fluxo:

#### 🔹 1. Desenhista de Arquitetura de Workflow
```text
Atue como um arquiteto de automação n8n. Quero automatizar a seguinte rotina: [DESCREVA SUA ROTINA AQUI].
Com base nos documentos, liste passo a passo a sequência exata de nós (Triggers, Ações e Lógica) necessários para construir este fluxo.
