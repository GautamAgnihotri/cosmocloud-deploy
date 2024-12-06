# cosmocloud-deploy Helm Chart

This Helm chart deploys a simple application with a backend, frontend, and Redis database using Kubernetes. The services are configured with appropriate environment variables, and they are exposed through Kubernetes services with specific configurations.

## Overview

The chart deploys the following services:
- **Backend**: Deployed using the `shreybatra/sample-backend` image, with Redis URI set to `redis://redis-svc:6379`.

- **Frontend**: Deployed using the `shreybatra/sample-frontend` image, with the Backend URL set to `http://backend-svc:8000`.

- **Redis**: Deployed using the `redis` image.

The services are exposed using the following configurations:
- **Backend**: ClusterIP, port `8000`
- **Frontend**: NodePort, port `5173`, NodePort `31000`
- **Redis**: ClusterIP, port `6379`


## Prerequisites

- Kubernetes cluster (version 1.30 or later)
- Helm 3.x
- kubectl configured to access the cluster
- **Docker** or **CRI-O**: Make sure Docker or CRI-O is installed for container management.


## Installation

1. To get started, clone the repository:
    ```bash
        git clone https://github.com/GautamAgnihotri/cosmocloud-deploy
        cd cosmocloud-deploy
    ```


2. Install the chart:

    ```bash
    helm install testapp ./cosmocloud-deploy --atomic --timeout 30s
    ```

3. Wait for the services to be deployed.
4. Check the status of the deployed pods by running:
     ```bash
    kubectl get pods
    ```
    Wait until all pods are in the Running or Ready state.


## Accessing Services

- **Frontend**: Access the frontend at `http://<NODE_IP>:31000` (replace `<NODE_IP>` with the worker node's IP).

## Uninstallation

To uninstall the chart:

```bash
helm uninstall testapp
