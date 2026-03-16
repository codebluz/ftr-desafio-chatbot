# 🌦️ Sentinela do Clima - Telegram AI Agent

Este projeto é um assistente meteorológico inteligente integrado ao Telegram, desenvolvido como parte de um desafio técnico para demonstrar a migração de fluxos tradicionais para arquiteturas baseadas em **Agentes de IA**.

## 🚀 Sobre o Projeto
O agente processa mensagens em linguagem natural, extrai entidades geográficas brasileiras e consome dados da API OpenWeather. O diferencial está na camada de inteligência que utiliza **LangChain** dentro do **n8n** para garantir que a interação seja humana, variável e tecnicamente precisa.

## 🛠️ Stack Tecnológica
* **Orquestração:** [n8n](https://n8n.io/) 
* **Modelos de Linguagem (LLM):** Groq (GPT-OSS).
* **Interface:** Telegram Bot API.
* **Dados:** OpenWeather API.

## 🧠 Arquitetura do Workflow
O workflow segue uma lógica de processamento em camadas para otimizar o uso de tokens e garantir a precisão:

1.  **Information Extractor:** Um nó de extração que valida se a entrada do usuário contém uma cidade e um estado brasileiro (UF). Ele limpa os dados e prepara a query para a API.
2.  **Weather Integration:** Chamada via HTTP Request à API OpenWeather para obter dados climáticos reais em formato métrico.
3.  **AI Agent (O Sentinela):** O agente final que recebe a temperatura bruta, realiza o arredondamento matemático e gera uma resposta amigável e variável.

## 📋 Regras do Agente
O prompt do sistema foi configurado com as seguintes diretrizes:
* **Arredondamento:** Temperaturas decimais (ex: 24.7°C) são convertidas para o inteiro mais próximo (25°C).
* **Variabilidade:** O bot alterna entre diferentes saudações e tons de voz para evitar repetitividade.
* **Identidade Visual:** Uso obrigatório de emojis que simbolizam o estado atual do tempo.
* **Tratamento de Erros:** Fluxos de exceção amigáveis para cidades não encontradas ou falhas de conexão.

## 📂 Como Utilizar
1. Importe o arquivo `workflow-chatbot-telegram.json` no seu n8n.
2. Configure as credenciais para:
   * Telegram API
   * Groq API
   * OpenWeather API
3. Ative o workflow e envie o nome de uma cidade e estado (ex: "Natal RN") para o seu bot.

---
