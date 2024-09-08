# ISEC6000-SecureDevOps-21322895-A1

## Overview

This repository contains the configuration and deployment scripts for the Secure DevOps assignment using the Saleor platform. Saleor is a high-performance e-commerce solution built with Python and Django. The project involves deploying Saleor using Docker and Kubernetes, and integrating additional services for a complete e-commerce setup.In this assignment, the Saleor platform is utilized as a submodule.

## Repository Structure

### Root Directory

- **`kubernetes/`**: Contains Kubernetes deployment and service configuration files.
- **`saleor-platform/`**: Contains Saleor-related deployment files and Docker Compose configurations.
- **`service-account-key.json`**: Service account key for Google Cloud -GKE .
- **`README.md`**: This file.

### `saleor-platform/` Directory

- **Deployment Files**:
  - `api-deployment.yaml`: Kubernetes deployment for the Saleor API.
  - `db-deployment.yaml`: Kubernetes deployment for the database.
  - `redis-deployment.yaml`: Kubernetes deployment for Redis.
  - `dashboard-deployment.yaml`: Kubernetes deployment for the Saleor dashboard.
  - `mailpit-deployment.yaml`: Kubernetes deployment for the Mailpit service.
  - `worker-deployment.yaml`: Kubernetes deployment for the Saleor worker service.

- **Service Files**:
  - `api-service.yaml`: Kubernetes service for the Saleor API.
  - `db-service.yaml`: Kubernetes service for the database.
  - `redis-service.yaml`: Kubernetes service for Redis.
  - `dashboard-service.yaml`: Kubernetes service for the Saleor dashboard.
  - `mailpit-service.yaml`: Kubernetes service for the Mailpit service.

- **Persistent Volume Claims**:
  - `jaeger-claim0-persistentvolumeclaim.yaml`: Persistent Volume Claim for Jaeger.
  - `saleor-db-persistentvolumeclaim.yaml`: Persistent Volume Claim for Saleor database.
  - `saleor-media-persistentvolumeclaim.yaml`: Persistent Volume Claim for Saleor media.
  - `saleor-redis-persistentvolumeclaim.yaml`: Persistent Volume Claim for Redis.

- **ConfigMaps and Environment Variables**:
  - `backend-env-configmap.yaml`: ConfigMap for backend environment variables.
  - `common-env-configmap.yaml`: ConfigMap for common environment variables.
  - `db-cm1-configmap.yaml`: ConfigMap for database configurations.
  - `backend.env`: Environment variables for the Saleor backend.
  - `common.env`: Common environment variables.

- **Docker and Database Files**:
  - `docker-compose.yml`: Docker Compose file for local development.
  - `replica_user.sql`: SQL script for setting up replica users.

- **Additional Files**:
  - `LICENSE`: License information.
  - `README.md`: This README file.

## Prerequisites

1. **Docker**: Ensure Docker is installed on Ubuntu.
2. **Kubernetes**: Ensure Kubernetes is set up and configured.
3. **Kubectl**: Ensure `kubectl` is installed and configured to interact with your Kubernetes cluster.
4. **GKE**: Goole cloud account is configured and enable container registry.

## Setup and Deployment

### Local Development

1. **Navigate to the `saleor-platform` Directory**:
   ```bash
   cd saleor-platform
   ```

2. **Start Services with Docker Compose**:
   ```bash
   docker-compose up
   ```

3. **Tagged Docker Images to GCR path**:
   ```bash
   docker tag SOURCE_IMAGE[:TAG] TARGET_IMAGE[:TAG]
   ```
4. **Push Docker Images**:
   ```bash
   docker push TARGET_IMAGE[:TAG]
   ```

### Kubernetes Deployment

1. **Apply Kubernetes Configurations**:
   ```bash
   kubectl apply -f kubernetes/
   ```

2. **Verify Deployments**:
   ```bash
   kubectl get deployments
   kubectl get services
   kubectl get pods
   ```

3. **Check Logs**:
   ```bash
   kubectl logs -f <pod-name>
   ```

## Configuration

Update environment variables and configuration files as needed for your deployment. Refer to `backend.env`, `common.env`, and ConfigMap files for specific configuration settings.

## Convert a Docker Compose file to Kubernetes manifests and output to the current directory
kompose convert -f docker-compose.yml


