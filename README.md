# 🛡️ Kubernetes Security Policies Starter Pack

This project is a **secure Kubernetes environment** that applies multiple security policies at the Pod, Network, and RBAC levels, along with a sample application to demonstrate how these policies work in practice.

---

## 📦 Project Components

- **Namespaces**
  - `secure-app`: Contains all secure application resources.

- **Pod Security Standards (Restricted)**
  - Ensures containers do **not run as root**.
  - Limits granted capabilities to pods.
  - Applied to all pods in `secure-app`.

- **Network Policies**
  - `allow-app-to-db`: Allows traffic from `myapp` to `postgres` only on TCP port 5432.
  - `deny-other-traffic`: Denies all other traffic to/from pods in `secure-app`.

- **RBAC Roles**
  - Roles grant access only to necessary resources.
  - RoleBinding connects the role to `dev-user`.

- **Application Deployment**
  - Nginx (2 Pods) demonstrates the security policies.
  - Communicates with `postgres` only through the allowed NetworkPolicy.

- **Postgres Pod**
  - Lightweight database for demonstration.
  - Accessible only from `myapp` pods.

- **Service**
  - ClusterIP exposes `myapp` pods internally within the namespace.

## 🔗 Component Interactions

- `myapp` → connects to `postgres` only via the specific NetworkPolicy.
- `myapp Service` → provides internal access to the `myapp` pods.
- PodSecurity (restricted) → enforces strict security rules on all pods.
- RBAC → prevents unauthorized access to resources.
- NetworkPolicy → blocks any unspecified traffic between pods or namespaces.

## ⚡ How to Apply

1. Create namespaces:
```bash
kubectl apply -f namespaces.yaml
kubectl apply -f pod-security.yaml
kubectl apply -f network-policies.yaml
kubectl apply -f rbac.yaml
kubectl apply -f postgres.yaml
kubectl apply -f app-deployment.yaml
kubectl apply -f app-service.yaml
```

## ✅ Key Benefits

- Strict **Pod security** prevents root containers and limits capabilities.
- **Network segmentation** reduces lateral movement risk.
- **RBAC roles** enforce least privilege access.
- Sample app demonstrates **policy enforcement in practice**.
- **Environment isolation** with namespaces reduces cross-application risks.
- **Simplified onboarding** for DevSecOps teams to quickly apply security best practices.
- **Compliance readiness** for standard Kubernetes security benchmarks.
- Lightweight design allows **easy testing and demonstration** without complex infrastructure.

## 🌟 Star this repo if you find it useful!

Made with 💻 by a Cloud Security Engineer, for DevOps, DevSecOps and Cloud Security Engineers.

## 👨‍💻 Author

[Abdullrahman Wasfi](https://www.linkedin.com/in/abdullrahmanwasfi)

Made with ❤️ using Kubernetes