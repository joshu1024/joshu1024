<h1 align="center">👋 Hi, I'm Joshua Kipamet</h1>

<p align="center">
  <strong>Fullstack AI Engineer</strong> — building production AI systems with RAG pipelines, autonomous agents, and semantic search
</p>

<p align="center">
  <a href="https://www.linkedin.com/in/joshua-kipamet-148698140/">
    <img src="https://img.shields.io/badge/LinkedIn-0077B5?style=flat-square&logo=linkedin&logoColor=white"/>
  </a>
  <a href="https://github.com/joshu1024">
    <img src="https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white"/>
  </a>
  <a href="https://portfolio-4jxo-git-main-joes-projects-50075601.vercel.app/">
    <img src="https://img.shields.io/badge/Portfolio-000000?style=flat-square&logo=vercel&logoColor=white"/>
  </a>
  <a href="mailto:joshuakipamet@gmail.com">
    <img src="https://img.shields.io/badge/Email-D14836?style=flat-square&logo=gmail&logoColor=white"/>
  </a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Open%20to-AI%20Fullstack%20%2F%20Backend%20Engineering%20Roles-1D9E75?style=flat-square"/>
</p>

---

## 🧠 What I build

I build production AI systems — not tutorials, not wrappers. Real deployed products with architectural decisions, automated tests, and CI/CD pipelines.

- **RAG pipelines** — HyDE, hybrid search (vector + BM25 + RRF), re-ranking, semantic caching
- **Autonomous agents** — ReAct loops, tool registries, guardrails, trace logging, human-in-the-loop
- **Semantic search** — pgvector, Cohere embeddings, HNSW indexing, cosine similarity
- **Streaming AI** — SSE, ReadableStream, TextDecoder, token-by-token rendering
- **Multi-tenant SaaS** — org-scoped data isolation, RBAC, per-user token quotas

---

## 🛠 Tech Stack

<table>
<tr>
<td><strong>Frontend</strong></td>
<td>
<img src="https://img.shields.io/badge/React-20232A?style=flat-square&logo=react&logoColor=61DAFB"/>
<img src="https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white"/>
<img src="https://img.shields.io/badge/Redux_Toolkit-764ABC?style=flat-square&logo=redux&logoColor=white"/>
<img src="https://img.shields.io/badge/Tailwind-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white"/>
<img src="https://img.shields.io/badge/shadcn/ui-000000?style=flat-square&logoColor=white"/>
</td>
</tr>
<tr>
<td><strong>Backend</strong></td>
<td>
<img src="https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=nodedotjs&logoColor=white"/>
<img src="https://img.shields.io/badge/Express-000000?style=flat-square&logo=express&logoColor=white"/>
<img src="https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white"/>
<img src="https://img.shields.io/badge/REST_API-FF6C37?style=flat-square&logoColor=white"/>
</td>
</tr>
<tr>
<td><strong>AI & Vector</strong></td>
<td>
<img src="https://img.shields.io/badge/pgvector-336791?style=flat-square&logo=postgresql&logoColor=white"/>
<img src="https://img.shields.io/badge/Cohere-6B4FBB?style=flat-square&logoColor=white"/>
<img src="https://img.shields.io/badge/Groq-F55036?style=flat-square&logoColor=white"/>
<img src="https://img.shields.io/badge/RAG_Pipelines-7F77DD?style=flat-square&logoColor=white"/>
<img src="https://img.shields.io/badge/ReAct_Agents-D85A30?style=flat-square&logoColor=white"/>
</td>
</tr>
<tr>
<td><strong>Database</strong></td>
<td>
<img src="https://img.shields.io/badge/PostgreSQL-316192?style=flat-square&logo=postgresql&logoColor=white"/>
<img src="https://img.shields.io/badge/MongoDB-47A248?style=flat-square&logo=mongodb&logoColor=white"/>
<img src="https://img.shields.io/badge/Prisma-2D3748?style=flat-square&logo=prisma&logoColor=white"/>
<img src="https://img.shields.io/badge/Neon-00E5CC?style=flat-square&logoColor=black"/>
</td>
</tr>
<tr>
<td><strong>DevOps</strong></td>
<td>
<img src="https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white"/>
<img src="https://img.shields.io/badge/Vercel-000000?style=flat-square&logo=vercel&logoColor=white"/>
<img src="https://img.shields.io/badge/Render-46E3B7?style=flat-square&logo=render&logoColor=black"/>
<img src="https://img.shields.io/badge/Vitest-6E9F18?style=flat-square&logo=vitest&logoColor=white"/>
</td>
</tr>
</table>

---

## 🚀 Featured Projects

---

