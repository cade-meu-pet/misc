# Contexto do Projeto "Cadê Meu Pet" — TCC

> Este documento é um mapa técnico e acadêmico do projeto para uso como contexto em conversas no Overleaf. Contém a stack, arquitetura, funcionalidades implementadas, estrutura da monografia e trechos já escritos.

---

## 1. Identificação

| Campo | Valor |
|---|---|
| **Projeto** | Cadê Meu Pet |
| **Tipo** | Trabalho de Conclusão de Curso (TCC) |
| **Prazo** | 19/06/2026 (versão preliminar) |
| **Repositórios** | `cade-meu-pet-backend`, `cade-meu-pet-frontend`, `cade-meu-pet-misc` |

---

## 2. Resumo do Projeto

Sistema integrado para rastreamento de animais de estimação perdidos, combinando:

- **Hardware (fase futura):** Coleira inteligente com tag ID físico, módulo de comunicação sem fio e QR Code fixado
- **Backend:** API REST em Java/Spring Boot, com autenticação JWT, banco PostgreSQL e cache Redis
- **Frontend:** Aplicação web em React, com mapas interativos (Leaflet/OpenStreetMap) e página pública para encontradores

O diferencial do projeto é a **funcionalidade sem hardware ativo**: qualquer pessoa que encontrar um pet pode escanear o QR Code da coleira, acessar informações do animal e do tutor, e compartilhar sua localização — sem necessidade de app, cadastro ou módulo eletrônico ativo.

---

## 3. Pergunta de Pesquisa

> Como podemos conciliar inovações tecnológicas com viabilidade prática, de modo a garantir que dispositivos de rastreamento se tornem, de fato, parte do cotidiano dos tutores e contribuam efetivamente para a redução do número de animais perdidos em ambientes urbanos?

---

## 4. Objetivos

### 4.1 Objetivo Geral

Desenvolver uma solução integrada, composta por um dispositivo de hardware de rastreamento (coleira inteligente com tag ID) e um software multiplataforma (aplicação web), com interfaces que proporcionem boa experiência ao tutor e possibilitem a localização e o monitoramento de pets em tempo real.

### 4.2 Objetivos Específicos

**OE1 — Funcionalidade independente do hardware:**
O sistema deve operar mesmo sem o módulo eletrônico ativo. QR Codes físicos fixados na coleira permitem que terceiros compartilhem localização e identifiquem o pet, mantendo parte da funcionalidade de rastreamento.

**OE2 — Otimização do consumo de energia:**
A coleira deve empregar heurísticas para eficiência energética, evitando o uso contínuo de GPS. Alternativas como Wi-Fi Positioning System (WPS) reduzem o consumo ao estimar posição via redes Wi-Fi próximas.

**OE3 — Funcionalidade em longas distâncias:**
A solução deve fornecer localização em tempo real com alcance funcional de até 2.500 metros e precisão média de 100 metros, com otimização de consumo de dados.

---

## 5. Motivação e Contexto (Texto da Introdução)

O texto abaixo já foi escrito e revisado — é o Capítulo 1 da monografia:

> "A convivência com animais de estimação contribui significativamente para a qualidade de vida, promovendo sensações de felicidade, atenuando a solidão e favorecendo a saúde física e mental" — Giumelli & Santos (Univille).

Em 2024, estimou-se que o Brasil possui a **terceira maior população de pets do mundo**, com 150–160 milhões de animais. Com o crescimento expressivo desta população surgem novos desafios: aumento de animais perdidos, ausência de identificação e processos de reencontro longos e emocionalmente desgastantes.

Tecnologias existentes (microchips subcutâneos, Apple AirTag) têm adoção limitada por custo, infraestrutura necessária e falta de conhecimento. A **Lei nº 15.046/2024** instituiu o Cadastro Nacional de Animais Domésticos (banco de dados nacional com microchip, raça, vacinação, dados do tutor), mas sua implementação ainda é incipiente.

