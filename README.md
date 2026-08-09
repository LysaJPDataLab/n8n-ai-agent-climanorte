# Agente de Suporte a Orçamentos com IA (n8n)

Este repositório contém o fluxo de automação desenvolvido no n8n para a **ClimaNorte Refrigeração**. O objetivo do projeto é utilizar Inteligência Artificial para ler e-mails de solicitação de orçamento, extrair informações obrigatórias, calcular propostas comerciais e estruturar os dados em uma planilha de controle.

## 🚀 Como o Fluxo Funciona

A automação é dividida nas seguintes etapas:
1. **Gatilho (Gmail):** Monitora a caixa de entrada por e-mails com o assunto "Solicitação de Orçamento".
2. **Processamento (AI Agent - Gemini):** Analisa o corpo do e-mail em busca de 5 informações obrigatórias (Localização, CEP, Qtd. de Máquinas, Tipo de Serviço e Data Proposta).
3. **Validação (Nó IF):**
   * **Caminho True:** Se todos os dados estiverem presentes, o agente calcula o valor do serviço baseado em regras de negócio (deslocamento, urgência e tipo de cliente), preenche uma nova linha no Google Sheets e cria um rascunho de e-mail com a proposta comercial.
   * **Caminho False:** Se faltarem dados, o agente cria um rascunho de e-mail solicitando ao cliente exatamente as informações que ficaram pendentes.

## 🛠️ Tecnologias Utilizadas
* **n8n:** Orquestração do fluxo e integração de sistemas.
* **Google Gemini:** Modelo de IA para análise de linguagem natural e estruturação de dados (JSON).
* **Google Workspace:** Gatilhos e ações no Gmail e Google Sheets.

## 📁 Como utilizar este fluxo
1. Clone este repositório ou baixe o arquivo `.json`.
2. No seu ambiente n8n, vá em *Workflows*, clique nos três pontos no canto superior direito e selecione **Import from File**.
3. Selecione o arquivo JSON deste repositório.
4. Configure as suas próprias credenciais para os nós do Google (Gmail e Sheets) e para o modelo de IA.
5. Ajuste a URL da planilha no nó *Append row in sheet*.
