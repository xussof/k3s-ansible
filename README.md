# Build a Kubernetes cluster using k3s via Ansible

Author: <https://github.com/itwars>

## K3s Ansible Playbook

Build a Kubernetes cluster using Ansible with k3s. The goal is easily install a Kubernetes cluster on machines running:

- [X] Debian
- [X] Ubuntu
- [X] CentOS

on processor architecture:

- [X] x64
- [X] arm64
- [X] armhf

## System requirements

Deployment environment must have Ansible 2.4.0+
Master and nodes must have passwordless SSH access

## Usage

First create a new directory based on the `sample` directory within the `inventory` directory:

```bash
cp -R inventory/sample inventory/my-cluster
```

Second, edit `inventory/my-cluster/hosts.ini` to match the system information gathered above. For example:

```bash
[master]
192.16.35.12

[node]
192.16.35.[10:11]

[k3s_cluster:children]
master
node
```

If needed, you can also edit `inventory/my-cluster/group_vars/all.yml` to match your environment.

Start provisioning of the cluster using the following command:

```bash
ansible-playbook site.yml -i inventory/my-cluster/somehost.ini
```

To reset:
ansible-playbook reset.yml -i inventory/my-cluster/somehost.ini

To install hd:
ansible-playbook external-hdd.yml -i inventory/my-cluster/somehost.ini

## Kubeconfig

To get access to your **Kubernetes** cluster just

```bash
scp pi@192.168.0.180:~/.kube/config ~/.kube/config
```

To set up garbage collection for k3s:
https://www.cloudsavvyit.com/11041/how-to-clean-up-old-containers-and-images-in-your-kubernetes-cluster/
