<img src="https://raw.githubusercontent.com/gsolmyrg/gsolmyrg/main/assets/hero.svg?v=1" alt="Terminal session probing a tokenizer for invisible characters: the classifier passes the input while the model receives a different sequence" width="880">

# Guilherme Candeloro Padilha

**AI Solutions Architect · AI Security Advisor**

Florianópolis, Brazil · [LinkedIn](https://www.linkedin.com/in/guilherme-candeloro-72113426b) · guilherme@aiveon.com

<p align="left">
  <img src="https://img.shields.io/badge/FOCUS-AI%20Security%20%C2%B7%20GenAI%20Architecture-E11D2E?style=flat-square&labelColor=08090B" alt="Focus: AI security and GenAI architecture">
  <img src="https://img.shields.io/badge/APPLIED%20AI-5%2B%20years-08090B?style=flat-square&labelColor=08090B" alt="5+ years applied AI">
  <img src="https://img.shields.io/badge/TECHNOLOGY-20%2B%20years-08090B?style=flat-square&labelColor=08090B" alt="20+ years in technology">
  <img src="https://img.shields.io/badge/RUNS-cloud%20%C2%B7%20on--prem%20%C2%B7%20air--gapped-08090B?style=flat-square&labelColor=08090B" alt="Cloud, on-premise, air-gapped">
</p>

---

## What you just watched

```text
   input ─▶ filter ─▶ normalize ─▶ tokenize ─▶ representation ─▶ output
   └─────────────┘                 └────────────────────────┘
   controls inspect here           behavior is decided here
```

A security control that reads visible text is not necessarily reading what the model receives. Zero-width characters survive the filter, change the segmentation, and reach the model as something else. The classifier reports clean. The model was handed a different sequence.

That gap is where I work: designing Generative AI systems that hold up not only against an audit, but against someone actively trying to break them.

Twenty years in infrastructure and information security, five building applied AI. The second half only makes sense because of the first.

---

## Research and writing

**The tokenizer as an attack surface**

Prompt injection dominates the conversation, and rightly so. But there is an earlier layer that rarely appears in threat models. Before a model interprets text, it fragments it — and small differences in characters, segmentation, or encoding produce a different internal representation.

Glitch tokens and weakly trained junk tokens exist in the thousands across models and tokenizers. Zero-width Unicode and adversarial tokenization can alter segmentation, degrade comprehension, obstruct auditing, and help evade classifiers — while the text still looks ordinary to a human reviewer.

The argument: tokenization sits inside the trust boundary, and therefore belongs inside threat modeling, adversarial testing, input normalization, tokenizer evaluation, observability, and red teaming.

> *Are we protecting only what users can read, or also what models actually process?*

Published on [LinkedIn](https://www.linkedin.com/in/guilherme-candeloro-72113426b), where I write on AI security and applied GenAI architecture.

---

## Attack surfaces I work on

| Surface | What is actually at stake |
|---|---|
| **Tokenization and normalization** | Controls inspecting text that differs from the model's internal representation |
| **Retrieval and corpus** | Contamination across sessions and tenants; poisoned or unbounded retrieval scope |
| **Agent tool scopes** | Actions taken outside the intended envelope; context leaking through tool calls |
| **Session isolation** | State bleeding between users; audit history a "reset" is expected to erase |
| **Evaluation integrity** | Metrics that flatter themselves, and scores computed on references too weak to support them |
| **Data residency** | Sensitive corpora leaving the perimeter as an architectural fact, not a policy violation |

---

## What I build

- **Enterprise RAG** over dense, adversarial document corpora — OCR and sanitization, chunking strategy, embeddings, hybrid retrieval, reranking, grounded generation with source attribution
- **Agentic systems** — single and multi-agent architectures with restricted tool scopes, designed so every action is visible and logged
- **Self-hosted and cloud LLM inference** — open-weight models on vLLM, NVIDIA NIM, Triton, and TensorRT-LLM across NVIDIA L40S, RTX 6000 Blackwell, and Intel Gaudi 2, or containerized endpoints on AWS and GCP when the workload calls for it
- **AI in regulated domains** — banking and collections, healthcare and mental health, public sector, education, legal and compliance
- **Evaluation harnesses** — custom QA datasets, LLM-as-a-judge scoring, expert-in-the-loop validation, and reliability gates that refuse to report a number they cannot defend

---

## Selected work

Nearly all applied AI work here is delivered under NDA for enterprise clients in regulated industries, so code and corpora cannot be published. What follows is the shape of the work. **Access to specific repositories can be granted on request** for a technical conversation, subject to the applicable agreements.

### AI Red Team Lab *(private)*

A range for attacking AI systems where they actually break — not in a notebook, but in the product: sessions, uploads, retrieval, the canonical prompt, the participant sitting next to you.

Three offensive exercises, mitigations switchable **without a redeploy** so cause and effect are observable in the same session, per-session isolation between participants, and an audit history a reset does not erase. Runs entirely on-premise.

Built spec-first: epics, stack decisions, data schema, API contract, isolation design, and acceptance criteria versioned as artifacts before implementation.

`AI security` · `LLM red teaming` · `session isolation` · `on-premise`

### On-Premise Legal Document RAG *(private)*

Air-gapped retrieval over legal case files: OCR ingestion, semantic chunking with page-level traceability, Milvus vector search with FAISS-GPU, and reranking in front of a self-hosted Llama model, deployed via GPU Docker Compose.

On-premise by requirement, not preference — the corpus cannot leave the client perimeter.

`RAG` · `Llama` · `Milvus` · `FAISS-GPU` · `air-gapped`

### OCR Engine Evaluation Harness *(private)*

Page-by-page benchmarking of competing OCR engines on character and word error rate, bag-of-words recall, and layout F1 against the document's native text layer, with cross-engine disagreement detection and visual quality-control overlays.

Includes a reliability gate that invalidates accuracy metrics when the reference text is too short to support them — a score you cannot trust is worse than no score. Validated on a 504-page case file, with per-engine latency measured to drive selection.

`evaluation` · `CER / WER` · `layout F1` · `benchmarking`

### Hybrid-Retrieval Knowledge Agent *(private)*

Semantic and lexical retrieval combined, with neighborhood context expansion so answers carry surrounding context rather than isolated fragments. Multi-format ingestion, controlled URL processing, source attribution on every response.

`RAG` · `hybrid search` · `document AI` · `source attribution`

### On-Premise Speech Pipeline *(private)*

Whisper transcription feeding XTTS v2 and YourTTS for zero-shot voice synthesis from a ten-second reference, with silence-based segmentation and per-chunk VRAM reclamation to process long-form audio inside fixed GPU memory.

`Whisper` · `XTTS v2` · `VRAM management` · `on-premise`

### Engineering Worklog *(private)*

A local-first CLI that reconstructs what an engineer actually did, collecting evidence from Git history and the filesystem into daily worklogs. Deterministic core, privacy by default: no telemetry, nothing leaves the machine, identical inputs always produce identical output. Layered architecture separating domain, collectors, application services, and CLI.

`Python` · `clean architecture` · `local-first` · `privacy by design`

### Conversational Agent Reference Stack *(public)*

Three-repository reference implementation of a multi-agent conversational system, published with synthetic data only.

[**Agent flow**](https://github.com/gsolmyrg/conversational_credit_negotiation_flow) — CrewAI Flow with a router-based state machine, parallel classification and planning agents, Pydantic structured outputs · [**Middleware**](https://github.com/gsolmyrg/conversational_credit_negotiation_middleware) — FastAPI with API-key authentication and messaging-channel integration · [**Simulation app**](https://github.com/gsolmyrg/conversational_credit_negotiation_app) — Streamlit front end driving configurable synthetic personas

---

## Stack

**Models** — OpenAI (GPT-4 / 4o / o-series) · Anthropic Claude · Google Gemini · Llama 3.x · Mistral / Mixtral · Qwen · DeepSeek · Whisper

**Serving and inference** — vLLM · NVIDIA NIM · Triton Inference Server · TensorRT-LLM · Ollama · cloud-managed endpoints (AWS, GCP)

**Retrieval** — Milvus · pgvector · Pinecone · Chroma / FAISS · hybrid semantic and lexical search · reranking

**Orchestration** — LangChain · LlamaIndex · CrewAI · Model Context Protocol (MCP) · custom SDK-level code

**Customization** — LoRA / QLoRA fine-tuning · embedding and reranker tuning · quantization

**Document AI and OCR** — Surya OCR · Tesseract · docTR · Docling · Unstructured · VLM-based parsing

**Security and governance** — LLM threat modeling · red teaming · prompt and context isolation · input normalization · audit trails · LGPD / GDPR

**Platform** — Python · SQL · C/C++ · Docker · Terraform · GitHub Actions · MLflow · Prometheus / Grafana · PostgreSQL

**Infrastructure** — NVIDIA L40S · RTX 6000 Blackwell · Intel Gaudi 2 · Nutanix NAI · InfiniBand · AWS · Google Cloud · Azure Machine Learning

---

## Credentials

**NVIDIA (official)** — NIM Microservices · Deploying a Model for Inference at Production Scale · Building RAG Agents with LLMs · Improving the Effectiveness of RAG Systems · Sizing LLM Inference Systems · InfiniBand Essentials

**Education** — Postgraduate Diploma in Data Science · Postgraduate Diploma in Advanced Python Programming · Technologist Degree in Information Security · AI Applications in Healthcare and Technical Fundamentals of Generative AI (Stanford) · AI for Business and OpenAI GPTs Development (Harvard Business School) · Python and Machine Learning (USP)

**Security and privacy** — Privacy & Data Protection · LGPD / GDPR Compliance · Cybersecurity (NYU)
