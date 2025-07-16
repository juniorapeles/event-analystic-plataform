# 📊 Realtime Event Analytics Platform

Plataforma distribuída de monitoramento de eventos em tempo real, com arquitetura orientada a eventos, microserviços, e comunicação via Kafka. Ideal para uso em casos como e-commerce, blogs de alto tráfego, sistemas IoT e monitoramento de logs.

---

## 🚀 Tecnologias Utilizadas

- **Java 17 / Spring Boot**
- **Node.js**
- **Apache Kafka**
- **MongoDB**
- **Redis**
- **PostgreSQL / MySQL**
- **Docker e Docker Compose**
- **JWT (autenticação)**
- **WebSockets / REST APIs**
- **Swagger (documentação)**

---

## 🧱 Estrutura de Microserviços

| Serviço             | Descrição |
|---------------------|-----------|
| `user-service`      | Cadastro e autenticação de usuários com JWT |
| `event-collector`   | Recebe eventos externos e publica no Kafka |
| `analytics-service` | Processa os eventos do Kafka e agrega os dados |
| `dashboard-frontend`| Painel em tempo real com dados atualizados |
| `cache-service`     | Redis para dados em tempo real |
| `database`          | MongoDB (eventos), PostgreSQL (usuários) |

---

## 📦 Como Rodar Localmente

### Pré-requisitos:
- Docker e Docker Compose instalados
- Java 17
- Node.js 18+

```bash
# Clone o repositório
git clone https://github.com/seu-usuario/event-analytics-platform.git
cd event-analytics-platform

# Suba os serviços com Docker
docker-compose up -d


´´´
[ Usuário ]
     │
     ▼
[Frontend Dashboard]
     │
     ▼                            ┌───────────────────────────────┐
[API Gateway (opcional)]────────▶│      User Service (Java)      │
     │                           └───────────────────────────────┘
     │                                       │
     ▼                                       ▼
[ Event Collector (Node.js) ] ─────▶ [ Kafka - Broker de Eventos ]
                                                │
                        ┌───────────────────────┴──────────────────────┐
                        ▼                                              ▼
        [ Analytics Service (Java ou Node.js) ]             [ Outros consumidores futuros ]
                │
                ├──▶ MongoDB (eventos brutos, logs)
                ├──▶ Redis (dados agregados)
                └──▶ PostgreSQL/MySQL (dados persistentes)

                                 ▼
                          [Dashboard Frontend]
                    (consulta APIs + WebSocket)

```