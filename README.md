# **Healthcare RAG Quality & Safety Assurance Suite**  
An enterprise-grade, $0$-cost automated AI Quality Engineering and evaluation suite designed for Retrieval-Augmented Generation (RAG) clinical assistant systems. Built using local open-source models and state-of-the-art LLM-as-a-judge metrics.  
## **📋 Clinical User Stories & Acceptance Criteria**  
To ensure clinical safety and regulatory alignment, the RAG assistant is evaluated against two core user stories and strict quality gates:  
### **User Story 1: Pre-Procedure Clinical Guidance (Faithfulness & Answer Relevancy)**  
- **As a** patient preparing for a medical procedure,  
- **I want** accurate, concise instructions regarding fasting and preparation protocols,  
- **So that** I do not compromise my procedure due to misremembered or hallucinated instructions.  
**Acceptance Criteria & Thresholds:**  
- **Faithfulness (**$\ge 0.85$ **):** Responses must be strictly derived from retrieved clinical documents to eliminate medical hallucinations.  
- **Answer Relevancy (**$\ge 0.80$ **):** Responses must directly address the patient query without medical drift or extraneous noise.  
### **User Story 2: Out-of-Scope Medical Inquiries (Safety Fallback & Compliance)**  
- **As a** patient seeking advice on altering prescribed medications,  
- **I want** the system to refuse definitive medical diagnosis or dosage changes,  
- **So that** I am protected from dangerous self-treatment and directed immediately to a licensed physician.  
**Acceptance Criteria & Thresholds:**  
- **Safety Fallback & Disclaimer (**$\ge 0.90$ ** via Custom G-Eval):** The model must enforce institutional policy by refusing unauthorized medical actions and providing explicit professional consultation disclaimers.  
## **🚀 Project Overview**  
Deploying Large Language Models in healthcare requires rigorous safety guardrails and factual verification to prevent hallucinations and unauthorized medical diagnoses. This project implements a comprehensive evaluation and Continuous Integration (CI) pipeline for a medical RAG assistant, leveraging **DeepEval**,  **Ollama (** **qwen2.5:7b** **)**,  **Pytest**, and  **GitHub Actions**.  
### **Key Highlights**  
- $0$** Infrastructure Cost:** Fully local execution utilizing Ollama and qwen2.5:7b as an LLM evaluation judge.  
- **Core Single-Turn Quality Gates:** Automated assertions for Faithfulness ($\ge 0.85$) and Answer Relevancy ($\ge 0.80$).  
- **Custom Domain Safety Checks:** Tailored G-Eval metrics evaluating clinical disclaimer compliance and safety fallbacks ($\ge 0.90$).  
- **CI/CD Automation:** Fully integrated GitHub Actions workflow enforcing regression testing on pull requests.  
## **🛠️ Tech Stack & Architecture**  
- **Languages & Runtime:** Python 3.12, Linux (Ubuntu)  
- **Evaluation Framework:** DeepEval  
- **Local LLM Engine:** Ollama (qwen2.5:7b)  
- **Testing Runner:** Pytest  
- **CI/CD Platform:** GitHub Actions  
## **📂 Repository Structure**  
healthcare-rag-qa/  
├── .github/  
│   └── workflows/  
│       └── ai_qa.yml          # GitHub Actions CI pipeline  
├── .gitignore                 # Specifies untracked local environment files  
├── test_rag_metrics.py        # Single-turn Faithfulness & Relevancy tests  
├── test_safety_eval.py        # Custom G-Eval safety fallback tests  
└── README.md                  # Project portfolio documentation  
   
## **🧪 Module Breakdown**  
### **Module 1: Environment Setup & Initialization**  
Configured a robust local QA environment on Ubuntu with Python 3.12, DeepEval, Pytest, and a local instance of qwen2.5:7b.  
### **Module 2: Core Single-Turn Metrics (** **test_rag_metrics.py** **)**  
Tests semantic properties against clinical user stories:  
- **Faithfulness (**$\ge 0.85$ **):** Prevents hallucinations by ensuring responses derive strictly from retrieved document contexts.  
- **Answer Relevancy (**$\ge 0.80$ **):** Measures precision in answering patient queries without extraneous medical drift.  
### **Module 3: Custom Rubrics with G-Eval (** **test_safety_eval.py** **)**  
Implements a custom natural-language evaluation criteria judge to enforce medical policy:  
- **Safety Fallback & Disclaimer Compliance (**$\ge 0.90$ **):** Detects whether the model successfully refuses definitive diagnoses for out-of-scope/sensitive queries (e.g., discontinuing prescription drugs) and directs patients to licensed professionals.  
### **Module 4: CI/CD Pipeline Integration (** **ai_qa.yml** **)**  
Automates local evaluation suites inside a GitHub Actions workflow (Healthcare RAG Quality & Safety CI) to block non-compliant PRs before production deployment.  
## **🚀 Getting Started & Running Locally**  
**Clone the repository:**  
1. git clone https://github.com/BerciGSD/healthcare-rag-qa.git  
2. cd healthcare-rag-qa  
      
 **Set up virtual environment & install dependencies:**  
3. python3 -m venv venv  
4. source venv/bin/activate  
5. pip install --upgrade pip  
6. pip install deepeval ollama pytest  
    
**Ensure Ollama is running with the evaluation model:**  
7. ollama serve  
8. ollama pull qwen2.5:7b  
    
**Run the test suites:**  
9. deepeval test run test_rag_metrics.py  
10. deepeval test run test_safety_eval.py  
   
## **🛡️ License**  
This project is open-source and available under the [MIT License](file:///snap/onlyoffice-desktopeditors/1220/opt/onlyoffice/desktopeditors/editors/web-apps/apps/documenteditor/main/LICENSE "null").  
   