**Trabalhos relacionados relevantes:**
- *PetCare* — Igor de Carvalho Negócio (2020, UFRN): rastreamento via IoT e LoRaWAN
- Protótipo de rastreador — Daniel Assis Carneiro (2019, UTFPR): GPS e LoRa, baixo custo

Ambos enfrentaram **alcance limitado** e **alto consumo energético** — desafios que este projeto busca endereçar.

---

## 6. Stack Tecnológico

| Camada | Tecnologia | Versão |
|---|---|---|
| Backend | Java + Spring Boot | 17 / 3.4.5 |
| ORM | Spring Data JPA + Hibernate | — |
| Banco de dados | PostgreSQL | 14 |
| Migrations | Flyway | — |
| Cache | Redis | — |
| Autenticação | JWT (Auth0) + Spring Security | — |
| Armazenamento | Cloudflare R2 (compatível S3) | — |
| Email | SMTP Gmail via Spring Mail | — |
| QR Code | Google ZXing | 3.5.3 |
| Build | Gradle | 8.x |
| Frontend | React | 19.1.0 |
| Roteamento | React Router DOM | 7.5.3 |
| UI | React Bootstrap + Bootstrap | 2.10.9 / 5.3.5 |
| Formulários | React Hook Form | 7.56.1 |
| HTTP Client | Axios | 1.9.0 |
| Mapas | React Leaflet + Leaflet | 5.0.0 / 1.9.4 |
| Notificações | React Toastify | 11.0.5 |
| Hardware (futuro) | IoT / ESP32 / LoRa / WPS | — |

---

## 7. Arquitetura do Sistema

### 7.1 Visão Geral

```
[Coleira Inteligente] ──GPS/WiFi──▶ [Backend API REST]
                                          │
[QR Code Físico] ──Escaneamento──▶ [Frontend Web] ◀──▶ [Tutor]
                                          │
                                   [PostgreSQL + Redis]
                                   [Cloudflare R2 (imagens)]
```

### 7.2 Backend — Padrão Arquitetural

Domain-Driven Design (DDD) com componentes organizados por domínio:

```
br.com.cade_meu_pet_backend/
├── domain/
│   ├── tutors/        # Entidade Tutor (UserDetails)
│   ├── pets/          # CRUD de Pets
│   ├── collars/       # Gestão de Coleiras
│   ├── locations/     # Histórico de Localização
│   ├── qrcode/        # Geração de QR Codes
│   ├── signup/        # Fluxo de Registro (com token por email)
│   ├── signin/        # Autenticação / JWT
│   └── shared/        # DTOs compartilhados
├── infra/
│   ├── security/      # SecurityFilter + CORS + BCrypt
│   ├── storage/       # Cloudflare R2
│   ├── email/         # SMTP + template HTML
│   ├── jwt/           # Geração e validação de tokens
│   ├── redis/         # Cache de tokens de confirmação
│   └── exceptions/    # Tratamento centralizado de erros
└── utils/             # AuthUtil, EmojiUtil
```

Cada domínio contém: `controller`, `service`, `dto`, `entity`, `repository`.

### 7.3 Frontend — Padrão Arquitetural

Atomic Design:

```
src/
├── components/
│   ├── atoms/       # PetButtonAtom, PetInputAtom, MapRouteAtom, ...
│   ├── molecules/   # PetCardMolecule, PetSigninFormMolecule, CollarLocationModalMolecule, ...
│   ├── organisms/   # HeaderSectionOrganism, PetListSectionOrganism, PetMapSectionOrganism, ...
│   └── templates/   # SigninTemplate, PetsTemplate, CollarsTemplate, ...
├── pages/           # SigninPage, SignupPage, PetPage, CollarPage, CollarPublicPage, AboutPage
├── contexts/        # GeolocationContext
├── hooks/           # useAuth, useSignin, useSignup, useSignupConfirmation
├── services/        # signinService, petService, collarService, publicPetService
└── utils/           # tokenUtils (decode/expiração de JWT), imageUrl (proxy R2)
```

