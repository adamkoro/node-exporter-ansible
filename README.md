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

Copy `inventory/hosts.ini.example` to `inventory/hosts.ini` and edit it.

```bash
cp inventory/hosts.ini.example inventory/hosts.ini
```

Copy `inventory/group_vars/all.yml.example` to `inventory/group_vars/all.yml` and edit it.

```bash
cp inventory/group_vars/all.yml.example inventory/group_vars/all.yml
```

#### all.yml variables

| Variable | Default | Description |
|----------|---------|-------------|
| `ansible_user` | `root` | Username which Ansible will use to connect via SSH |
| `node_exporter_version` | `1.5.0` | Version of the Node Exporter |
| `download_url` | `https://github.com/prometheus/node_exporter/releases/download/v{{ node_exporter_version }}` | URL to download Node Exporter |

#### hosts.ini variables

| Variable | Default | Description |
|----------|---------|-------------|
| `ansible_ssh_private_key_file` | `~/.ssh/id_rsa` | Path to SSH private key |
| `ansible_port` | `22` | SSH port |
| `ansible_ssh_extra_args` | `-o StrictHostKeyChecking=no` | SSH extra args |

### Install

```bash
ansible-playbook -i inventory/hosts.ini deploy.yml
```

### Uninstall

```bash
ansible-playbook -i inventory/hosts.ini reset.yml
```

