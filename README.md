# 🧠 GCP Vertex AI Model Registry Studio
> Deploy and track models in Vertex AI Model Registry. Generate batch prediction pipelines, model endpoint deployment specifications, and IAM service account bindings.

[![Studio](https://img.shields.io/badge/Developer_Studio-Live-brightgreen)](https://pradeeptalari14.github.io/portfolio/tools/gcp-vertex-ai/)
[![Category](https://img.shields.io/badge/Category-ai-blue)]()

---

## 🎛️ How This Studio Works

Deploy and track models in Vertex AI Model Registry. Generate batch prediction pipelines, model endpoint deployment specifications, and IAM service account bindings.

Open the **[Interactive Studio](${studioUrl})** to configure options and generate files.
Each option combination produces different output — try different settings to learn by example.

## 🏗️ Architecture Flow Diagram

![SRE Architecture Flow](docs/sre_architecture_flow.png)

## 🚀 Step-by-Step Onboarding & Validation Guide

Follow these SRE steps to deploy, validate, and monitor this repository's workspace configs in a local or production environment:

#### 1. Prerequisites
- [x] **Python 3.10+**
- [x] **Docker & Docker Compose**
- [x] **NVIDIA Container Toolkit (optional)**

#### 2. Download
Clone this repository locally:
```bash
git clone https://github.com/Pradeeptalari14/tp-gcp-vertex-ai.git
cd tp-gcp-vertex-ai
```

#### 3. Install
Fetch required packages and compile environment binaries:
```bash
pip install -r requirements.txt || pip install streamlit langchain chromadb fastapi uvicorn
```

#### 4. Enable Automatic Sidecar Injection
Deploy sidecar logging and telemetry containers (e.g. Jaeger agent or Fluentbit) to capture prompt latency and raw model responses.

#### 5. Install Kubernetes Gateway API CRDs
Install Kubernetes Gateway API CRDs to enable canary and load-balanced routing rules between models:
```bash
kubectl apply -f https://raw.githubusercontent.com/kubernetes-sigs/gateway-api/v1.1.0/config/crd/standard/gateway-api-v1.1.0-experimental.yaml
```

#### 6. Deploy Application Workload
Launch the Streamlit app or local FastAPI service mesh:
```bash
streamlit run app.py --server.port 8501
# Or via compose
docker compose up -d
```

#### 7. Validate Application Inside Cluster
Perform standard readiness and health probe checks:
```bash
curl -s -o /dev/null -w "%{http_code}" http://localhost:8501/health || curl -s http://localhost:8501
```

#### 8. Expose Application Using Gateway
Expose Streamlit user interface or gateway router to local dev host:
```bash
kubectl port-forward svc/tp-gcp-vertex-ai 8501:8501
```

#### 9. Access the Application
Access the model playground locally at [http://localhost:8501](http://localhost:8501) and API docs at `/docs`.

#### 10. Install Addons
Install Langsmith/Langfuse tracer proxies and Jaeger telemetry collection agents.

#### 11. Access Dashboard
Access Streamlit web interface or MLflow experiment models tracker on port 5000.

#### 12. View Service Mesh Graph
View the prompt-completion trace trees, agent step flows, and embeddings retrievable lists via web consoles.

#### 13. Generate Traffic
Simulate query traffic to evaluate prompt metrics:
```bash
for i in {1..20}; do curl -X POST -H "Content-Type: application/json" -d '{"prompt": "Test SRE load"}' http://localhost:8501/query; sleep 0.5; done
```

#### 14. Project Structure
```text
tp-tp-gcp-vertex-ai/
├── .gitignore                # Version control exclusions
├── LICENSE                   # MIT Open Source License
├── SECURITY.md               # Vulnerability reporting protocols
├── CHANGELOG.md              # Releases version history
├── README.md                 # Project learning guide & onboarding
├── .env.example              # Template parameters config
├── .pre-commit-config.yaml   # Gitleaks & lint pipeline hooks
├── docs/
│   ├── USAGE.md              # Extended developer usage docs
│   ├── TROUBLESHOOTING.md    # Failures resolution guide
│   ├── GLOSSARY.md           # SRE domain terminology index
│   ├── COMPLIANCE.md         # Legal and security checks checklist
│   └── sre_architecture_flow.png # Category SRE architecture diagram
├── scripts/
│   └── validate.sh           # Local validation helper script
└── .github/
    ├── CONTRIBUTING.md       # Contributing instructions
    ├── PULL_REQUEST_TEMPLATE.md # Pull request code compliance check
    ├── ISSUE_TEMPLATE/       # Bug and features tickets
    ├── dependabot.yml        # Auto updates dependencies
    └── workflows/
        └── security-scan.yml # Gitleaks/yamllint/shellcheck scans

# Primary Config File: vertex_deploy.py
```

#### 15. Observability Components
Exports prometheus metrics for prompt latency, tokens processed count, active model parameters, and error rates.

#### 16. Install Monitoring
Sets up notification thresholds for prompt latencies exceeding 2.0s or health status failures.

## 🔐 Security

- ❌ Never commit real credentials
- ✅ Use environment variables or secret managers
- ✅ Enable branch protection on `main`

## 📖 Resources

| Resource | Link |
|----------|------|
| Interactive Studio | [Open →](https://pradeeptalari14.github.io/portfolio/tools/gcp-vertex-ai/) |
| All 91 Studios | [Dashboard →](https://pradeeptalari14.github.io/portfolio/tools/) |

*Part of [Talari Pradeep Developer Studio Portfolio](https://pradeeptalari14.github.io/portfolio)*