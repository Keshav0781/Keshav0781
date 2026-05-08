# Keshav Jha

AI Engineer and Data Scientist based in Erlangen, Germany. Currently completing an M.Sc. in Data Science at Friedrich-Alexander University Erlangen-Nuremberg.

Before my Master's, I spent 4.5 years at Accenture as a Senior Analyst — building demand forecasting systems, operational analytics pipelines, and data-driven solutions for large retail clients. During my studies I worked part-time at Siemens Healthineers on machine learning models, Power BI dashboards, and AI-driven solutions for medical imaging.

My work sits at the intersection of AI engineering and applied data science. On one side, production systems — RAG pipelines, LLM APIs, cloud deployment on GCP. On the other, deep learning research — medical image segmentation, foundation model fine-tuning with LoRA. Both require the same discipline: understanding the problem well, building something that actually works, and being honest about the tradeoffs.

---

## What I Work With

Python is my primary language. On the AI engineering side: LangChain, ChromaDB, sentence-transformers, FastAPI, Docker, GCP Cloud Run, BigQuery. On the deep learning side: PyTorch, U-Net, nnU-Net, SAM, LoRA adapters via HuggingFace PEFT. For data and forecasting work: Pandas, Scikit-learn, Prophet, Statsmodels, Power BI, SQL. Cloud experience across GCP and Azure.

---

## Projects

### OCT Biomarker Segmentation — Master's Thesis

Multi-class segmentation of retinal biomarkers in OCT scans for automated detection of Age-related Macular Degeneration and Macular Hole. The work compared multiple U-Net variants against nnU-Net across two clinical datasets, with full methodology documentation and quantitative evaluation. This is the foundation that the SAM fine-tuning project below builds on directly.

[GitHub](https://github.com/Keshav0781/OCT-Biomarker-Segmentation)

---

### SAM Fine-tuning with LoRA — OCT Biomarker Segmentation

An extension of the thesis work exploring whether a large vision foundation model could outperform task-specific architectures with the right adaptation approach. SAM performs poorly on medical scans out of the box — zero-shot IoU of 0.27 on AMD OCT images. Fine-tuning it using LoRA adapters, which trains only a small fraction of the model's parameters, brought that number to 0.86. On Macular Hole the improvement was similar: 0.20 to 0.89.

The result is significant because annotated medical imaging data is always scarce. A method that achieves strong performance with limited trainable parameters and limited data has real clinical relevance.

[GitHub](https://github.com/Keshav0781/OCT-SAM-FineTuning-LoRA)

---

### ClinicalRAG — Intelligent Document Search System

A production RAG pipeline for searching Siemens Healthineers clinical documents, deployed as a live REST API on GCP Cloud Run. The system takes a natural language question and returns a precise answer with source references in under 3 seconds.

The retrieval pipeline uses two stages — ChromaDB for semantic search across 834 document chunks, then CrossEncoder reranking to select the best five results. Session-based conversation memory allows follow-up questions to work naturally across multiple turns. Three guardrail rules block medical advice requests and off-topic queries before they reach the LLM. Every query is async-logged to BigQuery with retry logic and exponential backoff so the API response is never delayed by logging.

The Docker setup uses a multi-stage build with a non-root user and went through GCP Container Analysis scanning before deployment — critical OS vulnerabilities were identified and patched before the service went live.

Live API: https://clinical-rag-service-324111066236.europe-west1.run.app/docs

[GitHub](https://github.com/Keshav0781/clinical-rag)

---

### Supply Chain Operations Analytics

An end-to-end analytics case study on four years of daily delivery operations data from Munich. The work covers SLA performance analysis, order volume forecasting across four models (Holt-Winters achieved MAPE 4.70%), driver capacity planning, and revenue impact quantification. The analysis identified 5.7 million euros in lost commission from SLA failures over four years and translated that into concrete operational recommendations.

This is the type of analysis done regularly during my time at Accenture — structured problem framing, rigorous methodology, and results that connect directly to business decisions.

[GitHub](https://github.com/Keshav0781/Munich-Delivery-Forecasting-Analysis)

---

## Get in Touch

LinkedIn: https://www.linkedin.com/in/keshav-jha-11899b255/

Email: iamkeshav0781@gmail.com
