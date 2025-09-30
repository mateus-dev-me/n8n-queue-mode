# N8N Queue Mode

> Uma configuração escalável e pronta para produção do n8n utilizando Queue Mode com Docker, Redis e PostgreSQL.

## 🚀 Visão Geral

Este repositório fornece uma configuração completa para executar o n8n em modo de fila (Queue Mode), permitindo a execução de workflows em segundo plano de forma escalável. Ideal para ambientes de produção que exigem alta disponibilidade e processamento eficiente de tarefas.

## 🛠️ Arquitetura

* **n8n Main**: Interface principal e API.
* **n8n Worker(s)**: Execução de workflows em segundo plano.
* **n8n Webhook(s)**: Recebe chamadas externas e dispara workflows via API, permitindo integração com outros serviços.
* **Redis**: Gerenciamento de filas de execução.
* **PostgreSQL**: Armazenamento de dados persistentes.

## 📁 Estrutura do Projeto

```plaintext
n8n-queue-mode/
├── .env.example          # Variáveis de ambiente de exemplo
├── docker-compose.yml    # Configuração do Docker Compose
├── docker-swarm.yml      # Definições de serviços para Docker Swarm
├── Makefile              # Automação de tarefas
└── .gitignore            # Arquivos a serem ignorados pelo Git
```

## ⚙️ Pré-requisitos

* Docker e Docker Compose instalados.
* Redis e PostgreSQL em execução (configurados no `docker-compose.yml`).

## 🚀 Instalação Rápida

1. Clone este repositório:

   ```bash
   git clone https://github.com/mateus-dev-me/n8n-queue-mode.git
   cd n8n-queue-mode
   ```

2. Copie o arquivo de variáveis de ambiente:

   ```bash
   cp .env.example .env
   ```

3. Edite o arquivo `.env` com suas configurações específicas.

4. Inicie os serviços:

   ```bash
   docker-compose up -d
   ```

5. Acesse a interface do n8n em [http://localhost:5678](http://localhost:5678).

## 🔧 Configuração

* **Modo de Execução**: Defina `EXECUTIONS_MODE=queue` no arquivo `.env`.
* **Conexão com Redis**: Configure `QUEUE_BULL_REDIS_HOST=redis` para apontar para o serviço Redis.
* **Saúde da Fila**: Ative verificações de saúde com `QUEUE_HEALTH_CHECK_ACTIVE=true`.

## 🧪 Testes e Escalabilidade

* **Escalabilidade Horizontal**: Utilize Docker Swarm para escalar os workers conforme necessário.
* **Testes Locais**: Execute `docker-compose up` para testes em ambiente local.