### 🤖 Apply-AI — Autonomous Job Application Agent
![Status](https://img.shields.io/badge/Status-In%20Progress-E6F1FB?style=flat-square&color=378ADD)

Autonomous AI agent that researches companies, identifies skill gaps between a CV and job description, drafts tailored cover letters, generates likely interview questions, and produces a full application report — without human intervention at every step.

**What makes it an agent, not a workflow:**
- Model decides which tool to call next — no hardcoded step order
- ReAct loop: reason → act → observe → repeat until `finish` or guardrail stops it
- Guardrails in code: max 15 iterations, cost budget, repeated-call detection, Zod argument validation
- Tool failures returned as observations — agent adapts, retries, or flags low confidence
- `askUser` tool — agent can pause mid-loop to ask the user a question
- Full trace log — every thought, tool call, and observation saved to database

**Stack:** Node.js · TypeScript · PostgreSQL · Prisma · Groq · Cohere · BullMQ · WebSockets · Mastra · React · shadcn/ui

🔗 Live Demo → coming soon  
💻 [GitHub](https://github.com/joshu1024/apply-ai)

---

### 🧠 Enterprise AI Knowledge Base
![CI](https://github.com/joshu1024/Enterprise-ai-kb/actions/workflows/ci.yml/badge.svg)

Production-ready multi-tenant RAG SaaS. Teams upload company documents and query them in natural language with streaming answers and inline source citations.

**Advanced RAG pipeline — not the tutorial version:**
- HyDE — embed a hypothetical answer, not the raw question
- Hybrid search — vector cosine + BM25 keyword, merged with Reciprocal Rank Fusion
- Re-ranking — LLM scores top 10 chunks, returns best 5
- Semantic caching — repeated queries (>0.92 similarity) cost zero API calls
- Multi-tenant — single org per email domain, org-scoped data isolation

**51 automated tests · GitHub Actions CI · Deployed on Render + Vercel + Neon**

**Stack:** Node.js · TypeScript · PostgreSQL · pgvector · Prisma · Neon · Cohere · Groq · React · shadcn/ui · Redux Toolkit

🔗 [Live Demo](https://enterprise-ai-kb.vercel.app)  
💻 [GitHub](https://github.com/joshu1024/Enterprise-ai-kb)

---

### 👟 SneakerZone — E-Commerce + AI Shopping Assistant

Production-ready e-commerce platform with an AI shopping assistant that uses tool calling to query real PostgreSQL data and stream results word by word.

**AI layer:**
- Semantic product search — Cohere embeddings + pgvector. "Something for a teenager who likes running" returns relevant results by meaning not keywords
- Tool use / function calling — AI queries real database via Prisma, scoped by userId
- Full AI security layer — rate limiting, prompt injection detection, output moderation, per-user token quotas
- Streaming chat — SSE, ReadableStream, AbortController

**Stack:** React · Node.js · Express · PostgreSQL · pgvector · Prisma · Groq · Cohere · Redux Toolkit · PayPal · Cloudinary

🔗 [Live Demo](https://mern-ecommerce-26w1-git-main-joes-projects-50075601.vercel.app/)  
💻 [GitHub](https://github.com/joshu1024/mern-ecommerce)

---

### 📊 SaaS Analytics Dashboard

Role-based analytics platform built with TypeScript across the full stack.

- Migrated entire codebase to TypeScript — 10+ Redux slices, 20+ React components, 15+ API endpoints
- MongoDB aggregation pipelines — real-time insights across 50K+ records
- Reduced initial load time by ~40% with server-side pagination
- RBAC authorization system — JWT with httpOnly cookies

**Stack:** React · TypeScript · Node.js · MongoDB · Recharts · Redux Toolkit · Railway

🔗 [Live Demo](https://dashboard-mern-tau.vercel.app/)  
💻 [GitHub](https://github.com/joshu1024/Analytics-Dashboard---MERN)

---

### 🖼 AI Text-to-Image Generator · ✂️ Background Remover

Two AI-powered MERN apps — image generation and background removal using ClipDrop API with optimized request handling and real-time preview.

🔗 [Text-to-Image](https://ai-text-to-image-six.vercel.app/) · [Background Remover](https://bg-remover-xi-brown.vercel.app/)  
💻 [Text-to-Image Repo](https://github.com/joshu1024/AI-Text-to-Image-) · [Background Remover Repo](https://github.com/joshu1024/bg-remover)

---

## 🏗 Engineering Highlights

- Built production RAG SaaS with HyDE, hybrid search, re-ranking, semantic caching — not a tutorial
- Building autonomous agent with ReAct loop, typed tool registry, guardrails, and full trace logging
- 51 automated tests across backend and frontend — tests caught a real production bug (loading state never set to true)
- GitHub Actions CI — all tests + build verified on every push
- Migrated live ecommerce database from MongoDB to PostgreSQL without data loss
- Debugged real library incompatibilities — Groq SDK streaming, pgvector dimension mismatch, ESM/CommonJS conflicts
- Tool calls scoped by userId — AI can never access another user's data even under prompt manipulation

---

## 📈 Currently Building

- 🔄 **Apply-AI** — autonomous job application agent (Phase 3 of AI roadmap)
- 🔜 **Docker** — containerization for Apply-AI
- 🔜 **Next.js** — App Router, server components, server actions
- 🔜 **Phase 4** — LangSmith tracing, prompt versioning, cost optimization

---

## 📫 Connect

<p>
  🌐 <a href="https://portfolio-4jxo-git-main-joes-projects-50075601.vercel.app/">Portfolio</a> &nbsp;·&nbsp;
  💼 <a href="https://www.linkedin.com/in/joshua-kipamet-148698140/">LinkedIn</a> &nbsp;·&nbsp;
  💻 <a href="https://github.com/joshu1024">GitHub</a> &nbsp;·&nbsp;
  📧 <a href="mailto:joshuakipamet@gmail.com">joshuakipamet@gmail.com</a> &nbsp;·&nbsp;
  📍 Nairobi, Kenya — open to remote
</p>

---

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=joshu1024&show_icons=true&theme=default&hide_border=true&count_private=true" alt="GitHub stats"/>
</p>