---

## 8. Modelo de Dados

### Entidades e Relacionamentos

```
Tutors (1) ──── (N) Pets
                  └── (1) Collars (1) ──── (N) Locations
```

### 8.1 Tutors
| Campo | Tipo | Observação |
|---|---|---|
| id | SERIAL PK | |
| email | TEXT UNIQUE | |
| password | TEXT | BCrypt |
| first_name | TEXT | |
| last_name | TEXT | |
| phone | TEXT UNIQUE | |
| picture_url | TEXT | URL Cloudflare R2 |
| created_at / updated_at | TIMESTAMP | |

### 8.2 Collars (Coleiras)
| Campo | Tipo | Observação |
|---|---|---|
| id | SERIAL PK | |
| pet_id | INT FK | nullable |
| tag | TEXT UNIQUE | Tag físico impresso + QR Code |
| status | BOOLEAN | ativo/inativo |
| available_balance | NUMERIC(10,2) | saldo |

### 8.3 Pets
| Campo | Tipo | Observação |
|---|---|---|
| id | SERIAL PK | |
| tutor_id | INT FK | |
| collar_id | INT FK | |
| picture_url | VARCHAR(255) | |
| name | VARCHAR(255) | |
| age_range | ENUM | BABY, YOUNG, ADULT, SENIOR |
| species | ENUM | DOG, CAT, BIRD, OTHER |
| race | ENUM | SRD, PURE, MIXED |
| gender | ENUM | MALE, FEMALE |
| description | VARCHAR(500) | |

### 8.4 Locations (Histórico de Localização)
| Campo | Tipo | Observação |
|---|---|---|
| id | SERIAL PK | |
| collar_id | INT FK | |
| type | ENUM | COLLAR (GPS) ou QRCODE (escaneamento) |
| lat | FLOAT | |
| lon | FLOAT | |
| created_at | TIMESTAMP | |

---

## 9. Endpoints da API

### Públicos (sem autenticação)

| Método | Rota | Descrição |
|---|---|---|
| POST | `/public/signup` | Registrar novo tutor |
| POST | `/public/signup/confirmation` | Confirmar registro com token do email |
| POST | `/public/signin` | Login — retorna JWT |
| GET | `/public/pets/collar/{tag}` | Buscar pet pela tag da coleira (QR Code) |
| POST | `/public/collars/{tag}/locations` | Registrar localização via QR Code (tipo: QRCODE) |
| GET | `/public/qrcode/pets/{petId}` | Gerar QR Code do pet (requer header `x-key`) |

### Protegidos (requer Bearer JWT)

| Método | Rota | Descrição |
|---|---|---|
| POST | `/pets` | Criar pet (multipart: JSON + imagem) |
| GET | `/pets` | Listar pets do tutor autenticado |
| GET | `/pets/{id}` | Detalhar pet |
| PUT | `/pets/{id}` | Atualizar pet |
| DELETE | `/pets/{id}` | Deletar pet |
| GET | `/collars` | Listar coleiras do tutor |
| GET | `/collars/{id}` | Detalhar coleira |
| PATCH | `/collars/{id}/status` | Ativar/desativar coleira |
| POST | `/collars/{id}/locations` | Registrar localização GPS (tipo: COLLAR) |
| GET | `/collars/{id}/locations` | Histórico de localizações |

---

## 10. Telas e Fluxos do Frontend

### Telas

| Tela | Rota | Acesso | Descrição |
|---|---|---|---|
| Login | `/signin` | Público | Email + senha, retorna JWT |
| Cadastro | `/signup` | Público | 3 etapas: dados → credenciais → token do email |
| Pets | `/pets` | Privado | Grid de pets + mapa interativo + modais de CRUD |
| Coleiras | `/collars` | Privado | Tabela de coleiras, busca, toggle de status, localização |
| Pet Público | `/collar/:tag` | Público | Página para quem encontrou o pet via QR Code |
| Sobre | `/about` | Privado | Equipe e descrição do projeto (TCC) |

