# 💾 Azure SQL Database - Configuração e Documentação (PaaS)

Este repositório documenta a experiência prática de configurar uma instância de banco de dados relacional (SQL) na plataforma Microsoft Azure. O objetivo foi consolidar os conhecimentos sobre Modelos de Serviço em Nuvem e Gerenciamento de Recursos.

---

## 1. 🎯 Análise e Objetivo (O Foco em PaaS)

O processo de criação de uma Instância Gerenciada de SQL do Azure é um exemplo clássico de **PaaS (Platform as a Service)**.

* **Por quê?** Nós, como clientes, não gerenciamos o Sistema Operacional (Windows/Linux) ou o software de banco de dados (SQL Server Engine). A Microsoft cuida de tudo isso. Nosso trabalho começa e termina na **gestão dos dados, usuários e regras de acesso** (Firewall).
* **Vantagem Financeira:** Este modelo nos permite desfrutar dos benefícios do **OpEx** (Custo Operacional), pois pagamos apenas pelo serviço de banco de dados ativo, sem gastar tempo ou capital na manutenção de hardware (CapEx).

## 2. 🛠️ Processo de Configuração (Checklist Prático)

As etapas abaixo representam as decisões de design tomadas no portal do Azure:

### 2.1. Organização e Infraestrutura (IaaS herdado)

| Decisão | Detalhe | Conceito Aplicado |
| :--- | :--- | :--- |
| **Grupo de Recursos** | `rg-banco-dio-sql-lab` | Contêiner lógico para agrupar todos os ativos (servidor, rede, disco) para fácil gerenciamento e monitoramento. |
| **Nome do Servidor** | `server-grupodionuvem` | Nome único para o servidor SQL na nuvem. |
| **Tamanho da Instância** | `Basic` ou `Standard` | Escolha dos recursos de CPU/RAM (Decisão de OpEx). |

### 2.2. Segurança e Conectividade (O Ponto de Controle)

| Configuração | Descrição | Pilar de Segurança |
| :--- | :--- | :--- |
| **Autenticação** | SQL Login ou Azure AD | Definir as credenciais para o administrador do banco de dados. |
| **Regras de Firewall** | Permissão de IP Cliente | É o principal ponto de **Responsabilidade Compartilhada**. Eu sou obrigado a dizer ao Azure qual IP (o meu) pode acessar o servidor. O Azure protege o servidor de todos os outros IPs. |
| **Nome do Database** | `db_financeiro` | O nome do banco de dados principal criado na instância. |

## 3. 📝 Notas e Dicas

* **Conexão String:** Após a criação, a URL de conexão é gerada. Este endereço é o **Endpoint** da nossa aplicação para acessar o banco de dados.
* **DBMS:** O Azure está rodando o software **SQL Server** como nosso SGBD.
* **Próxima Etapa:** Após a configuração inicial, o próximo passo seria usar ferramentas como o **DBeaver** ou o **SQL Server Management Studio (SSMS)** para conectar à instância, criar as tabelas (DDL) e iniciar a manipulação de dados (DML).
