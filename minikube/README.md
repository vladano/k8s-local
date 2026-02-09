---

## 📗 `minikube/README.md`

# Minikube

Minikube runs a **local single-node Kubernetes cluster** on your machine.

It’s ideal for:
- Learning Kubernetes fundamentals
- Trying addons (Ingress, metrics)
- Local development workflows

It is **not** a production solution or CI-centric tool — use Kind or K3s for those.

---

## 🧠 How Minikube Works

Minikube starts Kubernetes inside a lightweight VM or container runtime on your system. You interact with the cluster using `kubectl` — just like with any remote cluster.

```bash
+---------------------------+
|        Your Machine       |
|                           |
|   kubectl                 |
|      │                    |
|      ▼                    |
|   Minikube                |
|      │                    |
|      ▼                    |
|   VM / Container Runtime  |
|      │                    |
|      ▼                    |
| Single Kubernetes Node    |
| (Control Plane + Worker)  |
+---------------------------+
```

Before installing, ensure you have virtualization enabled on your system (BIOS/UEFI).

---

## 📌 Prerequisites

Before installing Minikube:

1. Windows
   Prerequisites
   Windows 10/11 64-bit (Pro, Enterprise, or Education recommended)
   Hyper-V or VirtualBox installed
   kubectl (Kubernetes CLI)
   Chocolatey (optional, simplifies installation)

Steps:
Step 1: Install a Hypervisor
For Hyper-V:
Open PowerShell as Administrator.
Run:

```bash
    dism.exe /Online /Enable-Feature:Microsoft-Hyper-V /All
```

    Restart your computer.

    For VirtualBox:
        Download from https://www.virtualbox.org
        and install.
        Ensure virtualization is enabled in BIOS.

Step 2: Install Minikube
Using Chocolatey:

```bash
    choco install minikube -y
```

    Without Chocolatey:
        Download the executable: Minikube Releases
        Add the folder containing minikube.exe to your PATH.

Step 3: Install kubectl
Using Chocolatey:

```bash
    choco install kubernetes-cli -y
```

    Or manually:

```bash
    kubectl install guide
```

Step 4: Start Minikube

# start minikube inside HyperV

```bash
    minikube start --driver=hyperv
```

# or start minikube inside Virtual Box

```bash
    minikube start --driver=virtualbox
```

Step 5: Check status

```bash
    minikube status
    kubectl get nodes
```

Step 6: Enable Addons (Optional)

```bash
    minikube addons enable dashboard
    minikube addons enable metrics-server
```

---

2. Linux (Ubuntu/Debian)
   Prerequisites
   Virtualization enabled (KVM, VirtualBox, or Docker)
   curl or wget
   kubectl installed

Steps:
Step 1: Install dependencies

```bash
    sudo apt update
    sudo apt install -y curl wget apt-transport-https conntrack socat
```

Step 2: Install a hypervisor
Docker (recommended for Linux):

```bash
    sudo apt install -y docker.io
    sudo systemctl enable --now docker
    sudo usermod -aG docker $USER
```

# Or VirtualBox:

```bash
    sudo apt install -y virtualbox
```

Step 3: Install Minikube

```bash
    curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
    sudo install minikube-linux-amd64 /usr/local/bin/minikube
```

Step 4: Install kubectl

```bash
    curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
    chmod +x kubectl
    sudo mv kubectl /usr/local/bin/
```

Step 5: Start Minikube

```bash
    minikube start --driver=docker
```

# Or for VirtualBox:

```bash
    minikube start --driver=virtualbox
```

Step 6: Verify

```bash
    minikube status
    kubectl get nodes
```

Common Tips:

# Switch Kubernetes versions

```bash
    minikube start --kubernetes-version=v1.27.0
```

# Delete a cluster

```bash
    minikube delete
```

# SSH into Minikube VM

```bash
    minikube ssh
```

# Check Minikube logs

```bash
    minikube logs
```

✅ Result:
After these steps, you should have a fully working local Kubernetes cluster on Windows or Linux ready for development and testing.

# 🚀 Start Your First Cluster

Start Minikube with:

```bash
minikube start
```

Verify:

```bash
kubectl get nodes
```

If you see a node in Ready state — your cluster is running.

# 🛠 Useful Addons

Minikube supports built-in addons. Enable them with:

```bash
minikube addons enable ingress
minikube addons enable metrics-server
```

Examples:
Ingress: helps test Ingress controllers locally
Metrics Server: enables resource metrics (for kubectl top)

# ⚠️ Common Issues & Fixes

⛔ Minikube fails to start
Try:

```bash
minikube delete
minikube start --driver=docker
```

Ensure Docker has:
Enough memory
Enough CPUs

❌ kubectl can’t connect
Set context explicitly:

```bash
kubectl config use-context minikube
```

# 🪄 Everyday Commands

```bash
minikube status               # Show cluster status
minikube dashboard            # Open UI dashboard
minikube kubectl -- get pods  # kubectl via minikube
```

## Summary Table for minikube commands:

| Command          | Purpose                               |
| ---------------- | ------------------------------------- |
| `start`          | Start a local Kubernetes cluster      |
| `stop`           | Stop the cluster (preserves state)    |
| `delete`         | Delete the cluster permanently        |
| `restart`        | Restart the cluster                   |
| `status`         | Show cluster status                   |
| `ip`             | Get cluster/node IP address           |
| `version`        | Print Minikube version                |
| `logs`           | Get cluster debug logs                |
| `addons`         | Enable/disable/list add-ons           |
| `dashboard`      | Open the Kubernetes Dashboard         |
| `config`         | Manage persistent configuration       |
| `profile`        | Manage multiple cluster profiles      |
| `update-context` | Fix kubeconfig after IP/port change   |
| `update-check`   | Check for Minikube updates            |
| `node`           | Add/remove/list cluster nodes         |
| `service`        | Access Kubernetes services            |
| `tunnel`         | Expose LoadBalancer services locally  |
| `ssh`            | SSH into the Minikube node            |
| `ssh-key`        | Get SSH key path for the node         |
| `ssh-host`       | Get SSH host key for the node         |
| `docker-env`     | Configure Docker CLI for Minikube     |
| `podman-env`     | Configure Podman CLI for Minikube     |
| `image`          | Build/load/list/remove images         |
| `cache`          | Manage local image cache              |
| `cp`             | Copy files into the node              |
| `mount`          | Mount a local directory into the node |
| `pause`          | Pause all workloads                   |
| `unpause`        | Resume paused workloads               |
| `kubectl`        | Run cluster-matched kubectl           |
| `completion`     | Generate shell completion script      |
| `help`           | Show help                             |
| `options`        | Show global flags                     |
| `license`        | Output dependency licenses            |

---

_Source: [Official Minikube Command Reference](https://minikube.sigs.k8s.io/docs/commands/)_
