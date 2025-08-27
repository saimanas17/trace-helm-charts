# Helm Charts for Trace Survey Application

This repository contains Helm charts for deploying the Trace survey application and its comprehensive infrastructure dependencies.

## Chart Structure

The Helm chart consists of seven subcharts:

1. **webapp** - The main Go-based User Interaction API application
2. **external-secrets** - Integration with External Secrets Operator for secure credentials management
3. **cert-manager** - Certificate management for HTTPS/TLS
4. **otel** - OpenTelemetry setup for distributed tracing and observability
5. **kafka** - Apache Kafka message broker setup with topic creation for event-driven messaging
6. **external-dns** - Automatic DNS record management for Istio Ingress Gateway with GCP Cloud DNS integration
7. **trace** - RAG (Retrieval-Augmented Generation) model deployment

## Prerequisites

- GKE (Google Kubernetes Engine) cluster
- Workload Identity enabled for GCS (Google Cloud Storage) and Secret Manager
- kubectl installed and configured
- Helm 3 installed
- Istio service mesh installed (for external-dns integration)
- GCP Cloud DNS zone configured

## Setup

### Install Core Dependencies

cert-manager and external-secrets need to be installed on your cluster:

```bash
# Install cert-manager
kubectl apply -f https://github.com/cert-manager/cert-manager/releases/download/v1.17.0/cert-manager.yaml

# Add external-secrets repository and install
helm repo add external-secrets https://charts.external-secrets.io
helm install external-secrets external-secrets/external-secrets
```

## Installation

### Clone the Repository

```bash
git clone https://github.com/saimanas17/helm-charts
cd helm-charts

# Update and build dependencies
helm dependency update .
helm dependency build .

# Install the complete application stack
helm install myapp .
```
