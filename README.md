# GOVPSI360 — Automação de Riscos Psicossociais (NR-1)

O **GOVPSI360** é uma solução *end-to-end* desenvolvida para automatizar a receção, triagem, armazenamento e visualização de relatos e denúncias sobre riscos psicossociais no ambiente de trabalho, em total conformidade com as diretrizes da **NR-1**.

---

## 🏗️ Arquitetura da Solução

O fluxo de dados integra automação no **n8n**, base de dados na nuvem **Azure MySQL** e relatórios executivos no **Power BI**:

1. **Entrada de Dados (Webhook / n8n):** Recebe os relatos de forma anónima ou identificada, processando a criticidade e categorização do risco.
2. **Armazenamento em Nuvem (Azure MySQL Flexible Server):**
   - Instância: `mysql-dio-powerbi-marcos2`
   - Base de Dados: `govpsi360_db`
   - Tabela Principal: `relatos_nr1`
3. **Consumo e Inteligência (Power BI):** Ligação direta ao Azure MySQL para atualização contínua dos indicadores executivos e acompanhamento pelo Comité de Ética.

---

## 🚀 Migração de Infraestrutura (Local → Azure Cloud)

Inicialmente desenvolvido em ambiente local (`localhost` via Docker), o projeto passou por um processo de migração para infraestrutura em nuvem, garantindo alta disponibilidade, segurança e escalabilidade.

### Etapas da Migração:
1. **Provisionamento no Azure:** Configuração do banco de dados MySQL Flexible Server e ajuste de regras de firewall/IP.
2. **Redirecionamento do Pipeline (n8n):** Atualização dos nós de inserção de dados para gravar no *endpoint* do Azure.
3. **Validação de Dados:** Homologação via **MySQL Workbench** confirmando a integridade dos esquemas e registos.
4. **Atualização do Dashboard:** Repontamento da origem de dados no **Power Query** (`Data Source Settings`) para o servidor de produção no Azure.

---

## 📊 Dashboard Executivo (Power BI)

O painel fornece visão panorâmica e acionável para a gestão de pessoas e conformidade jurídica:

- **Total de Relatos & Relatos Críticos:** Métricas em tempo real para tomada de decisão ágil.
- **Distribuição por Fator de Risco:** Organização do Trabalho, Ambiente Físico, Relações Interpessoais, etc.
- **Categorização por Criticidade:** Classificação automática (Alta, Média, Baixa) com direcionamento para o Comité de Ética.
- **Tabela Operacional de Detalhes:** Acompanhamento individualizado por protocolo (`PROT-YYYY-XXX`).

---

## 🛠️ Tecnologias Utilizadas

- **n8n** (Orquestração de Workflows e Webhooks)
- **Azure MySQL Flexible Server** (Base de Dados Relacional na Nuvem)
- **Power BI Desktop & Power Query** (Visualização e Tratamento de Dados)
- **MySQL Workbench** (Gestão e Administração BD)
- **SQL / DAX** (Consultas e Métricas)

---

## 🔒 Conformidade e Segurança (NR-1)

- Criptografia e acesso restrito por credenciais administrativas no Azure.
- Tratamento confidencial e anónimo de relatos conforme os requisitos de proteção de dados e governança de saúde ocupacional.
