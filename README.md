# Multi-Environment Web Application with Docker & Helm

This project demonstrates how to deploy a simple web application to Kubernetes using **Docker** and **Helm**, with separate configurations for **development** and **production** environments.

## Project Structure

```text
multi-env-webapp/
│
├── app/
│   ├── index.html
│   └── Dockerfile
│
├── helm/
│   └── webapp/
│       ├── Chart.yaml
│       ├── values.yaml
│       ├── values-dev.yaml
│       ├── values-prod.yaml
│       └── templates/
│            ├── deployment.yaml
│            ├── service.yaml
│            ├── ingress.yaml
│            ├── configmap.yaml
│            └── _helpers.tpl
│
└── README.md
```

## Features

* Simple static web application
* Dockerized application
* Kubernetes deployment using Helm
* Separate configuration files for development and production
* ConfigMap support for environment-specific settings
* Ingress configuration for external access

## Prerequisites

Before getting started, ensure you have the following installed:

* Docker
* Kubernetes cluster (Minikube, Kind, or a cloud provider)
* kubectl
* Helm 3+

## Build the Docker Image

Navigate to the application directory:

```bash
cd app
```

Build the Docker image:

```bash
docker build -t webapp:latest .
```

If using a local Kubernetes cluster like Minikube, load the image:

```bash
minikube image load webapp:latest
```

## Deploy with Helm

Navigate to the Helm chart directory:

```bash
cd helm/webapp
```

### Development Environment

```bash
helm install webapp-dev . -f values-dev.yaml
```

### Production Environment

```bash
helm install webapp-prod . -f values-prod.yaml
```

## Upgrade an Existing Release

Development:

```bash
helm upgrade webapp-dev . -f values-dev.yaml
```

Production:

```bash
helm upgrade webapp-prod . -f values-prod.yaml
```

## Uninstall

Development:

```bash
helm uninstall webapp-dev
```

Production:

```bash
helm uninstall webapp-prod
```

## Verify Deployment

Check Pods:

```bash
kubectl get pods
```

Check Services:

```bash
kubectl get services
```

Check Deployments:

```bash
kubectl get deployments
```

## Configuration Files

| File               | Purpose                        |
| ------------------ | ------------------------------ |
| `values.yaml`      | Default Helm configuration     |
| `values-dev.yaml`  | Development-specific values    |
| `values-prod.yaml` | Production-specific values     |
| `deployment.yaml`  | Kubernetes Deployment resource |
| `service.yaml`     | Kubernetes Service resource    |
| `ingress.yaml`     | Ingress configuration          |
| `configmap.yaml`   | Application configuration      |
| `_helpers.tpl`     | Helm helper templates          |

## Example Commands

Render Kubernetes manifests:

```bash
helm template webapp .
```

Validate the Helm chart:

```bash
helm lint .
```

## Future Improvements

* HTTPS with TLS
* Horizontal Pod Autoscaler (HPA)
* CI/CD pipeline
* Monitoring with Prometheus and Grafana
* Persistent storage support
* Secrets management

## License

This project is licensed under the MIT License.