### Fluxo — QR Code (encontrador de pet)

```
1. Encontrador escaneia QR Code da coleira
2. Abre URL: /collar/{tag} no navegador
3. Frontend chama GET /public/pets/collar/{tag}
4. Exibe: foto, nome, espécie, raça, tutor, última localização
5. Browser solicita geolocalização do encontrador
6. Frontend envia POST /public/collars/{tag}/locations {lat, lon, type: "QRCODE"}
7. Botão de WhatsApp com mensagem pré-formatada para o tutor
```

### Fluxo — Signup

```
1. POST /public/signup (dados pessoais + credenciais)
2. Backend gera token aleatório → Redis (TTL: 3 min)
3. Email enviado com token
4. POST /public/signup/confirmation {token, email}
5. Backend cria Tutor (senha BCrypt) → gera JWT → limpa Redis
6. Frontend armazena JWT no localStorage → redireciona para /pets
```

---

## 11. Funcionalidades Implementadas

- [x] Autenticação JWT com BCrypt, sessão stateless
- [x] Cadastro em 3 etapas com confirmação por email (Redis TTL 3min)
- [x] CRUD completo de pets com upload de foto (Cloudflare R2)
- [x] Gerenciamento de coleiras (ativar/desativar, listar, detalhar)
- [x] Registro de localização via GPS (coleira) e via QR Code (encontrador)
- [x] Geração dinâmica de QR Code (ZXing, PNG 300×300px, URL da página pública)
- [x] Página pública para encontrador: dados do pet + mapa + WhatsApp
- [x] Mapa interativo com todos os pets do tutor (Leaflet + OpenStreetMap)
- [x] Cálculo de rota entre usuário e pet (OSRM)
- [x] Geolocalização do tutor via browser com Context API
- [x] Suporte a imagens HEIC (conversão automática no frontend)
- [x] Atomic Design no frontend (atoms → molecules → organisms → templates)

---

## 12. Integrações Externas

| Serviço | Finalidade |
|---|---|
| PostgreSQL 14 | Banco de dados principal |
| Redis | Cache de tokens temporários de cadastro (TTL 3 min) |
| Cloudflare R2 | Object storage para fotos dos pets (API compatível com S3) |
| SMTP Gmail | Envio de email com token de confirmação de conta |
| OpenStreetMap / Leaflet | Mapa no frontend (sem API key) |
| OSRM | Cálculo de rota entre usuário e localização do pet |
| Google ZXing | Geração de QR Code PNG no backend |

---

## 13. Estrutura da Monografia

| # | Capítulo | Status |
|---|---|---|
| 1 | Introdução | ✅ Concluído |
| 2 | Referencial Teórico | ⬜ Pendente |
| 3 | Trabalhos Relacionados | ⬜ Pendente |
| 4 | Proposta / Metodologia | ⬜ Pendente |
| 5 | Desenvolvimento | ⬜ Pendente |
| 6 | Resultados | ⬜ Pendente |
| 7 | Conclusão | ⬜ Pendente |
| — | Referências (ABNT) | ⬜ Pendente |

---

## 14. Sugestões de Conteúdo por Capítulo

### Cap. 2 — Referencial Teórico
Temas a cobrir:
- Internet das Coisas (IoT) — conceito, arquitetura, aplicações
- Protocolos de comunicação sem fio: LoRa, LoRaWAN, Wi-Fi, BLE
- Wi-Fi Positioning System (WPS) — princípio e APIs
- GPS — funcionamento, consumo energético, limitações indoor
- QR Codes — padrão, uso em identificação de objetos
- JWT e autenticação stateless em APIs REST
- Armazenamento em nuvem e object storage

