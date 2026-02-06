# Summarisation-of-Medical-Report-LLM-
# Overview
This project presents an end-to-end Medical Text Intelligence Pipeline that combines:
- Large Language Models (LLMs) for medical report summarization
- BERTopic for unsupervised clinical topic discovery
- Bidirectional feedback between LLMs and topic modeling
- Treatment extraction and criticality scoring
- Evaluation using ROUGE and BERTScore
The system is designed to transform long, unstructured medical reports into concise, interpretable, and decision-ready insights, making it suitable for:
- Healthcare administrators
- Policy and strategy teams
- Non-technical stakeholders
- Clinical data analysts
- Health-tech solution providers
# Problem Statement
Healthcare institutions generate large volumes of free-text medical reports, which are:
- Time-consuming to read
- Difficult to analyze at scale
- Hard to summarize consistently
- Poorly structured for analytics and decision-making
Non-clinical stakeholders often struggle to extract meaningful insights from these reports.
# Solution
This project introduces a closed-loop NLP system where:
- LLMs enhance topic modeling, and topic modeling enhances LLM summarization
- The result is a system that:
- Produces context-aware medical summaries
- Discovers latent clinical themes
- Identifies treatments and interventions
- Assigns criticality scores for prioritization
- Communicates insights clearly to non-technical audiences
# System Architecture
Raw Medical Reports (Free Text)
        ↓
Text Cleaning & Preprocessing
        ↓
LLM-Based Medical Summarization (DistilBART)
        ↓
BERTopic Topic Modeling
        ↓
Topic → LLM Feedback Loop
        ↓
Refined Summaries + Topic-Aware Context
        ↓
Treatment Extraction & Criticality Scoring
        ↓
Evaluation & Visualization
# LLM → BERTopic (future improvement)
- LLM generates high-quality summaries from long medical reports
- These summaries reduce noise and redundancy
- BERTopic performs more stable and interpretable topic modeling
# BERTopic → LLM
BERTopic identifies:
- Dominant clinical themes
- Topic probabilities (confidence)
- Topic context is fed back into the LLM prompt:
- Improves focus
- Reduces hallucination
- Enables topic-aware summarization
This mutual reinforcement loop ensures smoother execution, better interpretability, and higher trust in outputs.
# Data Preprocessing
- Removal of missing or empty reports
- Text normalization (line breaks, spacing)
- Tokenization using NLTK
- Chunking for long medical documents (1024 token limit)
# Medical Summarization
Model Used:
* DistilBART (CNN-12-6)
* Fine-tuned for abstractive summarization
# Key Features
* Handles long documents via chunking
* Optional demographic context:
- Age
- Gender
- Structured clinical prompts
- Multi-pass summarization for long reports
# Topic Modeling with BERTopic
Models
- SentenceTransformer: all-MiniLM-L6-v2
- Vectorizer: CountVectorizer (English stopwords)
Outputs
- Topic clusters
- Topic probability scores
- Topic similarity heatmaps
- Interactive topic visualizations
# Treatment Mention Extraction
Using rule-based NLP patterns, the system extracts sentences containing:
* Medications
* Therapies
* Surgical procedures
* Radiation / chemotherapy
* Clinical interventions
This helps identify what was done, not just what was diagnosed.
# Criticality Scoring
Each report receives a criticality score derived from:
- BERTopic topic probability
- Degree of treatment mentions
This enables:
* Case prioritization
* Risk stratification
* Operational triaging
# Evaluation Metrics
Metric	Score
ROUGE-1	0.2328
ROUGE-2	0.1759
ROUGE-L	0.2176
BERTScore (F1)	0.5597
# Value to the Health Sector
- For Healthcare Management
- Faster understanding of patient reports
- Prioritization of critical cases
- Operational efficiency
For Policy & Strategy Teams
- Aggregated clinical trends
- Evidence-driven decision-making
- Resource planning
For Health-Tech & AI Teams
- Modular, extensible NLP pipeline
- Easily deployable components
- Research-grade evaluation
# Areas for Improvement & Future Work
Technical Enhancements
- Fine-tune summarization model on clinical datasets (e.g., MIMIC-III)
- Replace keyword-based treatment extraction with Named Entity Recognition (NER)
- Use topic-conditioned prompts systematically
- Introduce temporal modeling for patient history
 Model Improvements
* Domain-specific clinical LLMs (BioBERT, ClinicalBERT)
* Reinforcement learning from clinician feedback
* Hierarchical topic modeling
Product & Deployment
- REST API for hospital systems
- Interactive dashboard (Streamlit / Power BI)
- Real-time report ingestion
- Secure cloud deployment (HIPAA-aware)
# Ethical & Clinical Considerations
This system is decision-support, not diagnostic
* Outputs should always be reviewed by qualified professionals
* Patient identifiers should be anonymized
* Complies with responsible AI principles
