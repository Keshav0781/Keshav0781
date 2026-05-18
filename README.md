# Keshav Jha

**AI Engineer and Data Scientist** based in Erlangen, Germany, with an M.Sc. in Data Science from Friedrich-Alexander University Erlangen-Nuremberg.

I have spent most of my career working at the intersection of data, analytics, and engineering. At Accenture I worked as a Senior Software Engineer for 4.5 years on BestBuy's order management and retail analytics: analysing order lifecycles across Sterling OMS, building Power BI dashboards consumed daily by operations teams, migrating analytical workflows to BigQuery during BestBuy's GCP adoption, and translating order pattern analysis into inventory and procurement recommendations. At Siemens Healthineers I worked part-time on machine learning models, data pipelines, and AI-driven solutions for medical imaging during my Master's studies.

My current focus is production AI engineering: building systems that work end to end, from the retrieval architecture to the cloud deployment. I am also interested in data science and data analytics roles where the emphasis is on turning complex data into decisions that matter.

<br>

## Skills

Python is my primary language. On the AI engineering side: LangGraph, LangChain, ChromaDB, sentence-transformers, FastAPI, Docker, GCP Cloud Run, BigQuery, Pub/Sub, Terraform, Ragas. On the deep learning side: PyTorch, U-Net, nnU-Net, SAM, LoRA adapters. For analytics and forecasting: Pandas, Scikit-learn, Prophet, Statsmodels, Power BI, SQL. Cloud experience across GCP and Azure, with hands-on BigQuery work both at Accenture and in personal projects.

<br>

## Projects

### MedFlow Referral Agent: Clinical Referral AI System

A production-grade multi-agent AI system built for LMU Klinikum Munich that automatically processes patient referral PDFs and routes them to the correct hospital department, classifies urgency, and generates a clinical summary for coordinator review. The coordinator reviews every AI decision before any action is taken — AI assists, never decides.

The pipeline runs as a LangGraph graph with five nodes: PDF extraction via PyMuPDF, department routing using ChromaDB RAG and Gemini, urgency classification using ChromaDB RAG and Gemini, escalation check for Emergency cases, and clinical summary generation. Emergency cases trigger an immediate escalation alert before the coordinator has even reviewed the document. All coordinator decisions — Approve, Edit, or Reject — are logged to BigQuery for full clinical audit trail compliance.

The system is deployed across three isolated environments on GCP Cloud Run with a full CI/CD pipeline. Every push runs 43 automated tests. Staging deployment requires a Ragas accuracy gate — routing accuracy above 90% and urgency accuracy above 95% — before promotion. Production deployments require manual approval.

**Tech Stack:** Python, LangGraph, gemini-2.5-flash, ChromaDB, FastAPI, PyMuPDF, GCP Cloud Run, Pub/Sub, BigQuery, Terraform, GitHub Actions, Ragas

**Live Demo:**
- Dev: https://medflow-referral-agent-dev-togzrymjsq-ey.a.run.app
- Staging: https://medflow-referral-agent-staging-togzrymjsq-ey.a.run.app
- Production: https://medflow-referral-agent-prod-togzrymjsq-ey.a.run.app

[View on GitHub](https://github.com/Keshav0781/medflow-referral-agent)

<br>

### ClinicalRAG: Intelligent Document Search System

A production RAG pipeline for searching Siemens Healthineers clinical documents, deployed as a live REST API on GCP Cloud Run. The system takes a natural language question and returns a precise answer with source references in under 3 seconds.

The retrieval pipeline uses two stages: ChromaDB for semantic search across 834 document chunks, then CrossEncoder reranking to select the best five results. Session-based conversation memory allows follow-up questions to work naturally across multiple turns. Three guardrail rules block medical advice requests and off-topic queries before they reach the LLM. Every query is async-logged to BigQuery with retry logic and exponential backoff so the API response is never delayed by the logging operation.

The Docker setup uses a multi-stage build with a non-root user and went through GCP Container Analysis scanning before deployment. Critical OS vulnerabilities were identified and patched before the service went live.

**Tech Stack:** Python, FastAPI, ChromaDB, LangChain, Groq (Llama 3.3 70B), Docker, GCP Cloud Run, BigQuery

**Live API:** https://clinical-rag-service-324111066236.europe-west1.run.app/docs

[View on GitHub](https://github.com/Keshav0781/clinical-rag)

<br>

### OCT Biomarker Segmentation: Master's Thesis

Multi-class segmentation of retinal biomarkers in OCT scans for automated detection of Age-related Macular Degeneration and Macular Hole. The work compared multiple U-Net variants against nnU-Net across two clinical datasets, with full methodology documentation and quantitative evaluation. This is the foundation that the SAM fine-tuning project below builds on directly.

**Tech Stack:** Python, PyTorch, nnU-Net, U-Net, Medical Imaging

[View on GitHub](https://github.com/Keshav0781/OCT-Biomarker-Segmentation)

<br>

### SAM Fine-tuning with LoRA: OCT Biomarker Segmentation

An extension of the thesis work, exploring whether a large vision foundation model could outperform task-specific architectures with the right adaptation strategy. SAM performs poorly on medical scans without fine-tuning: zero-shot IoU of 0.27 on AMD OCT images. Fine-tuning with LoRA adapters, which trains only a small fraction of the model parameters, brought that to 0.86. On Macular Hole the result was similar, from 0.20 to 0.89.

The approach is practically relevant because annotated medical imaging data is always limited. A method that achieves strong performance with few trainable parameters has real clinical value.

**Tech Stack:** Python, PyTorch, SAM, LoRA (HuggingFace PEFT), Medical Imaging

[View on GitHub](https://github.com/Keshav0781/OCT-SAM-FineTuning-LoRA)

<br>

### Supply Chain Operations Analytics

An end-to-end analytics case study on four years of daily delivery operations data from Munich. The work covers SLA performance analysis, order volume forecasting across four models (Holt-Winters achieved MAPE 4.70%), driver capacity planning, and revenue impact quantification. The analysis identified 5.7 million euros in lost commission from SLA failures and translated that into operational recommendations across three planning scenarios.

The structure of this analysis reflects the kind of work done at Accenture on BestBuy's operations data: order lifecycle tracking, fulfilment metrics, and capacity planning applied here with full end-to-end documentation.

**Tech Stack:** Python, Prophet, SARIMA, Holt-Winters, Pandas, Scikit-learn, Matplotlib

[View on GitHub](https://github.com/Keshav0781/Munich-Delivery-Forecasting-Analysis)

<br>

## Contact

**LinkedIn:** https://www.linkedin.com/in/keshav-jha-11899b255/

**Email:** iamkeshav0781@gmail.com
