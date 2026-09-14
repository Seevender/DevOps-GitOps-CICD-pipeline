# DevOps GitOps CI/CD Pipeline

End-to-end CI/CD and GitOps pipeline for deploying a Java Spring Boot application to Kubernetes.

## Architecture

GitHub → Jenkins → Maven → SonarQube → Docker → Docker Hub → Git Manifest Update → Argo CD → Kubernetes

## Tech Stack

- Jenkins
- Maven
- SonarQube
- Docker
- Docker Hub
- Kubernetes
- Argo CD
- AWS
- Java Spring Boot
- Git & GitHub

## Pipeline Workflow

1. Jenkins checks out the source code.
2. Maven builds and tests the Spring Boot application.
3. SonarQube performs static code analysis.
4. Jenkins builds a Docker image.
5. The image is pushed to Docker Hub using the Jenkins build number as the tag.
6. Jenkins updates the Kubernetes deployment manifest with the new image tag.
7. The updated manifest is committed to GitHub.
8. Argo CD detects the Git change and synchronizes the application with Kubernetes.

## Kubernetes

The application runs with **2 replicas** using a Kubernetes Deployment.

A Kubernetes Service exposes the application on port `80` and forwards traffic to the container on port `8080`.

## Key DevOps Concepts

- CI/CD automation
- Infrastructure automation
- Docker containerization
- Kubernetes deployments
- GitOps
- Automated image versioning
- Argo CD synchronization
- Static code analysis
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