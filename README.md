# 🧪 Ansible Bootstrap - Bastion EC2 DevOps Tools

Este módulo automatiza la instalación de herramientas clave en una instancia EC2 Bastion (Amazon Linux 2023) utilizando Ansible.

---

## 🚀 Herramientas que se instalan

- `git` – Control de versiones
- `htop` – Monitor de procesos
- `unzip` – Utilidad de descompresión
- `kubectl` – CLI para gestionar clústeres Kubernetes (versión definida por variable)
- `helm` – Gestor de paquetes para Kubernetes (versión definida por variable)

---

## 📁 Estructura del proyecto

```bash

ansible-bootstrap/
├── inventory/
│   └── hosts               # IP pública de la bastión + clave SSH
├── group_vars/
│   └── all.yml             # Variables globales (versiones de kubectl y helm)
├── playbooks/
│   └── bootstrap.yml       # Playbook principal de automatización
├── ansible.cfg             # Configuración base de Ansible
└── README.md               # Este archivo

```
## ⚙️ Uso

1. Asegúrate de tener Ansible instalado localmente.
2. Define la IP de tu bastión en `inventory/hosts` y la clave `.pem`.
3. Corre el siguiente comando:

```bash

ansible-playbook playbooks/bootstrap.yml

```

## 🧠 Notas

- Las variables se cargan desde group_vars/all.yml o directamente desde vars_files.
- Si las variables no se cargan automáticamente, puedes usar vars_files dentro del playbook.
- Compatible con Amazon Linux 2 / 2023.
- Las versiones de kubectl y helm se definen en group_vars/all.yml.
- Ideal para preparar una máquina de control para gestionar un clúster EKS desde dentro de AWS.


## 🚀 Uso

1. Clona el repositorio:

   ```bash

   git clone https://github.com/Prisciflores/ansible-bootstrap.git
   cd ansible-bootstrap

   ```
   2. Configura tu archivo inventory/hosts con:

```bash

    [bastion]
    <IP_PUBLICA_BASTION> ansible_user=ec2-user ansible_ssh_private_key_file=~/.ssh/priscila-key.pem

```
3. Ejecuta el playbook

```bash

    ansible-playbook playbooks/bootstrap.yml

```

## ✍️ Autor
Creado con ❤️ por Priscila Flores