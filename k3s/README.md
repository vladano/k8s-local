# K3s

K3s is a **lightweight, CNCF-certified Kubernetes distribution**.

It is ideal for:

- Local development with _production-like behavior_
- Edge and IoT environments
- Low-resource machines
- Learning Kubernetes closer to real-world setups

Unlike Minikube or Kind, **K3s is not “Kubernetes in a wrapper”** — it _is_ Kubernetes, just simplified.

---

## 🧠 How K3s Works

K3s:

- Runs Kubernetes components as a **single binary**
- Uses **containerd** by default
- Replaces heavy dependencies with lightweight alternatives
- Disables non-essential features unless explicitly enabled

```bash
+-----------------------------+
|         Linux Host          |
|                             |
|   k3s (single binary)       |
|    │                        |
|    ├── API Server           |
|    ├── Controller Manager   |
|    ├── Scheduler            |
|    ├── containerd           |
|    └── CoreDNS              |
|                             |
|   (Optional)                |
|   └── Traefik / ServiceLB   |
+-----------------------------+
```

This makes K3s:

- Fast to start
- Easy to operate
- Suitable beyond local development

---

## 📌 Prerequisites

✔️ Linux or macOS (Linux preferred)  
✔️ Root or sudo access  
✔️ Recommended resources:

- 1–2 CPUs
- 2GB RAM minimum

> ⚠️ K3s is not officially supported on Windows without WSL.

---

## ⚙️ Installation

### Install K3s (Single-node)

Install with the official script:

```bash
curl -sfL https://get.k3s.io | sh -
```
