# net-trace: Multi-Layer Federated Fraud Intelligence


Enterprise-grade, privacy-safe mule account detection using Temporal Multi-Layer Trust Graphs and Federated Learning.

---

## The Problem

Modern cross-channel fraud and mule networks operate across multiple banks, devices, and payment rails.

Traditional rule-based engines fail because they:

- Analyze transactions in isolated silos  
- Lack visibility into device and behavioral context  
- Cannot detect cross-bank fraud rings due to strict data privacy laws preventing PII sharing  
- React only after money has already been withdrawn  

Fraud today is coordinated network behavior — not isolated transactions.

---

## The Solution

**NetTrace** replaces static rules with a **Temporal Multi-Layer Trust Graph**.

By fusing financial flow, device access, behavioral patterns, and KYC data, we model the exact **Behavioural DNA** of an account.

Using **Federated Graph Learning**, multiple banks collaboratively detect cross-network mule rings by sharing mathematical model gradients — without ever exposing raw customer data.

---

## Core Innovations & Architecture

### Multi-Layer Graph Attention Network (GAT)

We construct a 4-dimensional temporal graph:

- **Layer 1 – Financial Flow:** Account → Account transfers  
- **Layer 2 – Device & Access:** Account → Device → IP / SIM  
- **Layer 3 – Behaviour:** Session patterns, velocity, geo-shifts  
- **Layer 4 – KYC & Entities:** PAN, Phone, Address, Linked Entities  

Cross-layer attention fusion allows the model to detect coordinated fraud signals across dimensions.

---

### Behavioural DNA Fingerprinting (BDNA)

Each account is represented as a dynamic behavioral vector.

When compromised or acting as a mule, the system detects **Behaviour Drift** using Cosine Similarity:
     ** D_drift = 1 - ( V_baseline · V_current ) / ( ||V_baseline|| ||V_current|| )**

An alert is triggered when `D_drift` crosses a dynamic risk threshold — enabling intent detection before full chain completion.

---

### Transaction Complexity Score (TCS)

Instead of flagging only high transaction velocity, we quantify structural laundering behavior.
    TCS = ( H × W̄_J ) × ( 1 + F_index ) × e^(λ P_loop)

Where:

- `H` = number of hops (depth of fund movement)  
- `W̄_J` = jurisdiction risk weight  
- `F_index` = fragmentation score  
- `P_loop` = probability of circular routing  

This identifies 3–5 hop laundering loops instantly.

---

### Real-Time Risk Propagation Engine

Risk spreads dynamically through the graph using a heat-diffusion inspired model.
    R_i(t+1) = α R_i(t) + (1 - α) Σ ( w_ij R_j(t) )

If one node is flagged, connected nodes immediately update their risk profile.

This enables ring-level detection instead of isolated alerts.

---

### Privacy-Safe Federated Intelligence

Banks train local GNN models on private data.

Only model gradients are shared with the SentinelGraph central aggregator.

Result:

- Cross-bank mule ring detection  
- Zero raw data sharing  
- Full regulatory compliance  
- Privacy preserved by design  

---

## Real-Time Pipeline

1. Event Ingestion (Apache Kafka)  
2. Multi-Layer Graph Update (Neo4j)  
3. GNN Inference (PyTorch Geometric)  
4. Risk Propagation + BDNA + TCS Calculation  
5. Alert Generation & Auto-Freeze API  

Target inference latency: **< 300 ms**

---

##  Tech Stack

| Component | Technology |
|------------|------------|
| Data Ingestion | Apache Kafka |
| Graph Database | Neo4j |
| Model Training | PyTorch Geometric (GNNs) |
| Federated Server | Flower / TensorFlow Federated |
| Deployment | Docker / Kubernetes |

---

## 📂 Repository Structure

> Active development underway. Core modules follow this structure:
data_pipeline/ # Kafka ingestion & Neo4j connectors
models/ # Multi-Layer GAT definitions (PyTorch Geometric)
federated_server/ # Gradient aggregation logic
explainability_ui/ # XAI dashboard + API endpoints
notebooks/ # BDNA & TCS mathematical modeling


---

## Explainability & Compliance

NetTrace is built for regulators and audit teams.

The system provides:

- Risk factor breakdown (velocity, device reuse, routing complexity, jurisdiction)
- Highlighted suspicious fund flow paths
- Ring centrality ranking
- Automated Suspicious Activity Report (SAR) drafts
- Cryptographic audit logs for model decisions

No black-box decisions. Full transparency.

---

## Vision

From Transaction Monitoring  
To Network Intelligence  

NetTrace transforms fraud detection from reactive rule engines into proactive, privacy-safe, graph-based risk intelligence.
