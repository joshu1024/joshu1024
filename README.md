<h1 align="center">👋 Hi, I'm Joshua Kipamet</h1>

<p align="center">
  <strong>Fullstack AI Engineer</strong> — building production RAG systems, autonomous agents, and semantic search
</p>

<p align="center">
  <a href="https://www.linkedin.com/in/joshua-kipamet-148698140/">
    <img src="https://img.shields.io/badge/LinkedIn-0077B5?style=flat-square&logo=linkedin&logoColor=white"/>
  </a>
  <a href="https://portfolio-4jxo-git-main-joes-projects-50075601.vercel.app/">
    <img src="https://img.shields.io/badge/Portfolio-000000?style=flat-square&logo=vercel&logoColor=white"/>
  </a>
  <a href="mailto:joshuakipamet@gmail.com">
    <img src="https://img.shields.io/badge/Email-D14836?style=flat-square&logo=gmail&logoColor=white"/>
  </a>
  <img src="https://img.shields.io/badge/Open%20to-AI%20Fullstack%20%2F%20Backend%20Roles-1D9E75?style=flat-square"/>
</p>

---

## 🧠 What I build

Production AI systems — not tutorials, not wrappers. Deployed products with real architectural decisions, automated tests, and CI/CD pipelines.

- **RAG pipelines** — HyDE, hybrid search (vector + BM25 + RRF), re-ranking, semantic caching
- **Autonomous agents** — ReAct loops, typed tool registries, guardrails, trace logging, human-in-the-loop
- **Semantic search** — pgvector, Cohere embeddings, HNSW indexing, cosine similarity
- **Streaming AI** — raw SSE fetch, ReadableStream, TextDecoder, token-by-token rendering
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

## 💡 Architectural Decisions

Real decisions I made and debugged — not post-hoc justifications.

| Decision | Chose | Rejected | Why |
|----------|-------|----------|-----|
| LLM inference | Groq | OpenAI | Free tier, fast inference, same API shape |
| Embeddings | Cohere embed-english-v3 | OpenAI text-embedding-3 | Free tier, no credit card, 1024-dim vectors |
| Vector store | pgvector | Pinecone | Already on PostgreSQL — no new service, no extra cost. HNSW handles current scale |
| Streaming | Raw SSE fetch | Groq SDK | SDK v1.5.0 returned `delta: {}` for reasoning model chunks — switched to raw fetch which reads the stream directly and parses correctly |
| Chunking | Recursive | Fixed-size | Fixed-size breaks sentences mid-thought. Recursive splits on `\n\n` → `\n` → `. ` → ` ` — preserves complete thoughts |
| Multi-tenancy | Domain-based org grouping | Invite codes | Zero friction — same email domain auto-joins same org; public domains get isolated personal orgs |
| Auth storage | Authorization header | httpOnly cookies | Agent background workers make stateless API calls — cookies don't work in that context |

---

## 🚀 Featured Projects

---

