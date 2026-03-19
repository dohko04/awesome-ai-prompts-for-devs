# 🔒 Open-Source AI Governance Checker

> Audit your open-source AI dependencies for governance, security, and compliance risks (IBM/PyTorch 2026 framework).

## The Prompt

```
You are an Open-Source AI Governance Auditor. Analyze my project's AI stack 
for governance risks, following IBM's 2026 open-source AI governance framework 
(security-audited releases, transparent data pipelines, interoperability standards).

## My Stack
- Models: [LIST_MODELS — e.g., Llama 4, Mistral Small 4, Qwen 3.5]
- Frameworks: [LIST — e.g., PyTorch 2.8, LangChain, vLLM]
- Deployment: [ENVIRONMENT — cloud/on-prem/hybrid]

## Audit Tasks

1. **License Compliance Matrix**
   - For each model/framework: license type, commercial use OK?, attribution needed?
   - Flag any GPL/AGPL contamination risks
   - Output as a table

2. **Security Posture Check**
   - Does each dependency have signed releases?
   - Known CVEs in current versions?
   - Supply chain risk score (1-10)

3. **Data Provenance**
   - Training data transparency for each model (documented? auditable?)
   - GDPR/CCPA implications
   - Flag models with opaque data pipelines

4. **Interoperability Assessment**
   - ONNX/GGUF export support?
   - Vendor lock-in risk (1-10)
   - Migration difficulty if switching providers

Output a governance report card with RED/YELLOW/GREEN ratings per component.
```

## When to Use

- Before adopting open-source AI models in production
- Quarterly governance reviews of your AI stack
- Compliance preparation (SOC2, ISO 27001, EU AI Act)

## Example Output

A structured report card with license matrix, security scores, data provenance ratings, and interoperability assessments for your entire AI stack.

## Limitations (Free Version)

- Manual review (no automation scripts)
- Basic scoring without remediation steps

---

### 🔥 Want automated governance?

The **PRO version** includes:
- Python scanner that auto-audits your requirements.txt / pyproject.toml
- License conflict detector with dependency tree visualization
- CVE monitor with Slack/Discord alerts
- SBOM generator (CycloneDX format for compliance)
- Quarterly review automation with diff reports

**[Get AI Dev Toolkit — $9 → 218 production-ready resources](https://ai-dev-toolkit-five.vercel.app)**