### Cap. 3 — Trabalhos Relacionados
- **PetCare** (Igor de Carvalho Negócio, 2020, UFRN) — IoT + LoRaWAN
- **Rastreador GPS+LoRa** (Daniel Assis Carneiro, 2019, UTFPR) — baixo custo, bateria
- Apple AirTag — UWB, Find My network, privacidade, limitações
- Microchip subcutâneo — padrão ISO 11784/11785, infraestrutura de leitura
- Tabela comparativa: alcance, custo, precisão, dependência de infraestrutura

### Cap. 4 — Proposta / Metodologia
- Diagrama de arquitetura geral (hardware + backend + frontend)
- Diagrama de casos de uso (Tutor, Person, Admin)
- Modelo de dados (ER das 4 entidades)
- Decisões de projeto: por que Spring Boot, por que React, por que QR Code como fallback
- Metodologia de desenvolvimento: iterativo, repositórios separados por camada

### Cap. 5 — Desenvolvimento
- **Backend:** DDD, Spring Boot, endpoints REST, segurança JWT, Flyway, Redis, R2
- **Frontend:** Atomic Design, React 19, React Router v7, Leaflet, fluxos de telas
- **Hardware:** visão geral do protótipo planejado (ESP32/similar, módulo Wi-Fi, LoRa)

### Cap. 6 — Resultados
- Capturas de tela das telas implementadas
- Fluxos funcionando (cadastro → login → pet → QR Code → encontrador)
- Métricas: tempo de resposta da API, tamanho do bundle, performance Lighthouse

### Cap. 7 — Conclusão
- O que foi alcançado vs. objetivos específicos
- Trabalhos futuros: app mobile, notificações push, hardware real, painel admin

---

## 15. Referências Já Citadas na Introdução

- GIUMELLI, R. R.; SANTOS, C. P. dos. *A convivência com animais de estimação...* Univille. Disponível em: https://pepsic.bvsalud.org/pdf/rag/v22n1/v22n1a07.pdf
- AGÊNCIA SENADO. *Brasil tem terceira maior população pet do mundo.* 2024. Disponível em: https://www12.senado.leg.br/noticias/infomaterias/2024/12/brasil-tem-terceira-maior-populacao-pet-do-mundo-veja-os-projetos-do-senado-sobre-o-assunto
- BRASIL. *Lei nº 15.046, de 26 de novembro de 2024.* Institui o Cadastro Nacional de Animais Domésticos.
- NEGÓCIO, Igor de Carvalho. *PetCare.* UFRN, 2020. (rastreamento IoT + LoRaWAN)
- CARNEIRO, Daniel Assis. *Rastreador para pets com GPS e LoRa.* UTFPR, 2019.

---

## 16. Glossário Técnico

| Termo | Significado |
|---|---|
| JWT | JSON Web Token — token de autenticação stateless |
| DDD | Domain-Driven Design — organização de código por domínio de negócio |
| BCrypt | Algoritmo de hash para senhas |
| Flyway | Ferramenta de versionamento de banco de dados via SQL migrations |
| Redis | Banco de dados em memória, usado aqui como cache de tokens |
| R2 | Cloudflare R2 — object storage compatível com S3 (sem custo de egress) |
| ZXing | Biblioteca Java para geração/leitura de QR Codes |
| OSRM | Open Source Routing Machine — cálculo de rotas sobre OpenStreetMap |
| WPS | Wi-Fi Positioning System — geolocalização via redes Wi-Fi próximas |
| LoRa | Long Range — protocolo de rádio de longo alcance e baixo consumo |
| LoRaWAN | Protocolo de rede para dispositivos IoT baseado em LoRa |
| SRD | Sem Raça Definida — classificação de raça do pet |
| HEIC | Formato de imagem de câmeras Apple (iOS) |
| Atomic Design | Metodologia de UI que organiza componentes em átomos, moléculas, organismos, templates e páginas |
| CRA | Create React App — toolchain de build para aplicações React |
