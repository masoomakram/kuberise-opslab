# Project Screenshots

Visual documentation of the KubeRise OpsLab cluster lifecycle, from initial bootstrap to automated workloads and network troubleshooting.

## Cluster Initialization & Bootstrap

  * `control-plane-init.jpg` - Successful `kubeadm init` output on the control plane.
  * `worker-01-joined.jpg` - Worker node 1 successfully joining the cluster.
  * `worker-02-joined.jpg` - Worker node 2 successfully joining the cluster.
  * `cluster-ready.jpg` - `kubectl get nodes` showing all 3 nodes in a Ready state.
  * `cluster-pods-running.jpg` - Core cluster components (Flannel, CoreDNS, etc.) running successfully.

## Ansible Automation

  * `ansible-inventory.png` - The grouped inventory structure for control plane and worker nodes.
  * `ansible-ping-test.png` - Passwordless SSH validation using the Ansible ping module.
  * `ansible-prerequisites-playbook-success.png` - Successful execution of kernel module and sysctl tasks.
  * `ansible-kubernetes-services-success.png` - Verification of containerd and kubelet service states.

## Workloads & Networking

  * `nginx-workload.png` - Nginx pods successfully deployed across multiple worker nodes.
  * `pod-to-pod-connectivity-success.png` - Nginx HTML output proving internal Service discovery and cross-node VXLAN routing.
