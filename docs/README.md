# KubeRise OpsLab

A hands-on Kubernetes lab project built using Rocky Linux VMs and kubeadm to understand Kubernetes internals, networking, container runtime configuration, Ansible automation, and cluster administration.

## Phases

  * Phase 1 — Infrastructure & Base System Setup
  * Phase 2 — Kubernetes Cluster Initialization
  * Phase 3 — Workload Deployment & Ansible Automation
  * Phase 4 — Recovery & Automation Node Setup
  * Phase 5 — VXLAN & Firewalld Troubleshooting

## Environment

  * VMware Workstation Pro
  * Rocky Linux 9
  * containerd
  * Kubernetes v1.36.0
  * Flannel CNI
  * Ansible

## Current Automation Status

  * Automated: OS prerequisites (kernel modules, sysctl settings) and service states via Ansible.
  * Manual: Cluster bootstrapping (`kubeadm init`), CNI installation, and worker node joining.

## Documentation

  * [Node Provisioning & Runtime Setup](01-node-provisioning-and-runtime.md)
  * [Cluster Bootstrap & Networking](02-cluster-bootstrap-and-networking.md)
  * [Workload Deployment & Automation](03-workload-deployment-and-automation.md)
  * [Recovery & Automation Node](04-recovery-and-automation-node.md)
  * [VXLAN & Firewalld Troubleshooting](05-vxlan-and-firewalld-troubleshooting.md)

## Next Steps

  * End-to-End Automation: Automate `kubeadm init`, CNI deployment, and `kubeadm join` using Ansible playbooks.
  * Persistent Storage: Implement Longhorn or NFS provisioner for dynamic PVCs.
  * Observability: Deploy Prometheus and Grafana for cluster monitoring.
  * Ingress: Install an NGINX Ingress Controller for external routing.
