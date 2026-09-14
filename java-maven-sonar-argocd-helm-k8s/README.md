# Java CI/CD Pipeline with Jenkins, Docker, Kubernetes & Argo CD

An end-to-end CI/CD and GitOps project for deploying a Java Spring Boot application to Kubernetes.

## Architecture

Developer → GitHub → Jenkins → Maven Build & Test → SonarQube → Docker → Docker Hub → Git Manifest Update → Argo CD → Kubernetes

## Tech Stack

- **CI/CD:** Jenkins
- **Code Quality:** SonarQube
- **Build:** Maven
- **Containerization:** Docker
- **Container Registry:** Docker Hub
- **Orchestration:** Kubernetes
- **Configuration:** Kubernetes YAML manifests
- **GitOps:** Argo CD
- **Application:** Java Spring Boot
- **Version Control:** Git & GitHub

## Pipeline Workflow

1. Jenkins checks out the source code.
2. Maven builds and tests the Spring Boot application.
3. SonarQube performs static code analysis.
4. Jenkins builds a Docker image.
5. The image is pushed to Docker Hub with the Jenkins build number as the tag.
6. Jenkins updates the Kubernetes deployment manifest with the new image tag.
7. The updated manifest is committed to GitHub.
8. Argo CD detects the Git change and synchronizes the desired state with Kubernetes.

## Kubernetes Deployment

The application runs as a Kubernetes Deployment with **2 replicas**.

A Kubernetes Service exposes the application and forwards traffic from port `80` to the application's container port `8080`.

## Key DevOps Concepts Demonstrated

- CI/CD automation
- Kubernetes deployment
- Docker image versioning
- Git-based deployment configuration
- GitOps with Argo CD
- Automated deployment updates
- Static code analysis with SonarQube
- Jenkins credentials management

## Project Structure

```text
java-maven-sonar-argocd-helm-k8s/
├── Argo CD/
├── spring-boot-app/
│   ├── Dockerfile
│   ├── JenkinsFile
│   ├── pom.xml
│   └── src/
└── spring-boot-app-manifests/
    ├── deployment.yml
    └── service.yml