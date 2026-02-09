Minikube is a local Kubernetes cluster that runs in a VM or container on your machine.

Before installing, ensure you have virtualization enabled on your system (BIOS/UEFI).

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
        dism.exe /Online /Enable-Feature:Microsoft-Hyper-V /All
        Restart your computer.

    For VirtualBox:
        Download from https://www.virtualbox.org
        and install.
        Ensure virtualization is enabled in BIOS.

Step 2: Install Minikube
    Using Chocolatey:
    choco install minikube -y
    Without Chocolatey:
        Download the executable: Minikube Releases
        Add the folder containing minikube.exe to your PATH.

Step 3: Install kubectl
    Using Chocolatey:
    choco install kubernetes-cli -y
    Or manually: kubectl install guide

Step 4: Start Minikube

# start minikube inside HyperV
minikube start --driver=hyperv

# or start minikube inside Virtual Box
minikube start --driver=virtualbox

Step 5: Check status
minikube status
kubectl get nodes

Step 6: Enable Addons (Optional)
minikube addons enable dashboard
minikube addons enable metrics-server

---
2. Linux (Ubuntu/Debian)
Prerequisites
    Virtualization enabled (KVM, VirtualBox, or Docker)
    curl or wget
    kubectl installed

Steps:
Step 1: Install dependencies
sudo apt update
sudo apt install -y curl wget apt-transport-https conntrack socat

Step 2: Install a hypervisor
Docker (recommended for Linux):

sudo apt install -y docker.io
sudo systemctl enable --now docker
sudo usermod -aG docker $USER

# Or VirtualBox:
sudo apt install -y virtualbox

Step 3: Install Minikube
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube

Step 4: Install kubectl
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
chmod +x kubectl
sudo mv kubectl /usr/local/bin/

Step 5: Start Minikube
minikube start --driver=docker

# Or for VirtualBox: 
minikube start --driver=virtualbox

Step 6: Verify
minikube status
kubectl get nodes

Common Tips:
# Switch Kubernetes versions
minikube start --kubernetes-version=v1.27.0

# Delete a cluster
minikube delete

# SSH into Minikube VM
minikube ssh

# Check Minikube logs
minikube logs

✅ Result: 
After these steps, you should have a fully working local Kubernetes cluster on Windows or Linux ready for development and testing.

