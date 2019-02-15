PHP Metrics
===========

Install php analysers like phpmd, phpcs, phpstan, phplint, phpcpd, ext.

### Setup in Your Project

```bash
mkdir -p etc/ansible/common && mkdir -p etc/ansible/requirements

cat > etc/ansible/requirements.yml << EOF
- name: common-php-metrics
  src: https://github.com/muhammadtaqi/php-metrics.git
  scm: git
EOF

cat > etc/ansible/metrics.yml << EOF
---
- hosts: localhost
  connection: local

  roles:
    - { role: common-php-metrics }
EOF

cat > etc/ansible.cfg << EOF
[defaults]
roles_path=ansible/common
EOF
```

## Run ansible playbook

```bash
cd ./etc/
ansible-galaxy install -r ansible/requirements.yml -p ansible/common --force
ansible-playbook  ansible/metrics.yml --limit=localhost --flush-cache
```