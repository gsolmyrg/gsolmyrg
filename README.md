```text
╔══════════════════════════════════════════════════════════════════════════╗
║                                                                          ║
║   GUILHERME CANDELORO PADILHA                                            ║
║   AI Solutions Architect                                                 ║
║                                                                          ║
║   Generative AI · Enterprise RAG · Agents · LLM Infrastructure           ║
║                                                                          ║
║   ──────────────────────────────────────────────────────────────────     ║
║   CAPABILITY BRIEF          Rev. 2026.08          Florianopolis, BR      ║
║                                                                          ║
╚══════════════════════════════════════════════════════════════════════════╝
```

<p align="left">
  <img src="https://img.shields.io/badge/EXPERIENCE-20%2B%20years%20in%20technology-76B900?style=for-the-badge&labelColor=0B1220" alt="20+ years in technology">
  <img src="https://img.shields.io/badge/APPLIED%20AI-3%2B%20years%20in%20production-76B900?style=for-the-badge&labelColor=0B1220" alt="3+ years applied AI in production">
  <img src="https://img.shields.io/badge/DEPLOYS-cloud%20%C2%B7%20on--premise%20%C2%B7%20hybrid-0B1220?style=for-the-badge&labelColor=0B1220" alt="Cloud, on-premise and hybrid">
</p>

---

## THE PROBLEM I WORK ON

Most enterprises can prototype Generative AI in a week and still fail to ship it for a year. The blocker is almost never the model. It is that the corpus cannot leave the client's perimeter, that answers cannot be reproduced or defended when someone asks *why did it say that*, and that cost per token grows faster than the value the system creates.

I design and build the version that survives those three questions.

---

## WHAT I BUILD

```text
   documents · forms · case files · scanned PDFs
        │
        ▼
   OCR / VLM parsing ──▶ chunk + embed ──▶ vector index
                                               │
                                               ▼
   grounded answer ◀── LLM ◀── rerank ◀── hybrid retrieval
        │              vLLM · NIM · Triton · TensorRT-LLM
        ▼
   source attribution · structured audit log · evaluation set
```

Every arrow above is a decision with a cost, a latency and a failure mode. Architecture is choosing them on purpose.

---

## WHERE IT RUNS

The self-hosted-versus-API question has no universal answer. It has a constraint that decides it.

| If your binding constraint is | What I deploy | Why |
|---|---|---|
| The corpus legally cannot leave the building | Open-weight models on your own GPUs, air-gapped | Data residency is architectural, not contractual |
| Volume is unpredictable, sensitivity is low | Managed endpoints on AWS or GCP | You should not buy GPUs to absorb a spike |
| Sensitive core, elastic edges | Hybrid: private inference, cloud orchestration | Isolate what is regulated, scale what is not |
| Cost per token is the ceiling | Self-hosted, sized and quantized to the workload | Fixed cost beats per-call cost past a break-even |
| Latency is a product requirement | Local inference with reranking budget tuned | Every retrieval stage is a latency purchase |

---

## FAILURE MODES I DESIGN AGAINST

This is the part that separates a demo from a system.

| Failure mode | Control I build in |
|---|---|
| Answers nobody can trace back to a source | Source attribution on every response, plus structured audit logging |
| Corpus contamination across sessions or tenants | Per-session isolation and scoped retrieval boundaries |
| Context and prompt leakage through tool use | Restricted tool scopes, visible actions, agent behavior bounded by design |
| Evaluation metrics that flatter themselves | Reliability gates that invalidate a score when the reference is too weak to support it |
| Cost that quietly outgrows the value | Inference sizing, quantization, and migration off per-token pricing |
| "It worked in the demo" | Evaluation sets and expert-in-the-loop validation before rollout |

---

## SELECTED WORK

Nearly all applied AI work here is delivered under NDA for enterprise clients in regulated industries, so code and corpora cannot be published. What follows is the shape of the work. **Access to specific repositories can be granted on request** for a technical conversation, subject to the applicable agreements.

**AI Red Team Lab** · *private*
A range for attacking AI systems where they actually break — sessions, uploads, retrieval, the canonical prompt. Three offensive exercises, mitigations switchable without a redeploy so cause and effect are observable in the same session, per-session isolation, and an audit history a reset does not erase. Built spec-first: epics, schema, API contract, isolation design and acceptance criteria versioned before implementation.

**On-Premise Legal Document RAG** · *private*
Air-gapped retrieval over legal case files. OCR ingestion, semantic chunking with page-level traceability, Milvus vector search with FAISS-GPU, reranking in front of a self-hosted Llama model, deployed via GPU Docker Compose. On-premise by requirement, not preference.

