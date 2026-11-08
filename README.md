# KubeRise OpsLab

A production-simulated, multi-node Kubernetes homelab built on Rocky Linux VMs. This project demonstrates manual cluster bootstrapping, partial Infrastructure as Code (IaC) automation for node prerequisites, and advanced container networking troubleshooting.

## Current Automation Status

  * Automated: OS prerequisites (kernel modules, sysctl networking parameters, and service states) via Ansible.
  * Manual: Cluster bootstrapping (`kubeadm init`), CNI installation, and worker node joining.

## Architecture & Tech Stack

  * Hypervisor: VMware Workstation Pro
  * Operating System: Rocky Linux 9
  * Container Runtime: containerd (with systemd cgroup alignment)
  * Orchestration: Kubernetes (kubeadm)
  * CNI: Flannel (VXLAN)
  * Configuration Management: Ansible (native modules, Vault)
  * Networking: firewalld (hardened bridge/VXLAN routing)

## Key Highlights

  * Cluster Bootstrap: Architected a 3-node cluster (1 control plane, 2 workers) with a dedicated 10.244.0.0/16 Pod CIDR to avoid VM network overlap.
  * Node Automation: Refactored raw Linux commands into idempotent Ansible roles to automate kernel module loading (overlay, br_netfilter) and sysctl networking parameters.
  * Workload Deployment: Deployed a 2-replica Nginx application in a dedicated namespace and exposed it internally via a ClusterIP Service.
  * Advanced Troubleshooting: Diagnosed and resolved a cross-node No route to host error by configuring firewalld trusted zones for cni0 and flannel.1 interfaces, restoring VXLAN packet flow.
  * Recovery Control Node: Built a dedicated out-of-band recovery node (kr-self-heal) with passwordless SSH to serve as the Ansible control plane.

## Repository Structure

  * [`ansible/`](ansible/) - Playbooks, roles, and inventories for node automation.
  * [`docs/`](docs/) - Comprehensive setup, architecture, and troubleshooting documentation.
  * [`manifests/`](manifests/) - Declarative Kubernetes YAML (Deployments, Services, Namespaces).
  * [`screenshots/`](screenshots/) - Visual proof of cluster health, Ansible runs, and successful connectivity tests.

## Documentation

Explore the detailed engineering logs, setup guides, and runbooks below:

  * [01 - Node Provisioning & Runtime Setup](docs/01-node-provisioning-and-runtime.md)
  * [02 - Cluster Bootstrap & Networking](docs/02-cluster-bootstrap-and-networking.md)
  * [03 - Workload Deployment & Automation](docs/03-workload-deployment-and-automation.md)
  * [04 - Recovery & Automation Node](docs/04-recovery-and-automation-node.md)
  * [05 - VXLAN & Firewalld Troubleshooting](docs/05-vxlan-and-firewalld-troubleshooting.md)

## Next Steps

  * End-to-End Automation: Extend Ansible playbooks to automate `kubeadm init`, CNI deployment, and `kubeadm join`.
  * Persistent Storage: Implement Longhorn or NFS provisioner for dynamic PVCs.
  * Observability: Deploy Prometheus and Grafana for cluster monitoring.
  * Ingress: Install an NGINX Ingress Controller for external routing.
