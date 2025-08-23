# Helm Charts for User Interaction API

This repository contains Helm charts for deploying the User Interaction API microservice and its dependencies.

## Chart Structure

The Helm chart consists of three subcharts:

1. **webapp** - The main Go-based User Interaction API application
2. **external-secrets** - Integration with External Secrets Operator for secure credentials management
3. **cert-manager** - Certificate management for HTTPS/TLS

## Prerequisites

- GKE (Google Kubernetes Engine) cluster
- Workload Identity enabled for GCS (Google Cloud Storage) and Secret Manager
- kubectl installed and configured
- Helm 3 installed

## Setup

### Install cert-manager

cert-manager needs to be installed on your cluster:

```bash
kubectl apply -f https://github.com/cert-manager/cert-manager/releases/download/v1.17.0/cert-manager.yaml

helm repo add external-secrets https://charts.external-secrets.io
helm install external-secrets external-secrets/external-secrets
```

## Installation

### Clone the Repository

```bash
git clone https://github.com/cyse7125-sp25-team01/helm-charts
cd helm-charts

helm dependency update .
helm dependency build .

helm install myapp .

```