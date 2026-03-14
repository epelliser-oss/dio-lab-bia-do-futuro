# 🤖 BIA: Consultora Financeira Proativa (GenAI)

Este repositório contém o projeto final desenvolvido para o Bootcamp **Bradesco - GenAI & Dados** da plataforma DIO. O objetivo é evoluir a assistente virtual BIA de um modelo reativo para um **Agente Inteligente Proativo**.

## 🎯 Caso de Uso
A solução foca em transformar a experiência do cliente Bradesco, saindo da simples consulta de extrato para uma consultoria financeira automatizada. O agente analisa o histórico de transações e o perfil de risco para sugerir metas de economia e investimentos adequados, utilizando técnicas de **IA Generativa**.

## 🛠️ Tecnologias Utilizadas
- **Python**: Linguagem base para o processamento de dados.
- **Pandas**: Biblioteca utilizada para manipulação e análise dos arquivos CSV e JSON (Base de Conhecimento).
- **Streamlit**: Framework utilizado para criar a interface de chatbot interativa.
- **Engenharia de Prompt**: Implementação de *System Prompts* rigorosos para garantir respostas seguras (Anti-alucinação).

## 📂 Estrutura do Projeto
- `data/`: Contém os dados simulados de transações e perfis de clientes.
- `docs/`: Documentação detalhada sobre a arquitetura, prompts e métricas.
- `src/`: Protótipo da aplicação funcional (`app.py`).

## 🚀 Como Funciona a Solução
O agente utiliza a técnica de **RAG (Retrieval-Augmented Generation)**:
1. O sistema lê as transações reais do cliente em `transacoes.csv`.
2. Cruza esses dados com o `perfil_investidor.json`.
3. A IA gera insights personalizados, como: *"Notei que seu gasto com lazer aumentou, que tal investir R$ 200,00 no CDB para sua reserva de emergência?"*

## 🛡️ Segurança e Confiabilidade
Para o setor bancário, a precisão é fundamental. Este projeto implementa:
- **Grounding**: Respostas ancoradas estritamente nos dados fornecidos.
- **Filtro de Perfil**: Bloqueio de sugestões de alto risco para investidores conservadores.
- **Privacidade**: Simulação de dados para garantir a integridade de informações sensíveis.

---
**Autor:** Eduardo Filho
**Bootcamp:** Bradesco - GenAI & Dados (Hashtag + DIO)
