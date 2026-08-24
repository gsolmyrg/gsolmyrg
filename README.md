# Guilherme Candeloro Padilha

**AI Solutions Architect** — Generative AI, Enterprise RAG & Multi-Agent Systems | Self-Hosted LLM Infrastructure

Florianópolis, Brazil · [LinkedIn](https://www.linkedin.com/in/guilherme-candeloro-72113426b) · guilherme@aiveon.com

---

I architect and operate production Generative AI systems for enterprise and regulated environments — with 20+ years in technology behind it, spanning software engineering, infrastructure, and information security.

My focus is the part of GenAI that most teams skip: **running it yourself, reliably**. Sizing GPU capacity, serving open-weight models on-premise, keeping sensitive corpora inside the client perimeter, and making the output traceable enough to survive an audit.

---

## What I work on

- **Enterprise RAG** over dense, messy document corpora — OCR and sanitization, chunking strategy, embeddings, hybrid retrieval, reranking, grounded generation with source attribution
- **Agentic systems** — single and multi-agent architectures with controlled tool scopes, designed so every action is visible and logged
- **Self-hosted LLM inference** — open-weight models served with vLLM, NVIDIA NIM, Triton, and TensorRT-LLM on NVIDIA L40S, RTX 6000 Blackwell, and Intel Gaudi 2
- **AI for regulated domains** — banking and collections, healthcare and mental health, public sector, education, legal and compliance
- **Evaluation as engineering** — custom QA datasets, LLM-as-a-judge scoring, and expert-in-the-loop validation, because "it looks good in the demo" is not a metric

---

## A note on private repositories

Most of my repositories are private. Nearly all of my applied AI work is delivered under NDA for enterprise clients in regulated industries, so the code, corpora, and architectures cannot be published.

What I can share is the shape of the work — what the system does, how it is structured, and which decisions it turned on. That is what the section below is for. **Access to specific repositories can be granted on request** for a hiring conversation, subject to the applicable agreements.

---

## Selected work

### AI Red Team Lab *(private)*

A hands-on range for attacking AI systems the way they actually break — not in a notebook, but in the product: sessions, uploads, retrieval, the canonical prompt, the user sitting next to you.

Three offensive exercises, mitigations that can be switched on and off **without a redeploy** (so cause and effect are observable in the same session), per-session isolation between participants, and an audit history that a "reset" does not erase. Runs entirely on-premise.

Built spec-first: the repository carries the epics, stack decisions, data schema, API contract, isolation design, and acceptance criteria as versioned artifacts before implementation.

`AI security` · `LLM red teaming` · `session isolation` · `on-premise` · `Python`

### Engineering Worklog *(private)*

A local-first CLI that reconstructs what an engineer actually did, by collecting evidence from Git history and the filesystem into daily worklogs.

**Deterministic core, privacy by default:** no telemetry, no data leaves the machine, and the same inputs always produce the same output. Layered architecture with a clean separation between domain, collectors, application services and CLI, plus cross-platform bootstrap and a `doctor` diagnostic command.

`Python` · `clean architecture` · `local-first` · `developer tooling`

### On-Premise Legal Document RAG *(private)*

A fully air-gapped retrieval system for legal case files: OCR ingestion, semantic chunking with page-level traceability, Milvus vector search with FAISS-GPU, and a reranking stage in front of a self-hosted Llama model. Deployed via GPU Docker Compose.

Built on-premise by requirement, not preference — the corpus cannot leave the client perimeter.

`RAG` · `Llama` · `Milvus` · `FAISS-GPU` · `reranking` · `OCR` · `on-premise`

### Hybrid-Retrieval Knowledge Agent *(private)*

A knowledge agent combining semantic and lexical retrieval, with neighborhood context expansion so that answers carry surrounding context rather than isolated fragments. Multi-format ingestion (PDF, DOCX, text), controlled URL processing, and source attribution on every response.

`RAG` · `hybrid search` · `document AI` · `source attribution`

### Conversational Agent Reference Stack *(public)*

A three-repository reference implementation of a multi-agent conversational system, published with synthetic data only:

- **[Agent flow](https://github.com/gsolmyrg/conversational_credit_negotiation_flow)** — CrewAI Flow with a router-based state machine, parallel classification and planning agents, and Pydantic structured outputs
- **[Middleware](https://github.com/gsolmyrg/conversational_credit_negotiation_middleware)** — FastAPI service with API-key authentication and messaging-channel integration
- **[Simulation app](https://github.com/gsolmyrg/conversational_credit_negotiation_app)** — Streamlit front end for exercising the flow against configurable synthetic personas

---

## Stack

**Models** — GPT-4 / 4o / o-series · Claude · Gemini · Llama 3.x · Mistral / Mixtral · Qwen · DeepSeek

**Serving & inference** — vLLM · NVIDIA NIM · Triton Inference Server · TensorRT-LLM · Ollama

**Retrieval** — Milvus · pgvector · Pinecone · Chroma / FAISS

**Orchestration** — LangChain · LlamaIndex · CrewAI · Model Context Protocol (MCP) · custom SDK-level code

**Customization** — LoRA / QLoRA fine-tuning · embedding and reranker tuning · quantization

**ML & NLP** — PyTorch · text classification · named entity recognition · sentiment analysis · document AI

**Platform** — Python · SQL · C/C++ · Docker · Terraform · GitHub Actions · MLflow · Prometheus / Grafana · PostgreSQL

**Cloud** — AWS · Google Cloud · Azure Machine Learning · on-premise and hybrid

**Hardware** — NVIDIA L40S · RTX 6000 Blackwell · Intel Gaudi 2 · Nutanix NAI · InfiniBand

---

## Speaking, teaching & mentoring

- **2026** — Speaker, multinational aerospace manufacturer: *AI in Hyperautomated Critical Environments*, delivered in person and live-streamed to 820 LATAM engineers
- **2025** — Plenary Speaker, Brazilian Government: practical and responsible use of AI in the public sector
- **2025** — Guest Lecturer, ISLA (Portugal): Cybersecurity and Artificial Intelligence
- **2025** — Plenary Speaker, Porto Business Group (Portugal): applying AI to business productivity
- **2025** — Startup Mentor, 351 Startups & Techstars (Portugal): AI strategy and product validation

---

## Credentials

**NVIDIA (official)** — NIM Microservices · Deploying a Model for Inference at Production Scale · Building RAG Agents with LLMs · Improving the Effectiveness of RAG Systems · Sizing LLM Inference Systems · InfiniBand Essentials

**Education** — Postgraduate Diploma in Data Science · Postgraduate Diploma in Advanced Python Programming · Technologist Degree in Information Security · AI Applications in Healthcare and Technical Fundamentals of Generative AI (Stanford) · AI for Business and OpenAI GPTs Development (Harvard Business School) · Python and Machine Learning (USP)

**Security & privacy** — Privacy & Data Protection · LGPD/GDPR Compliance · Cybersecurity (NYU)

---

## Open to

AI Solutions Architect · Generative AI Architect · Principal / Staff AI Engineer · AI Engineering Lead

Reach me at **guilherme@aiveon.com**.
