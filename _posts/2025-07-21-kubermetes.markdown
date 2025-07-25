---
layout: post
title:  "Kubermetes"
date:   2025-07-21 02:22:30 +0530
categories: k8s
---
Great! You mentioned **Kubernetes** — let’s break it down in a **simple and complete way**, even if you're new to cloud or DevOps.

---

## 🚀 What is Kubernetes?

**Kubernetes** (often abbreviated as **K8s**) is an **open-source system** for **automating deployment, scaling, and management of containerized applications**.

> Think of Kubernetes as a **manager** that tells your applications where to run, when to run, and how many copies to run — all inside containers (like Docker).

---

## 🧱 Core Concepts (Simplified)

### 1. **Container**

A lightweight unit that packages your app and its dependencies. Usually created using **Docker**.

---

### 2. **Pod**

* Smallest unit in Kubernetes.
* Wraps **one or more containers**.
* Example: If your app + sidecar (e.g., for logging) need to run together, they go in a **pod**.

---

### 3. **Node**

* A **physical or virtual machine** where pods run.
* Kubernetes uses multiple nodes.

---

### 4. **Cluster**

* A **group of nodes** managed by Kubernetes.
* You interact with the cluster using `kubectl`.

---

### 5. **Deployment**

* A blueprint to tell Kubernetes **how to run pods**.
* You define how many copies, the image to use, and update strategies.

---

### 6. **Service**

* Makes your pods **accessible** to other pods or the internet.
* Types:

  * **ClusterIP** – Internal communication
  * **NodePort** – External access via node IP
  * **LoadBalancer** – External access with load balancing

---

## 🛠️ What You Can Do With Kubernetes

| Task                    | Kubernetes Feature             |
| ----------------------- | ------------------------------ |
| Run containers          | Pods                           |
| Scale apps up/down      | Deployments, Autoscaling       |
| Manage traffic          | Services, Ingress              |
| Roll out updates safely | Rolling updates in deployments |
| Handle failed apps      | Self-healing (restart pods)    |

---

## 📦 A Sample Kubernetes YAML (Deployment + Service)

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-app
spec:
  replicas: 3
  selector:
    matchLabels:
      app: my-app
  template:
    metadata:
      labels:
        app: my-app
    spec:
      containers:
        - name: my-container
          image: nginx
---
apiVersion: v1
kind: Service
metadata:
  name: my-service
spec:
  type: NodePort
  selector:
    app: my-app
  ports:
    - port: 80
      targetPort: 80
      nodePort: 30000
```

This will:

* Deploy 3 pods of an `nginx` container.
* Expose it at port `30000` on the host machine.

---

## 📚 Basic Kubernetes Commands

```bash
kubectl apply -f app.yaml     # Deploy resources
kubectl get pods              # List running pods
kubectl get services          # List services
kubectl describe pod PODNAME  # Detailed pod info
kubectl logs PODNAME          # See logs of a pod
kubectl delete -f app.yaml    # Delete resources
```

---

## 💡 Real-World Uses

* Deploy microservices in production
* Handle huge traffic spikes with autoscaling
* Blue/green deployments and A/B testing
* Easily run CI/CD pipelines in clusters (e.g., with ArgoCD, Jenkins)

---

## 🛑 Kubernetes Isn’t For:

* Tiny personal projects (too complex)
* Apps that don’t need high availability or scaling

---