**OCR Engine Evaluation Harness** · *private*
Page-by-page benchmarking of competing OCR engines on character and word error rate, bag-of-words recall and layout F1 against the document's native text layer, with cross-engine disagreement detection and visual QC overlays. Includes a reliability gate that invalidates accuracy metrics when the reference text is too short to support them. Validated on a 504-page case file with per-engine latency measured to drive selection.

**Hybrid-Retrieval Knowledge Agent** · *private*
Semantic and lexical retrieval combined, with neighborhood context expansion so answers carry surrounding context instead of isolated fragments. Multi-format ingestion, controlled URL processing, source attribution on every response.

**On-Premise Speech Pipeline** · *private*
Whisper transcription feeding XTTS v2 and YourTTS for zero-shot voice synthesis from a ten-second reference, with silence-based segmentation and per-chunk VRAM reclamation to process long-form audio inside fixed GPU memory.

**Conversational Agent Reference Stack** · *public, synthetic data only*
[Agent flow](https://github.com/gsolmyrg/conversational_credit_negotiation_flow) — CrewAI Flow with a router-based state machine, parallel classification and planning agents, Pydantic structured outputs · [Middleware](https://github.com/gsolmyrg/conversational_credit_negotiation_middleware) — FastAPI with API-key authentication and messaging-channel integration · [Simulation app](https://github.com/gsolmyrg/conversational_credit_negotiation_app) — Streamlit front end driving configurable synthetic personas.

---

## TECHNOLOGY, BY LEVEL OF CLAIM

Listed by what I can actually defend in an interview, not by what looks good in a keyword search.

**Run in production, repeatedly**
Python · PostgreSQL · Docker · RAG pipelines end to end · agent orchestration · vLLM · NVIDIA NIM · Triton · TensorRT-LLM · Milvus · pgvector · OpenAI, Anthropic and Google model families · Llama · Mistral · Qwen · DeepSeek · AWS (EC2, S3, VPC, IAM, Lambda, ECS/EKS, RDS, API Gateway) · Google Cloud · LangChain · LlamaIndex · CrewAI · MCP

**Built and operated hands-on**
NVIDIA L40S · RTX 6000 Blackwell · Intel Gaudi 2 · Nutanix NAI · InfiniBand · GPU sizing and VRAM optimization · LoRA / QLoRA fine-tuning · embedding and reranker tuning · Whisper · XTTS v2 · Surya OCR · Tesseract · docTR · Docling · VLM document parsing · Terraform · GitHub Actions · MLflow · Prometheus / Grafana · PyTorch · Azure Machine Learning

**Benchmarked and evaluated**
OCR engine comparison (CER, WER, bag-of-words recall, layout F1) · retrieval strategies and reranking configurations · LLM-as-a-judge scoring against custom QA sets · inference throughput and latency across serving stacks

**Foundations that still matter**
20 years in infrastructure, information security and software engineering · C / C++ · SQL · LGPD and GDPR compliance · security-first architecture · data governance

---

## HOW AN ENGAGEMENT USUALLY STARTS

**Architecture review** — a short, bounded engagement producing a reference architecture, an infrastructure sizing model, a cost projection and a risk register. Useful when a proof of concept exists and nobody can agree on whether it can go to production.

**Design and build** — architecture through production, hands-on. I do not hand over a diagram and leave; I implement it and stay through post-sales.

**Technical advisory** — ongoing architecture authority for a team already building, including standards, review and vendor and model selection.

---

## CREDENTIALS

**NVIDIA, official** — NIM Microservices · Deploying a Model for Inference at Production Scale · Building RAG Agents with LLMs · Improving the Effectiveness of RAG Systems · Sizing LLM Inference Systems · InfiniBand Essentials

**Education** — Postgraduate Diploma, Data Science · Postgraduate Diploma, Advanced Python Programming · Technologist Degree, Information Security · Stanford University: AI Applications in Healthcare, Technical Fundamentals of Generative AI · Harvard Business School: AI for Business, OpenAI GPTs Development · USP: Python and Machine Learning

**Security and privacy** — Privacy & Data Protection · LGPD / GDPR Compliance · Cybersecurity, NYU

---

```text
   ── Florianopolis, Brazil · available for remote and hybrid engagements ──
```

<p align="left">
  <a href="https://www.linkedin.com/in/guilherme-candeloro-72113426b">
    <img src="https://img.shields.io/badge/LinkedIn-guilherme--candeloro-0B1220?style=for-the-badge&logo=linkedin&logoColor=76B900" alt="LinkedIn">
  </a>
  <a href="mailto:guilherme@aiveon.com">
    <img src="https://img.shields.io/badge/Email-guilherme%40aiveon.com-0B1220?style=for-the-badge&logo=maildotru&logoColor=76B900" alt="Email">
  </a>
</p>
