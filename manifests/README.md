# Kubernetes Manifests

Declarative YAML resources used to deploy and expose workloads within the KubeRise cluster.

## Workloads

  * `namespace.yml` - Creates a dedicated `kuberise` namespace to isolate the application from system components.
  * `nginx-deploy.yml` - Deploys a 2-replica Nginx application across the worker nodes.
  * `nginx-service.yml` - Exposes the Nginx deployment internally using a ClusterIP Service.

## Key Features

  * Declarative Configuration: Infrastructure state is defined in code, allowing for repeatable and version-controlled deployments.
  * Resource Isolation: Utilizes namespaces to keep workloads logically separated.
  * Service Discovery: Internal cluster routing is configured via Kubernetes Services.

## Usage

Apply the manifests to the cluster:

```bash
kubectl apply -f manifests/nginx/
