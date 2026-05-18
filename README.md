<div align="center"> 
<img scr=<img width="1670" height="887" alt="Image" src="https://github.com/user-attachments/assets/0fcc34ea-3ca8-40ef-a016-3461e541c155" width="400px" />
<div/>       
# 🤖 AI Bot — Chatbot Inteligente com n8n + Google Sheets + Telegram

> Automação criada no n8n que integra um assistente de IA ao Telegram, utilizando Google Sheets como base de conhecimento dinâmica.

---

## 📋 Sobre o Projeto

O **NOLA AI Bot** é um chatbot inteligente desenvolvido para atendimento ao cliente de um restaurante, capaz de responder perguntas sobre cardápio, estoque, procedimentos operacionais, dúvidas frequentes e histórico de vendas — tudo em tempo real, direto pelo Telegram.

Qualquer atualização feita no Google Sheets reflete automaticamente nas respostas do bot, sem necessidade de reprogramação.

---
<div align="left">
       
## 🚀 Funcionalidades

- 🍔 **Cardápio completo** — preços, ingredientes, alergênicos e disponibilidade no delivery
- 📦 **Estoque** — consulta de ingredientes disponíveis e status em tempo real
- 📋 **SOPs** — procedimentos operacionais acessíveis via chat
- ❓ **FAQ** — respostas automáticas para perguntas frequentes
- 📊 **Vendas** — produtos mais vendidos, receita por canal e últimos pedidos
</div> 

---

## 🛠️ Tecnologias Utilizadas

| Ferramenta | Função |
|---|---|
| [n8n](https://n8n.io) | Orquestração do fluxo de automação |
| [Google Sheets](https://sheets.google.com) | Base de conhecimento dinâmica |
| [Telegram Bot API](https://core.telegram.org/bots) | Canal de atendimento ao cliente |
| [Google Gemini](https://aistudio.google.com) | Modelo de linguagem para geração de respostas |
| [Claude (Anthropic)](https://claude.ai) | Apoio na construção dos prompts e código |

---
<div align="center">

## 🔄 Fluxo da Automação

```
Telegram Trigger
       ↓
5x Google Sheets (produtos, estoque, sops, faq, vendas)
       ↓
Merge (unifica os dados)
       ↓
Code JavaScript (formata o contexto)
       ↓
AI Agent + Google Gemini (gera a resposta)
       ↓
Conversation Memory (armazenamento do histórico de conversação)
       ↓
Send Telegram Message
```
<div/>
       
---
<div align="left">

## 📁 Estrutura da Base de Dados (Google Sheets)

```
📊 produtos   → SKU, nome, categoria, preço, ingredientes, alergênicos
📦 estoque    → ingrediente, quantidade, unidade, status
📋 sops       → id, categoria, pergunta, resposta
❓ faq        → id, pergunta, resposta
📈 vendas     → pedido_id, produto, qtd, total, canal, forma_pagamento
```
<div/>
---

## ⚙️ Como Configurar

### Pré-requisitos
- Conta no [n8n Cloud](https://n8n.io) ou instância própria
- Conta Google com Google Sheets
- Bot criado no Telegram via [@BotFather](https://t.me/BotFather)
- API Key do [Google AI Studio](https://aistudio.google.com/app/apikey)

### Passo a Passo

**1. Clone o repositório**
```bash
git clone https://github.com/alessandrodevbp/Automacao_N8N_Chat_Bot_IA.git
```
**2. Importe o workflow no n8n**
- Acesse seu n8n
- Vá em **Workflows → Import**
- Selecione o arquivo `workflow.json`

**3. Configure as credenciais**
- Google Sheets OAuth2
- Telegram Bot Token
- Google Gemini API Key

**4. Aponte para sua planilha**
- Em cada nó Google Sheets, selecione sua planilha
- Configure o nome de cada aba corretamente

**5. Ative o workflow**
- Clique em **Publish**
- Teste enviando uma mensagem para o bot no Telegram

---

## 💬 Prompt do Agente

```
Você é um assistente inteligente da NOLA especializado em food service.
Use APENAS as informações da base de dados recebida abaixo para responder.
Se não encontrar a resposta, informe claramente sem inventar.
Responda em texto simples, sem asteriscos, negrito ou qualquer formatação markdown.
Responda de forma clara, profissional e objetiva.

=== BASE DE DADOS NOLA ===
{{ $json.contexto }}

=== PERGUNTA DO CLIENTE ===
{{ $('Telegram Trigger').item.json.message.text }}
```

---

## 💡 Casos de Uso em Customer Success

- Redução de chamados repetitivos sobre produtos e preços
- Onboarding mais rápido de novos colaboradores
- Acesso instantâneo a procedimentos operacionais
- Atendimento 24/7 sem necessidade de agente humano
- Consulta de dados de vendas em tempo real

---

## 🤝 Ferramentas de IA Utilizadas como Apoio

- **Google Gemini** (gemini-1.5-flash) — modelo principal do bot
- **Claude (Anthropic)** — apoio na construção do código, prompts e resolução de erros

---

## 📄 Licença

Este projeto foi desenvolvido como demonstração técnica de automação com IA aplicada a Customer Success.

---

*Desenvolvido com n8n + Google Sheets + Telegram + Google Gemini*
