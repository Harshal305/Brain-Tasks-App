# Brain Tasks App – End-to-End AWS DevOps CI/CD Project

An end-to-end DevOps project demonstrating automated application deployment using GitHub, AWS CodePipeline, CodeBuild, Docker, Amazon ECR, Amazon EKS and Kubernetes.

## Project Architecture

GitHub → AWS CodePipeline → AWS CodeBuild → Docker → Amazon ECR → Amazon EKS → Kubernetes Service → AWS LoadBalancer

## Technologies Used

- Git and GitHub
- Docker
- Nginx (Alpine)
- AWS CodePipeline
- AWS CodeBuild
- Amazon ECR
- Amazon EKS
- Kubernetes
- AWS IAM
- AWS EC2
- AWS Elastic Load Balancing

## Project Workflow

1. Developer pushes code to GitHub.
2. AWS CodePipeline automatically detects the change.
3. CodeBuild builds the Docker image.
4. Docker image is pushed to Amazon ECR.
5. CodeBuild connects to Amazon EKS.
6. Kubernetes Deployment updates the application image.
7. Kubernetes performs a rolling update.
8. AWS LoadBalancer exposes the application publicly.

## Infrastructure Details

| Resource | Configuration |
|---|---|
| AWS Region | us-east-1 |
| EKS Cluster | brain-tasks-cluster |
| Node Group | brain-tasks-nodes |
| EC2 Instance | t3.small |
| Kubernetes Version | 1.37 |
| Deployment | brain-tasks-app |
| Replicas | 2 |
| Container Port | 3000 |
| ECR Repository | brain-tasks-app |
| Pipeline | Brain-test-12 |

## Docker Configuration

The application uses Nginx Alpine to serve the production-ready static files from the `dist/` directory on port 3000.

## Kubernetes Resources

- `deployment.yaml` – Application deployment with two replicas.
- `service.yaml` – LoadBalancer service exposing the application on port 3000.

## CI/CD Pipeline

The pipeline is configured to:

- Detect GitHub source changes.
- Build a Docker image.
- Push the image to Amazon ECR.
- Update the Kubernetes Deployment in EKS.
- Verify the rollout status.

## Verification Commands

Check Kubernetes nodes:

```bash
kubectl get nodes
```

Check application pods:

```bash
kubectl get pods
```

Check deployment:

```bash
kubectl get deployment brain-tasks-app
```

Check service:

```bash
kubectl get svc brain-tasks-service
```

Check rollout:

```bash
kubectl rollout status deployment/brain-tasks-app
```

## Project Outcome

- Successfully deployed the Brain Tasks application on Amazon EKS.
- Configured two running Kubernetes replicas.
- Exposed the application using an AWS LoadBalancer.
- Implemented automated CI/CD deployment from GitHub to EKS.
- Verified successful pipeline execution and Kubernetes rollout.

## Author

Harshal Patil

Cloud & DevOps Engineering Practice Project
