# Ansible Server

![GitHub issues](https://img.shields.io/github/issues/Freaky2112/Scripts?style=flat-square&color=red) ![GitHub Pull Requests](https://img.shields.io/github/issues-pr/Freaky2112/ansible_server)

![GitHub license](https://img.shields.io/github/license/Freaky2112/ansible_server?style=flat-square&color=blue) ![Contributions Welcome](https://img.shields.io/badge/contributions-welcome-orange.svg) ![Stars](https://img.shields.io/github/stars/Freaky2112/ansible_server?style=social)


Ansible pull configuration for automated server management and configuration.

## 📋 Table of Contents

- [About](#about)
- [Features](#features)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Usage](#usage)
- [Configuration](#configuration)
- [Project Structure](#project-structure)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## 🎯 About

This repository contains Ansible playbooks and configurations designed for automated server provisioning and management using Ansible Pull. It enables servers to pull their configuration from this repository and apply it automatically, making it ideal for maintaining consistent configurations across multiple servers.

## ✨ Features

- 🔄 Automated configuration management using Ansible Pull
- 📦 Modular playbook structure for easy maintenance
- 🔐 Secure server configuration and hardening
- 🚀 Easy deployment and scalability
- 📝 Well-documented playbooks and roles
- 🔧 Customizable variables for different environments

## 🛠️ Prerequisites

Before using this project, ensure you have the following installed:

- **Ansible** >= 2.9
- **Python** >= 3.6
- **Git** (for ansible-pull functionality)
- Target servers running a supported Linux distribution (Ubuntu/Debian/CentOS/RHEL)

## 📥 Installation

### On the Control Node

1. Clone this repository:
```bash
git clone https://github.com/Freaky2112/ansible_server.git
cd ansible_server
```

2. Install Ansible (if not already installed):
```bash
# For Ubuntu/Debian
sudo apt update
sudo apt install ansible

# For RHEL/CentOS
sudo yum install ansible

# Using pip
pip install ansible
```

### On Target Servers

For ansible-pull setup on target servers:

```bash
# Install Ansible
sudo apt update && sudo apt install ansible git -y

# Run ansible-pull
ansible-pull -U https://github.com/Freaky2112/ansible_server.git
```

## 🚀 Usage

### Manual Execution

Run the playbook manually from the control node:

```bash
ansible-playbook site.yml -i inventory/hosts
```

### Ansible Pull

Configure servers to automatically pull and apply configurations:

```bash
ansible-pull \
  -U https://github.com/Freaky2112/ansible_server.git \
  -C main \
  -i localhost, \
  site.yml
```

### Scheduled Ansible Pull

Set up a cron job for automatic updates:

```bash
# Add to crontab (runs every hour)
0 * * * * ansible-pull -U https://github.com/Freaky2112/ansible_server.git -C main
```

## ⚙️ Configuration

### Inventory

Edit the inventory file to match your infrastructure:

```ini
[webservers]
web1.example.com
web2.example.com

[databases]
db1.example.com
```

### Variables

Customize variables in `group_vars/` or `host_vars/` directories:

```yaml
# group_vars/all.yml
ansible_user: admin
ansible_become: true
```

### Playbooks

Main playbook structure:
- `site.yml` - Main playbook entry point
- `roles/` - Ansible roles for different configurations
- `group_vars/` - Group-specific variables
- `host_vars/` - Host-specific variables

## 📂 Project Structure

```
ansible_server/
├── README.md
├── site.yml                 # Main playbook
├── ansible.cfg              # Ansible configuration
├── inventory/
│   └── hosts               # Inventory file
├── group_vars/
│   └── all.yml             # Global variables
├── host_vars/              # Host-specific variables
├── roles/                  # Ansible roles
│   ├── common/
│   ├── security/
│   └── monitoring/
└── playbooks/              # Additional playbooks
```

## 🤝 Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Contribution Guidelines

- Follow Ansible best practices
- Test your changes thoroughly
- Update documentation as needed
- Keep commits atomic and well-described
- Ensure all playbooks are idempotent

## 📄 License

This project is licensed under the [MIT License](LICENSE) - see the LICENSE file for details.

## 📧 Contact

**Freaky2112** - [@Freaky2112](https://github.com/Freaky2112)

Project Link: [https://github.com/Freaky2112/ansible_server](https://github.com/Freaky2112/ansible_server)

## 🙏 Acknowledgments

- [Ansible Documentation](https://docs.ansible.com/)
- [Ansible Galaxy](https://galaxy.ansible.com/)
- All contributors who have helped improve this project

## 📊 Project Status

![GitHub last commit](https://img.shields.io/github/last-commit/Freaky2112/ansible_server)
![GitHub commit activity](https://img.shields.io/github/commit-activity/m/Freaky2112/ansible_server?color=green)
---

⭐ If you find this project useful, please consider giving it a star!
