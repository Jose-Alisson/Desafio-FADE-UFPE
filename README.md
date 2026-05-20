# 🚀 Fade UFPE — Sistema Inteligente de Planos de Aula com IA

## 📌 Visão Geral do Projeto

O **Fade UFPE** é uma plataforma full stack desenvolvida como solução para o desafio técnico da **Fade UFPE**, com foco em engenharia de software moderna, arquitetura escalável, boas práticas de backend e integração avançada com Inteligência Artificial.

O sistema tem como objetivo principal o **gerenciamento de planos de aula**, indo além de um CRUD tradicional ao incorporar um mecanismo inteligente de recomendação de conteúdo pedagógico baseado em IA.

---

## 🧱 Arquitetura do Sistema

A aplicação foi projetada com separação clara de responsabilidades:

* 🔧 Backend: API REST + regras de negócio + IA
* 🎨 Frontend: SPA moderna
* 🗄️ Banco de Dados: PostgreSQL
* ⚙️ Infraestrutura: Docker + Nginx + VPS
* 🧠 IA: Sistema de recomendação pedagógica - Claude (Anthropic)

---

## 🌐 Ambiente de Produção

O sistema está disponível em ambiente real de execução:

👉 [https://sunshineax.com/](https://sunshineax.com/)

---

## 🔧 Backend (Fade Server)

### 🧰 Stack

* Node.js
* TypeScript / JavaScript
* Fastify
* Prisma ORM (v7)
* Zod (validação de dados)
* JWT (autenticação)
* Redis (cache de performance e otimização de consultas)

---

### ⚙️ Funcionalidades principais (Requisitos atendidos)

✔ CRUD completo de planos de aula (Lessons)
✔ Listagem com paginação
✔ Cadastro, edição e remoção
✔ Busca por:

* Título da aula
* Disciplina
* Tags

✔ Filtros por disciplina, tags e data prevista
✔ Ordenação por título e data de criação

---

### 🧠 Arquitetura e decisões técnicas

* Criação de uma camada tipo “mini framework” sobre Fastify para padronização e aceleração do desenvolvimento
* Validação centralizada de requisições utilizando Zod
* Sistema de cache com **Redis aplicado em filtros e consultas críticas**, reduzindo carga e melhorando performance
* Uso de `cacheable` para abstração de estratégias de cache
* Arquitetura modular preparada para escalabilidade

---

## 🧠 Sistema de Inteligência Artificial (Smart Assist)

O sistema implementa o requisito de **“Smart Assist”**, onde a IA auxilia o professor na criação de planos de aula.

### ⚙️ Funcionamento

* O frontend envia:

  * Título da aula
  * Disciplina
  * Ementa/Resumo

* O backend:

  * Monta prompt estruturado (prompt engineering)
  * Consulta uma API de LLM
  * Retorna:

    * conteúdos complementares
    * tópicos relacionados
    * 3 tags recomendadas

* O frontend preenche automaticamente os campos com base na resposta

---

### 🧩 Arquitetura avançada de IA (Diferencial)

Foi implementado um modelo persistido chamado:

### `IaRecommendation`

Responsável por:

* Armazenar respostas geradas pela IA
* Estruturar o retorno da LLM
* Aplicar uma **máscara inteligente sobre a entidade `Lesson`**
* Garantir rastreabilidade e reprodutibilidade das recomendações

---

### 🔄 Fluxo da IA

1. Usuário solicita recomendação no formulário
2. Backend envia dados para a IA
3. IA retorna sugestão estruturada
4. Resposta é normalizada e salva em `IaRecommendation`
5. A recomendação é aplicada como “máscara” na `Lesson`
6. Frontend recebe dados enriquecidos automaticamente

---

### 📊 Observabilidade da IA

As interações com a IA são monitoradas com logs estruturados:

* Latência da requisição
* Tokens estimados
* Contexto da operação
* Identificador da Lesson processada

---

## 🎨 Frontend (Fade Front)

### 🧰 Stack

* Angular 20

---

### ⚙️ Requisitos atendidos

✔ SPA (Single Page Application)
✔ Tela de listagem com paginação e filtros
✔ Formulário de criação/edição com validação
✔ Feedback visual durante processamento da IA (loading state)
✔ Tratamento de erro em chamadas à API
✔ Login e registro de usuários

---

### ✨ Experiência do usuário

* Splash screen durante processamento da IA
* Preenchimento automático via Smart Assist
* Interface responsiva e fluida
* Fluxo otimizado de criação de planos

---

## 🗄️ Banco de Dados

* PostgreSQL como banco principal
* Modelagem relacional estruturada
* Prisma ORM para acesso tipado
* Migrações automatizadas

---

## ⚙️ DevOps & Infraestrutura

✔ Docker + Docker Compose para orquestração
✔ Nginx como reverse proxy
✔ Deploy em VPS própria
✔ Ambiente acessível publicamente

---

## 📊 Observabilidade (Requisito atendido)

✔ Logs estruturados implementados
✔ Monitoramento de operações críticas
✔ Logs de chamadas da IA com:

* tokens
* contexto

---

## 🔐 Autenticação e Segurança

* JWT para autenticação stateless
* Sistema de usuários com login e registro
* Controle de acesso por roles (RBAC parcial)
* Endpoints com acesso flexível conforme contexto

---

## 🚀 Funcionalidades Técnicas Relevantes

* CRUD completo de planos de aula
* Sistema de filtros avançados
* Paginação otimizada
* Cache com Redis em endpoints críticos
* Integração backend + IA (Smart Assist)
* Persistência de recomendações de IA
* Arquitetura modular e escalável

---

## 👤 Acesso ao Sistema (Demo)

Para avaliação do sistema, está disponível um usuário demo com acesso completo:

> ⚠️ Ambiente destinado exclusivamente para testes técnicos

* 📧 Usuário: `alissonbarbosa.9982@gmail.com`
* 🔑 Senha: `a12345678`

> 💡 Caso queira, sinta-se à vontade para criar uma nova conta e testar o fluxo completo de registro e autenticação.

---

## 🔗 Repositórios

* 🎨 Frontend: [https://github.com/Jose-Alisson/Fade---Front](https://github.com/Jose-Alisson/Fade---Front)
* 🔧 Backend: [https://github.com/Jose-Alisson/Fade---Server](https://github.com/Jose-Alisson/Fade---Server)

---

## 📈 Melhorias Futuras

* Testes automatizados (unitários e e2e)
* Pipeline CI/CD
* Observabilidade avançada (Prometheus/Grafana)
* Escalabilidade horizontal
* Evolução do motor de recomendação IA
* Cache distribuído avançado

---

## 🧠 Consideração Final

O Fade UFPE demonstra uma solução completa de engenharia full stack, integrando backend robusto, frontend moderno, inteligência artificial aplicada e infraestrutura real em produção.

O projeto vai além de um CRUD tradicional, implementando arquitetura orientada a escalabilidade, rastreabilidade e enriquecimento inteligente de dados educacionais.

---

# ✅ Checklist final (validando o desafio)

✔ CRUD de planos de aula
✔ Paginação
✔ Filtros (disciplina, tags, data)
✔ Busca por título
✔ Ordenação
✔ Smart Assist com IA
✔ Prompt engineering estruturado
✔ Front SPA
✔ Loading state IA
✔ Tratamento de erro IA
✔ Docker + compose
✔ CI/observabilidade (logs estruturados)
✔ Deploy VPS
✔ Uso de LLM
✔ Segurança via env + JWT
✔ Cache (Redis)