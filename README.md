# Ansible Cloud Playbooks

## 10 Production-Ready Ansible Playbooks for Cloud Engineers

This repository contains 10 comprehensive Ansible playbooks designed for cloud infrastructure management across AWS, Azure, GCP, and OCI. Perfect for DevOps engineers, cloud architects, and infrastructure automation specialists.

### 📋 Playbook List

1. **AWS EC2 Instance Deployment** - Launch and configure EC2 instances with security groups, tags, and monitoring
2. **Linux Security Hardening** - CIS Benchmark compliance, firewall, SELinux, and SSH hardening
3. **Docker Container Management** - Install Docker, manage containers, images, and registry operations
4. **Kubernetes Cluster Setup** - Deploy K8s cluster with kubeadm, networking, and storage configuration  
5. **Web Server Stack (LEMP/LAMP)** - Deploy Nginx/Apache with PHP, MySQL, SSL certificates
6. **Database Replication** - MySQL/PostgreSQL master-slave replication with backup automation
7. **Monitoring Stack (Prometheus+Grafana)** - Deploy complete monitoring solution with exporters
8. **Load Balancer Configuration** - HAProxy/Nginx load balancing with health checks
9. **Log Aggregation (ELK Stack)** - Elasticsearch, Logstash, Kibana deployment and configuration
10. **CI/CD Pipeline (GitLab Runner)** - Deploy and configure GitLab Runners for CI/CD automation

### 📁 Directory Structure

```
ansible-cloud-playbooks/
├── README.md
├── ansible.cfg
├── inventory/
│   ├── hosts.ini
│   └── group_vars/
├── playbooks/
│   ├── 01-aws-ec2-deployment.yml
│   ├── 02-linux-security-hardening.yml
│   ├── 03-docker-container-management.yml
│   ├── 04-kubernetes-cluster-setup.yml
│   ├── 05-lemp-web-stack.yml
│   ├── 06-database-replication.yml
│   ├── 07-prometheus-grafana-monitoring.yml
│   ├── 08-haproxy-load-balancer.yml
│   ├── 09-elk-stack-deployment.yml
│   └── 10-gitlab-runner-setup.yml
├── roles/
│   ├── aws-ec2/
│   ├── linux-security/
│   ├── docker/
│   └── kubernetes/
├── group_vars/
│   └── all.yml
└── templates/
    ├── security-config.j2
    └── monitoring-config.j2
```

### 🚀 Quick Start

#### Prerequisites
- Ansible 2.10+
- Python 3.8+
- AWS CLI / Azure CLI / GCP SDK (depending on platform)
- SSH access to target hosts

#### Installation

```bash
# Clone repository
git clone https://github.com/Manjunathsmurthy/ansible-cloud-playbooks.git
cd ansible-cloud-playbooks

# Install dependencies
pip install -r requirements.txt
ansible-galaxy install -r requirements.yml

# Update inventory
vi inventory/hosts.ini

# Run playbook
ansible-playbook playbooks/01-aws-ec2-deployment.yml -i inventory/hosts.ini
```

### 📚 Playbook Details

#### 1. AWS EC2 Instance Deployment
Deploys EC2 instances with VPC, security groups, EBS volumes, and monitoring.
```bash
ansible-playbook playbooks/01-aws-ec2-deployment.yml -e "instance_count=3 instance_type=t3.medium"
```

#### 2. Linux Security Hardening  
Implements CIS Benchmarks, disables root SSH, configures firewall (UFW/FirewallD).
```bash
ansible-playbook playbooks/02-linux-security-hardening.yml --become
```

#### 3. Docker Container Management
Installs Docker, pulls images, runs containers, manages volumes and networks.
```bash
ansible-playbook playbooks/03-docker-container-management.yml
```

#### 4. Kubernetes Cluster Setup
Deployskubeadm-based K8s cluster with networking (Flannel/Calico) and storage (EBS/AzureDisk).
```bash
ansible-playbook playbooks/04-kubernetes-cluster-setup.yml -i inventory/k8s_hosts.ini
```

#### 5. LEMP/LAMP Web Stack
Deploys Nginx/Apache, PHP, MySQL, SSL (Let's Encrypt), and performance tuning.
```bash
ansible-playbook playbooks/05-lemp-web-stack.yml --tags=nginx,php,mysql,ssl
```

#### 6. Database Replication
Configures MySQL/PostgreSQL master-slave replication with automated backups and recovery.
```bash
ansible-playbook playbooks/06-database-replication.yml
```

#### 7. Prometheus & Grafana Monitoring
Deploys Prometheus, Grafana, Node Exporter, MySQL Exporter with pre-built dashboards.
```bash
ansible-playbook playbooks/07-prometheus-grafana-monitoring.yml
```

#### 8. HAProxy Load Balancer
Configures HAProxy with health checks, SSL termination, and multiple backends.
```bash
ansible-playbook playbooks/08-haproxy-load-balancer.yml
```

#### 9. ELK Stack Deployment
Deploys Elasticsearch cluster, Logstash pipelines, Kibana dashboards, and log shipping.
```bash
ansible-playbook playbooks/09-elk-stack-deployment.yml --vault-password-file=.vault
```

#### 10. GitLab Runner CI/CD Setup
Installs GitLab Runner, registers executors (docker, shell, kubernetes), and configures jobs.
```bash
ansible-playbook playbooks/10-gitlab-runner-setup.yml -e "gitlab_url=https://gitlab.com gitlab_token=xxxx"
```

### 🔐 Security Best Practices

- All sensitive data stored in Ansible Vault (`group_vars/secrets.yml`)
- SSH keys managed securely with proper permissions
- Playbooks use `become: yes` with password-less sudo for safety
- Firewall rules validated before application
- TLS/SSL certificates auto-generated where applicable

### 🧪 Testing & Validation

```bash
# Syntax check
ansible-playbook playbooks/01-aws-ec2-deployment.yml --syntax-check

# Dry run
ansible-playbook playbooks/01-aws-ec2-deployment.yml --check

# Lint with ansible-lint
ansible-lint playbooks/
```

### 📖 Documentation

Each playbook includes:
- Detailed comments explaining each task
- Variable definitions and defaults
- Error handling and validation
- Rollback procedures
- Performance tuning recommendations

### 🤝 Contributing

Contributions welcome! Please:
1. Test playbooks thoroughly
2. Follow Ansible best practices
3. Add documentation
4. Submit pull requests

### 📝 License

MIT License - See LICENSE file

### ✨ Author

Manjunathsmurthy - Cloud Architect & DevOps Engineer

### 📞 Support

For issues, questions, or suggestions, please open a GitHub issue.
