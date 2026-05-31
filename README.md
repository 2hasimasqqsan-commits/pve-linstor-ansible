# Proxmox VE LINSTOR Ansible Lab

Ansible portfolio project for building a Proxmox VE two-node lab environment with LINSTOR, DRBD-backed storage, QDevice quorum support, and HA verification.

This project is intended for infrastructure learning, storage clustering practice, and validation of Proxmox VE high availability workflows using Infrastructure as Code.

## Overview

This playbook automates the setup of a Proxmox VE lab environment using Ansible.

The lab is designed to verify a two-node Proxmox VE cluster with LINSTOR/DRBD storage and an additional QDevice node for quorum support.

The main purpose of this project is to demonstrate:

-Proxmox VE cluster automation
-LINSTOR and DRBD-backed shared storage configuration
-QDevice-based quorum support
-Proxmox VE HA resource verification
-VM disk placement on LINSTOR-backed storage
-Infrastructure automation using Ansible roles

## Architecture

```text
Ansible Control Node
        |
        | SSH
        |
        +-----------------------+
        |                       |
Proxmox VE Node 1         Proxmox VE Node 2
pve-linstor01            pve-linstor02
        |                       |
        |                       |
        +------ LINSTOR / DRBD -+
        |
        |
QDevice / QNetd Node
qnetd01
```

## Lab Nodes
| Role | Hostname  | Example IP |
|---|---|---|
| Proxmox VE node 1 | pve-linstor01 | 192.168.56.221 |
| Proxmox VE node 2 | pve-linstor02 | 192.168.56.222 |
| QDevice node | qnetd01 | 192.168.56.223 |

## Main Components
-Proxmox VE
-LINSTOR
-DRBD
-QDevice / QNetd
-Proxmox VE HA Manager
-Ansible
-LINBIT repository
-LINSTOR-backed Proxmox VE storage

## Main Features
-Proxmox VE repository configuration
-LINBIT repository configuration
-LINSTOR package installation
-LINSTOR controller / satellite setup
-DRBD-backed storage configuration
-Proxmox VE cluster setup
-QDevice quorum support
-Proxmox VE storage integration
-Basic verification tasks
-Example inventory and variable files for public use

## Directory Structure
pve-linstor-ansible/
├── ansible.cfg
├── inventory.ini.example
├── group_vars/
│   └── all.yml.example
├── roles/
│   ├── common/
│   ├── linbit_repo/
│   ├── linstor/
│   ├── linstor_cluster/
│   ├── linstor_storage/
│   ├── pve_cluster/
│   ├── pve_linstor_storage/
│   ├── pve_repo/
│   ├── qdevice/
│   └── verify/
└── site.yml

## Requirements
-Ansible control node
-Two Proxmox VE nodes
-One QDevice / QNetd node
-SSH access from the Ansible control node
-Sudo privileges for the Ansible user
-Network connectivity between all lab nodes
-Additional storage devices for DRBD/LINSTOR testing

## Usage

Copy the example inventory file:

cp inventory.ini.example inventory.ini

Copy the example variable file:

cp group_vars/all.yml.example group_vars/all.yml

Edit the files for your lab environment:

vi inventory.ini
vi group_vars/all.yml

Run syntax check:
```bash
ansible-playbook site.yml --syntax-check
```
Apply the playbook:
```bash
ansible-playbook site.yml
```
## Example Verification Commands

Check Proxmox VE cluster status:

pvecm status

Check Proxmox VE HA status:

ha-manager status

Check LINSTOR resources:

linstor resource list

Check DRBD status:

drbdadm status

Check Proxmox VE storage configuration:

pvesm status

## Screenshots / Verification

Screenshots and verification results will be added later.

Planned verification materials:

-Proxmox VE cluster GUI
-Proxmox VE HA status
-LINSTOR resource list
-DRBD Primary / Secondary status
-QDevice quorum status
-VM disk running on LINSTOR-backed storage
-Auto failover test screenshots
-Auto failover demo video

## Security Notes

Do not publish real environment values.

Before publishing this repository, make sure the following information is not included:

-Real IP addresses
-Real hostnames
-Passwords
-API tokens
-SSH private keys
-Vault password files
-Internal domain names
-Customer or company confidential information

Use example values such as:

192.168.56.0/24
example.local
CHANGE_ME

## Notes

This project is for lab and validation use.

Additional design, hardening, fencing, quorum, storage redundancy, and operational review are required for production use.
