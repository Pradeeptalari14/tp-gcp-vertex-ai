# GCP Vertex AI Model Registry Studio

This repository contains the target configuration and SRE runtime files compiled by the **GCP Vertex AI Model Registry Studio** dashboard module.

## 🚀 Description
Deploy and track models in Vertex AI Model Registry. Generate batch prediction pipelines, model endpoint deployment specifications, and IAM service account bindings.

## 🛠️ Specification Matrix
- **Primary Configuration File**: `/scripts/vertex_deploy.py`
- **Execution Command**: `python3 vertex_deploy.py`
- **Validation Command**: `python3 vertex_deploy.py --check`

## 📋 How to Run & Validate

1. **Clone the repository:**
   ```bash
   git clone https://github.com/Pradeeptalari14/tp-gcp-vertex-ai.git
   cd tp-gcp-vertex-ai
   ```

2. **Run Execution Target:**
   ```bash
   python3 vertex_deploy.py
   ```

3. **Verify Runtime Stability:**
   ```bash
   python3 vertex_deploy.py --check
   ```

## 🔐 Security & Best Practices
* **Secret Isolation**: Use organization-level secrets (or SSM parameter hooks) rather than hardcoded environment variables inside files.
* **Pull Request Lifecycles**: Protect default branch merges with validation checks before merging code changes.
