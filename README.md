# OBI Automation

Este repositorio contiene scripts necesarios para levantar la infraestructura de OBI.

## Requisitos

1. Servidores VPS (depende de la cantidad de concursantes).
2. Llave SSH de cada VPS.
3. Ansible instalado.

## Pasos

### 1. Aprovisionar usuarios SSH e instalar PostgreSQL
```bash
ansible-playbook -i env/hosts.ini cms/setup_environment.yml
```

### 2. Instalación del CMS
Para desplegar el CMS:
```bash
ansible-playbook -i env/hosts.ini -e @env/vars.yml cms/deploy.yml
```

### 3. Configuración de SSH
Es necesario cambiar la ruta de la llave SSH dentro del archivo `ansible.cfg`:
```ini
private_key_file = /home/sam/.ssh/id_rsa
```

### 4. Actualizar las IPs del archivo `hosts.ini`
Antes de ejecutar los playbooks, verifica que las direcciones IP de los servidores estén actualizadas en `env/hosts.ini`.