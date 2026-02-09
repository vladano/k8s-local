# k8s-local

A practical, clear, and opinionated guide for running **Kubernetes locally** using:

- **Minikube**
- **Kind**
- **K3s**

This repository focuses on hands-on installation, configuration steps, common pitfalls, and real-world tips — so you don’t have to piece things together from multiple sources.

---

## 🚀 Why this Repo Exists

Local Kubernetes environments are essential for:

- Learning Kubernetes
- Testing manifests and Helm charts
- Developing cloud-native applications
- Exploring networking, Ingress, and storage plugins

But the ecosystem has multiple tools — each with trade-offs. This repo helps you:

- Pick the **right tool for your needs**
- Install and configure it correctly
- Understand “why” and not just “how”

---

## 🧠 Local Kubernetes: Mental Model

Each tool in this repo targets a different use case:

| Tool     | Best For                               |
| -------- | -------------------------------------- |
| Minikube | Beginners, addons, single-node cluster |
| Kind     | Kubernetes-in-Docker, CI testing       |
| K3s      | Lightweight clusters, edge-style uses  |

---

## 📁 Repo Structure

```text
k8s-local/
├── minikube/
│   ├── README.md
│   └── examples/
├── kind/
│   ├── README.md
│   └── examples/
├── k3s/
│   ├── README.md
│   └── examples/
└── docs/
    └── comparison.md
```
