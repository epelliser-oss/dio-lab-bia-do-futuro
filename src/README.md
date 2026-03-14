import streamlit as st

import pandas as pd

import json

# 1. Configuração da Página
st.set_page_config(page_title="BIA - Consultora Proativa", page_icon="🤖")

# 2. Carregar a "Base de Conhecimento" (Dados do seu repositório)
def carregar_dados():
    try:
        transacoes = pd.read_csv('data/transacoes.csv')
        with open('data/perfil_investidor.json', 'r') as f:
            perfil = json.load(f)
        return transacoes, perfil
    except:
        st.error("Erro ao carregar os dados. Verifique se os arquivos estão na pasta /data.")
        return None, None

df_transacoes, perfil_usuario = carregar_dados()

# 3. Interface do Usuário
st.title("🤖 BIA - Consultora Proativa Bradesco")
st.markdown("---")

# Barra lateral com informações do perfil (Base de Conhecimento)
if perfil_usuario:
    st.sidebar.header("Perfil do Cliente")
    st.sidebar.write(f"**Nome:** {perfil_usuario['nome']}")
    st.sidebar.write(f"**Perfil:** {perfil_usuario['tipo_perfil']}")

# 4. Lógica do Chat (Simulação de Integração com LLM)
if "messages" not in st.session_state:
    st.session_state.messages = []

# Exibir mensagens anteriores
for message in st.session_state.messages:
    with st.chat_message(message["role"]):
        st.markdown(message["content"])

# Campo de entrada do usuário
if prompt := st.chat_input("Como posso ajudar com suas finanças hoje?"):
    st.session_state.messages.append({"role": "user", "content": prompt})
    with st.chat_message("user"):
        st.markdown(prompt)

    # Simulação de resposta do Agente baseada nos dados
    with st.chat_message("assistant"):
        if "saldo" in prompt.lower():
            # Exemplo de lógica usando o Pandas (Excel no Python)
            saldo = df_transacoes['valor'].sum()
            resposta = f"Seu saldo atual, baseado nas transações recentes, é de R$ {saldo:.2f}."
        elif "investir" in prompt.lower():
            perfil = perfil_usuario['tipo_perfil']
            resposta = f"Vi que seu perfil é {perfil}. Para você, recomendo opções de Baixo Risco como CDB."
        else:
            resposta = "Olá! Sou a BIA. Posso analisar seus gastos ou sugerir investimentos com base no seu perfil. O que prefere?"
        
        st.markdown(resposta)
        st.session_state.messages.append({"role": "assistant", "content": resposta})
