# 📅 Cronograma TCC — Cadê Meu Pet

**Prazo de entrega (Versão Preliminar):** 19/06/2026  
**Tempo disponível:** 4 semanas

---

## Semana 1 — 20/05 a 26/05 · Backend: endpoints faltantes

| Dia | Tarefa |
|-----|--------|
| Ter 20/05 | `DELETE /pets/{id}` + `PUT /pets/{id}` |
| Qua 21/05 | `PATCH /collars/{id}/status` (ativar/desativar coleira) |
| Qui 22/05 | `GET /collars` + `GET /collars/{id}` |
| Sex 23/05 | Endpoint de localização GPS — `POST /collars/{id}/location` + `GET /collars/{id}/location` |
| Sáb 24/05 | QR Code: geração por pet + endpoint público de leitura |
| Dom 25/05 | Buffer — testes manuais dos endpoints (Postman) |

---

## Semana 2 — 27/05 a 02/06 · Frontend: integração real + páginas faltantes

| Dia | Tarefa |
|-----|--------|
| Ter 27/05 | Modal de **Cadastrar Pet** (formulário + integração `POST /pets`) |
| Qua 28/05 | Integrar **Remover pet** (`DELETE /pets/{id}`) + toggle coleira (`PATCH /collars/{id}/status`) |
| Qui 29/05 | Página `/collars` — listagem de coleiras com status |
| Sex 30/05 | Mapa com localização real vinda da API |
| Sáb 31/05 | Página `/about` |
| Dom 01/06 | Página de detalhes do pet (`/pets/{id}`) — rota "Ver mais" |

---

## Semana 3 — 03/06 a 09/06 · Monografia: capítulos técnicos

| Dia | Tarefa |
|-----|--------|
| Ter 03/06 | **Cap. 2 — Referencial Teórico:** IoT, GPS, WiFi Positioning, rastreamento de animais |
| Qua 04/06 | **Cap. 3 — Trabalhos Relacionados:** apps similares e comparativo |
| Qui 05/06 | **Cap. 4 — Proposta:** arquitetura geral, diagrama de casos de uso, modelo de dados |
| Sex 06/06 | **Cap. 5 — Desenvolvimento Backend:** Spring Boot, endpoints, JWT, banco de dados |
| Sáb 07/06 | **Cap. 5 — Desenvolvimento Frontend:** React, atomic design, telas |
| Dom 08/06 | **Cap. 5 — Hardware:** visão geral e planejamento (versão preliminar) |

---

## Semana 4 — 10/06 a 16/06 · Monografia: fechamento e revisão

| Dia | Tarefa |
|-----|--------|
| Ter 10/06 | **Cap. 6 — Resultados:** prints das telas, fluxos funcionando, diagramas de sequência |
| Qua 11/06 | **Cap. 7 — Conclusão** + trabalhos futuros (hardware, notificações, mobile) |
| Qui 12/06 | **Referências** + normalização ABNT |
| Sex 13/06 | Revisão completa da monografia |
| Sáb 14/06 | Ajustes finais de texto e formatação |
| Dom 15/06 | Buffer |

---

## 17–19/06 · Entrega

- Revisão final com orientador
- Submissão da Versão Preliminar do Texto

---

## Estrutura da Monografia

| # | Capítulo | Status |
|---|----------|--------|
| 1 | Introdução | ✅ Feito |
| 2 | Referencial Teórico | ⬜ Pendente |
| 3 | Trabalhos Relacionados | ⬜ Pendente |
| 4 | Proposta / Metodologia | ⬜ Pendente |
| 5 | Desenvolvimento | ⬜ Pendente |
| 6 | Resultados | ⬜ Pendente |
| 7 | Conclusão | ⬜ Pendente |
| — | Referências | ⬜ Pendente |

---

## Stack do Projeto

| Camada | Tecnologia |
|--------|-----------|
| Backend | Java 17 + Spring Boot 3.4.5 |
| Banco de dados | PostgreSQL 14 + Flyway |
| Cache | Redis |
| Auth | JWT + Spring Security |
| Frontend | React 19 + React Bootstrap |
| Mapa | React Leaflet |
| Hardware | IoT (fase futura) |
