# Ansible Automation

Infrastructure as Code (IaC) playbooks used to automate the provisioning, configuration, and maintenance of the Kubernetes cluster nodes.

## Repository Structure

  * `inventory/` - Host definitions (`hosts.ini`), group variables, and Ansible Vault secrets.
  * `playbooks/` - Main execution entry points for specific operational tasks.
  * `roles/` - Reusable, modular automation tasks (e.g., `kubernetes_prerequisites`).

## Key Features

  * Native Modules: Utilizes idempotent native Ansible modules (`ansible.posix.sysctl`, `community.general.modprobe`, `ansible.builtin.copy`).
  * Security: Secured sudo credentials using Ansible Vault, with automated password retrieval via a local config file.
  * Idempotency: Safely re-runs without making unnecessary changes, automatically detecting and correcting kernel-level state drift.

## Prerequisites

  * Ansible installed on the control node (`kr-self-heal`).
  * Passwordless SSH access to all cluster nodes.
  * Ansible Vault password file securely stored at `~/.config/ansible/kuberise-vault-pass`.

## Usage

The project root contains an `ansible.cfg` file that automatically defines the inventory path (`./ansible/inventory/hosts.ini`) and the Vault password file path. Because of this, neither the `-i` flag nor the `--ask-vault-pass` flag are required.

Run the prerequisite playbook across all nodes:

```bash
ansible-playbook playbooks/configure-kubernetes-prerequisites.yml
