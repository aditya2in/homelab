# 🏠 HomeLab — Kubernetes Platform

A **6-node bare-metal Kubernetes homelab** built for deep, hands-on learning of Linux, networking, containers, and Kubernetes — mapped 1:1 to the **CKAD → CKA → CKS** certification path.

> ## ⚠️ PUBLIC REPOSITORY — NO SECRETS, NO REAL ADDRESSES
> This repository is intentionally **public** as a portfolio / showcase.
> - **No credentials** are ever committed: kubeconfigs, tokens, keys, certificates, and `.env` files are excluded via `.gitignore`.
> - **No real network addresses** are published. Hostnames and IP addresses are omitted or replaced with documentation placeholders.
> - Real topology details live only in the private vault.

---

## 🛰️ Cluster Topology

```text
ROLE               NODE           SPEC
────────────────── ─────────────  ─────────────────────────────
Cluster endpoint   vip            HAProxy + Keepalived (HA)
Control plane      master01       16 GB RAM
Control plane      master02       16 GB RAM
Control plane      master03       16 GB RAM
Worker             worker01       16 GB RAM
Worker + dev       gpuworker01    RTX 3060 · workstation
Worker + GPU       gpuworker02    RTX 3060
```

| Node | Role | Notes |
| :--- | :--- | :--- |
| `vip` | Cluster Endpoint | HAProxy + Keepalived |
| `master01` | Control Plane | 16 GB RAM |
| `master02` | Control Plane | 16 GB RAM |
| `master03` | Control Plane | 16 GB RAM |
| `worker01` | Worker | 16 GB RAM |
| `gpuworker01` | Worker + Workstation | RTX 3060 · dev environment |
| `gpuworker02` | Worker + GPU | RTX 3060 |

```text
                    ┌─────────────────┐
                    │      vip        │
                    │ HAProxy+Keepalv │
                    └────────┬────────┘
             ┌───────────────┼───────────────┐
        ┌────┴────┐     ┌────┴────┐     ┌────┴────┐
        │master01 │     │master02 │     │master03 │
        └────┬────┘     └────┬────┘     └────┬────┘
             └───────────────┼───────────────┘
             ┌───────────────┼───────────────┐
        ┌────┴────┐     ┌────┴────┐     ┌────┴────┐
        │worker01 │     │gpuwork01│     │gpuwork02│
        └─────────┘     └─────────┘     └─────────┘
```

## 🧱 Software Stack

- **Orchestration:** Kubernetes (Vanilla, `kubeadm`)
- **Container Runtime (CRI):** `containerd`
- **Networking (CNI):** Flannel (overlay)
- **High Availability:** HAProxy + Keepalived (stacked topology)
- **OS:** Arch Linux (headless) + Omarchy (workstation)
- **GPU:** NVIDIA RTX 3060 ×2 (drivers + operator)

## 📂 Repository Layout

```text
homelab/
├── cluster/        kubeadm / CRI / CNI / HA configuration
├── manifests/      Kubernetes manifests (one folder per capability)
│   └── capabilities/
├── scripts/        bootstrap, health-check, backup automation
├── docs/           runbooks and engineering notes
└── n8n/            self-hosted n8n automation stack
```

## 🔒 Sanitisation Policy

Because this repository is public:

1. **Addresses are omitted.** Hostnames are generic role names; no IPs, no subnets, no MACs.
2. **Manifests use placeholders** (`<NODE-IP>`, `<TOKEN>`, `<CA-CERT-HASH>`).
3. **Credentials are never committed** — enforced by `.gitignore` and a pre-push scan.
4. Real values are kept only in the private vault. If a value cannot be published safely, it is left out.

```bash
# Pre-push safety scan (run before every push)
git grep -nE "([0-9]{1,3}\.){3}[0-9]{1,3}|kubeconfig|token|\.key|\.pem|\.env" || echo "CLEAN"
```

## 🎯 Purpose

This is not a production cluster — it is a **learning platform**. Every concept studied is implemented here, on real hardware, and committed. The commit history is the study log.

## 📅 Daily Log Discipline

Every homelab session ends with a commit. The history is the proof of work.

---

_Updated: 2026-09-18 IST — Repository created. IP addresses removed for public safety; sanitisation policy added._