### 🤖 Apply-AI — Autonomous Job Application Agent
![Status](https://img.shields.io/badge/Status-In%20Progress-378ADD?style=flat-square)

Autonomous AI agent that researches companies, identifies skill gaps, drafts tailored cover letters, generates likely interview questions, and produces a full report — the model decides what to do next, not the code.

**Agent vs workflow — the key distinction:**

| Workflow (what tutorials build) | Agent (what I built) |
|--------------------------------|---------------------|
| Hardcoded step order | Model picks each next tool from a registry |
| Fixed pipeline | ReAct loop: reason → act → observe → repeat |
| No failure handling | Tool failures returned as observations — agent adapts |
| One fixed checkpoint | `askUser` can pause the loop mid-execution |
| No safety bounds | Guardrails in code: max 15 iters, cost cap, repeat-call detection |

**Pipeline:**

```mermaid
flowchart TD
    A[CV + job description] --> B[agent.service\nreason — pick next tool]
    B --> C{guardrails\nmax 15 iters · cost cap\nrepeat-call check}
    C -->|stop| G[generateReport]
    C -->|continue| D[executeToolSafely\nZod validate · retry · backoff]
    D --> E[Tool registry\nparseCV · research · gaps · draft · finish]
    E -->|observation| B
    E -->|askUser| F[pause — wait for user]
    F -->|answer| B
    E -->|finish| G
    G --> H[save report + full trace to DB]
    B -.->|every iteration| T[traceEvent SSE → live UI]
```

**Stack:** Node.js · TypeScript · PostgreSQL · Prisma · Groq · Cohere · BullMQ · WebSockets · Mastra · React · shadcn/ui

💻 [GitHub](https://github.com/joshu1024/apply-ai) · 🔗 Live demo — coming soon

---

### 🧠 Enterprise AI Knowledge Base
![CI](https://github.com/joshu1024/Enterprise-ai-kb/actions/workflows/ci.yml/badge.svg)

Multi-tenant RAG SaaS. Teams upload company documents and query them in natural language with streaming answers and inline source citations.

**Basic RAG vs this implementation:**

| Tutorial RAG | This implementation |
|-------------|---------------------|
| Embed raw question | Embed hypothetical answer (HyDE) — questions and answers live in different vector spaces |
| Vector search only | Vector + BM25 keyword, merged with Reciprocal Rank Fusion |
| Return top-k directly | LLM re-ranks top 10, returns best 5 |
| No caching | Semantic cache — repeated queries (>0.92 similarity) cost zero API calls |
| Generic retrieval | Org-scoped — `WHERE organizationId = $1` on every query |

**Pipeline:**

```mermaid
flowchart TD
    A[User query] --> B{SemanticCache\nsimilarity > 0.92?}
    B -->|hit| C[stream cached answer\nzero API cost]
    B -->|miss| D[hydeQuery\ngenerate hypothetical answer]
    D --> E[generateQueryEmbedding\nCohere search_query type]
    E --> F[hybridSearch\nvector cosine + BM25 + RRF]
    F --> G[rerankChunks\nLLM scores top 10 → 5]
    G --> H[buildContext + citations\ninject into system prompt]
    H --> I[Groq raw fetch\nstream tokens via SSE]
    I --> J[setCachedAnswer\nwrite embedding to cache]
    I --> K[recordTokenUsage\nincrement user quota]
```

> 🎥 GIF: streaming answer with inline `[Source 1]` citations loading token-by-token — coming soon

**51 automated tests · GitHub Actions CI · Render + Vercel + Neon**

**Stack:** Node.js · TypeScript · PostgreSQL · pgvector · Prisma · Neon · Cohere · Groq · React · shadcn/ui · Redux Toolkit

🔗 [Live Demo](https://enterprise-ai-kb.vercel.app) · 💻 [GitHub](https://github.com/joshu1024/Enterprise-ai-kb)

---

### 👟 SneakerZone — E-Commerce + AI Shopping Assistant

Production e-commerce app with AI features layered on top of a real PostgreSQL database.

**AI features:**
- **Semantic search** — Cohere embeddings + pgvector. "Something for a teenager who likes running" returns relevant products by meaning, not keyword match. Retrieval-based — not the model learning or improving.
- **Tool use** — AI calls `searchProducts` or `semanticSearchProducts`, receives real Prisma query results, streams the answer. All tool calls scoped by `userId` — AI cannot access another user's orders under any prompt.
- **Security layer** — rate limiting, prompt injection pattern detection, output moderation scan before response reaches user, per-user token quota with monthly reset

> 🎥 GIF: chat widget streaming a product search response — coming soon

**Stack:** React · Node.js · Express · PostgreSQL · pgvector · Prisma · Groq · Cohere · Redux Toolkit · PayPal · Cloudinary

🔗 [Live Demo](https://sneakerzone.vercel.app) · 💻 [GitHub](https://github.com/joshu1024/mern-ecommerce)

---

### 📊 SaaS Analytics Dashboard

Role-based analytics platform — the project where I learned TypeScript by migrating a production MERN codebase.

- Migrated 10+ Redux slices, 20+ React components, 15+ API endpoints to TypeScript
- MongoDB aggregation pipelines over 50K+ records
- ~40% load time reduction with server-side pagination
- RBAC with JWT in httpOnly cookies — XSS token exposure eliminated

**Stack:** React · TypeScript · Node.js · MongoDB · Recharts · Redux Toolkit

🔗 [Live Demo](https://dashboard-mern-tau.vercel.app/) · 💻 [GitHub](https://github.com/joshu1024/Analytics-Dashboard---MERN)

---

## 🏗 Engineering Highlights

- Debugged Groq SDK streaming failure — `delta` returned as `{}` for reasoning models. Identified root cause (SDK v1.5.0 incompatibility), switched to raw SSE fetch, documented the fix
- Tests caught a real production bug — document slice `pending` reducers set `loading: false` instead of `true`. Would have shipped broken loading states without tests
- Migrated live ecommerce database from MongoDB to PostgreSQL + Prisma without data loss
- Tool calls scoped by `userId` in every Prisma query — AI cannot access another user's data even under adversarial prompting
- 51 automated tests across two projects — unit tests + agent behavioral evals with LLM-as-judge

---

## 📈 Currently Building

- 🔄 **Apply-AI** — autonomous job application agent (Phase 3)
- 🔜 **Docker** — containerization for Apply-AI
- 🔜 **Next.js** — App Router, server components, server actions
- 🔜 **Phase 4** — LangSmith tracing, prompt versioning, cost optimization

---

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=joshu1024&show_icons=true&theme=default&hide_border=true&count_private=true" alt="GitHub stats"/>
</p>

<p align="center">
  📍 Nairobi, Kenya — open to remote &nbsp;·&nbsp;
  <a href="mailto:joshuakipamet@gmail.com">joshuakipamet@gmail.com</a>
</p>
