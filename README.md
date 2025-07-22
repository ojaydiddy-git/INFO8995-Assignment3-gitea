# INFO8995 – Assignment 3: Open Source CI/CD Pipeline with Gitea

## 📌 Objective

This project demonstrates the setup of an open-source CI/CD environment using **Gitea** deployed in Kubernetes via Helm charts. It includes transitioning from a development environment (SQLite) to a production setup backed by **MySQL** and **persistent volumes**, with public access via **ngrok**. Automation is done using **Ansible**.

---

## 🧰 Tools & Technologies

- Kubernetes
- Helm
- Gitea
- MySQL
- Ansible
- Ngrok
- GitHub Actions

---

## ✅ Key Deliverables (Marking Rubric)

| Requirement                                                | Status |
|------------------------------------------------------------|--------|
| Persistent Gitea via Helm                                  | ✅     |
| Gitea using external MySQL database                        | ✅     |
| Ngrok tunnel for public access                             | ✅     |
| Separate Ansible playbook for ngrok                        | ✅     |
| Clear, accurate README                                     | ✅     |

---

## 🚀 Setup Instructions

> Make sure you have `kubectl`, `helm`, `ansible`, and `ngrok` installed.

### 1. Clone the Repository

```bash
git clone https://github.com/ojaydiddy-git/INFO8995-Assignment3-gitea.git
cd INFO8995-Assignment3-gitea
```

### 2. Initialize Git Submodules (if any)

```bash
git submodule update --init --recursive
```

### 3. Start Kubernetes Cluster

Start your local k8s cluster (e.g., via Docker Desktop or Minikube) and verify with:

```bash
kubectl get nodes
```

### 4. Deploy Gitea in Production (MySQL) Mode

Run:

```bash
ansible-playbook prod/up.yml
```

Wait for all pods to be ready:

```bash
kubectl get pods
```

You should see:
- `gitea-*`
- `gitea-valkey-*`
- All with STATUS `Running`

### 5. Start ngrok Tunnel (Public Exposure)

Run:

```bash
ansible-playbook ngrok/up.yml
```

It will output a public link like:

```
Your Gitea instance is publicly accessible at: https://c1bfc6493b76.ngrok-free.app
```

Paste this in the submission comment.

---

## 🌍 Public Access

Your Gitea instance can be accessed at:

🔗 **https://c1bfc6493b76.ngrok-free.app**

---

## 🔄 Teardown

To remove the Gitea environment:

```bash
ansible-playbook prod/down.yml
```

And to stop ngrok:

```bash
ansible-playbook ngrok/down.yml
```

---
















