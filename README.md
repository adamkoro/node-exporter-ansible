# node-exporter-ansible

Deploy Prometheus node exporter with Ansible

**Only works on arm64 and amd64 architecture.**

## Requirements

- Ansible

## Usage

Clone repository

```bash
git clone https://github.com/adamkoro/node-exporter-ansible.git
cd node-exporter-ansible
```

### Configuration

Copy `inventory-example.yaml` to `inventory.yaml` and edit it.

```bash
cp inventory-example.yaml inventory.yaml
```

#### inventory.yaml variables
`TODO` update
| Variable | Default | Description |
|----------|---------|-------------|
| `ansible_user` | `root` | Username which Ansible will use to connect via SSH |
| `ansible_ssh_private_key_file` | `~/.ssh/id_rsa` | Path to SSH private key |
| `ansible_port` | `22` | SSH port |
| `ansible_ssh_extra_args` | `-o StrictHostKeyChecking=no` | SSH extra args |
| `node_exporter_version` | `1.7.0` | Version of the Node Exporter |
| `node_exporter_download_url` | `https://github.com/prometheus/node_exporter/releases/download/v{{ node_exporter_version }}` | URL to download Node Exporter |
| `smart_metrics_enabled` | `true` | Disk S.M.A.R.T metrics collector enable |
| `smart_metrics_download_url` | `https://github.com/prometheus-community/node-exporter-textfile-collector-scripts/blob/master/smartmon.sh` | Disk S.M.A.R.T metrics collector script url |
| `nvme_metrics_enabled` | `true` | NVME SSD metrics collector enable |
| `nvme_metrics_download_url` | `https://github.com/prometheus-community/node-exporter-textfile-collector-scripts/blob/master/nvme_metrics.sh` | NVME SSD metrics collector script url |
| `lvm_metrics_enabled` | `true` | LVM metrics collector enable |
| `lvm_metrics_download_urls` | `https://github.com/prometheus-community/node-exporter-textfile-collector-scripts/blob/master/lvm-prom-collector` | LVM metrics collector script url |
| `zfs_metrics_enabled` | `true` | ZFS metrics collector enable |
| `zfs_metrics_download_url` | `https://github.com/prometheus-community/node-exporter-textfile-collector-scripts/blob/master/zfs_zpool.sh` | ZFS metrics collector script url |

### Install

```bash
ansible-playbook -i inventory.yaml playbooks/install.yaml
```

### Uninstall

```bash
ansible-playbook -i inventory.yaml playbooks/reset.yaml
```
