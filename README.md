# opensearch-k8s
OpenSearch deployment on AWS EKS (1 master, 2 data nodes)

# OpenSearch on AWS EKS (Kubernetes)

This project demonstrates deploying an **open-source search engine (OpenSearch)** on **AWS EKS** using Kubernetes.  
The setup follows a production-style architecture with **1 master node and 2 data nodes**, exposed via an AWS LoadBalancer.

---

##  Architecture

- **Kubernetes Platform:** AWS EKS
- **OpenSearch Version:** 2.11.0
- **Cluster Topology:**
  - 1 × Master node
  - 2 × Data nodes
- **Service Exposure:** Kubernetes LoadBalancer (AWS ELB)
- **Security:** Disabled (for demo/testing purposes)

---

##  Project Structure

```text
opensearch-k8s/
├── manifests/
│   ├── master.yaml      # OpenSearch master node deployment
│   ├── data.yaml        # OpenSearch data nodes (2 replicas)
│   └── service.yaml     # LoadBalancer service to expose OpenSearch
└── README.md
```

## Deployment Steps
### Prerequisites

* AWS Account

* AWS CLI configured

* EKS cluster running

* kubectl configured for EKS

* eksctl installed

## Apply Kubernetes Manifests
```bash
kubectl apply -f manifests/master.yaml
kubectl apply -f manifests/data.yaml
kubectl apply -f manifests/service.yaml
```
## Verify Pods
```
kubectl get pods
```

## Get Public Endpoint
```
kubectl get svc
```
Copy the EXTERNAL-IP / ELB DNS name.

## Test OpenSearch
```
curl http://<ELB-DNS>:9200
```

### Expected response:
```
{
  "cluster_name": "opensearch-cluster",
  "version": {
    "number": "2.11.0",
    "distribution": "opensearch"
  }
}
```

## Security Note

The OpenSearch security plugin is disabled for demonstration and learning purposes to allow public access.
In a production environment:

* TLS/HTTPS should be enabled

* Authentication & authorization must be configured

* Access should be restricted via security groups and IAM

##  Use Case

* Demonstrates Kubernetes-based deployment of an open-source search engine

* Useful for learning EKS, Kubernetes manifests, and cloud-native architecture

# Author

Suyash Srivastava
DevOps Engineer 

GitHub: https://github.com/Suyash1001

LinkedIn: www.linkedin.com/in/suyash-srivastava-9b7516229 

E-Mail: srivastavas160@gmail.com
