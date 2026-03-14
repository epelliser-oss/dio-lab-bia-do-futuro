# 🗄️ Base de Conhecimento

Para que a BIA não "alucine" e forneça respostas precisas, ela utiliza uma base de dados mockados (simulados) organizada da seguinte forma:

## 1. Estrutura dos Dados

| Arquivo | Formato | Descrição e Uso |
| :--- | :--- | :--- |
| `transacoes.csv` | CSV | Contém o histórico de compras, datas e categorias. Essencial para a BIA calcular o saldo e identificar padrões de consumo. |
| `perfil_investidor.json` | JSON | Define se o cliente é Conservador, Moderado ou Arrojado. É o "filtro de segurança" para recomendações. |
| `produtos_financeiros.json` | JSON | Catálogo de investimentos disponíveis no banco, com taxas e prazos. |
| `historico_atendimento.csv` | CSV | Registros de interações passadas, permitindo que a BIA tenha memória sobre problemas anteriores. |

## 2. Estratégia de Recuperação (RAG)
O agente não tenta "adivinhar" o saldo. O fluxo técnico seguido é:
1. O sistema lê o arquivo `transacoes.csv`.
2. Realiza a soma de `Entradas - Saídas`.
3. Cruza o resultado com o `perfil_investidor.json`.
4. Gera a resposta baseada exclusivamente nesse cruzamento.

## 3. Atualização da Base
Embora os dados sejam estáticos para este protótipo, a arquitetura foi desenhada para suportar atualizações em tempo real via API, permitindo que cada nova transação do cliente alimente instantaneamente o contexto da IA.
