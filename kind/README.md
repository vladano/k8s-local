# 📗 Kind (Kubernetes in Docker)

Kind runs **Kubernetes clusters inside Docker containers**.

It is ideal for:

- CI pipelines
- Fast, reproducible Kubernetes clusters
- Multi-node local testing
- Testing Kubernetes upgrades and manifests

Kind is **not** designed for beginners or UI-driven workflows — Minikube fits that role better.

---

## 🧠 How Kind Works

Kind runs each Kubernetes node as a **Docker container**.

- Control plane = Docker container
- Worker nodes = Docker containers
- Networking = Docker bridge
- Storage = ephemeral by default

```text
+----------------------------+
|        Your Machine        |
|                            |
|    kubectl                 |
|      │                     |
|      ▼                     |
|    Docker                  |
|      │                     |
|      ├── Control Plane Node|
|      │ (Docker container)  |
|      │                     |
|      ├── Worker Node       |
|      │ (Docker container)  |
|      │                     |
|      └── Worker Node       |
|          (Docker container)|
+----------------------------+
```

This makes Kind:

- Fast to create and destroy
- Perfect for automation
- Very close to real Kubernetes behavior

---

## 📌 Prerequisites

Before using Kind:

✔️ Docker installed and running  
✔️ kubectl installed  
✔️ Recommended system resources:

- 4GB RAM
- 2 CPUs minimum

> ⚠️ Kind will not work without Docker.

---

## ⚙️ Installation

### Install Kind

On Linux/macOS:

```bash
curl -Lo ./kind https://kind.sigs.k8s.io/dl/latest/kind-linux-amd64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind
```
