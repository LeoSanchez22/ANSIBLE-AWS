# Terraform-Ansible AWS Integration

Este proyecto implementa una integración entre Terraform y Ansible para el aprovisionamiento y configuración automatizada de infraestructura en AWS.

## Estructura del Proyecto

```
Infra-Ansible/
├── terraform/
│   ├── main.tf           # Configuración principal de AWS
│   ├── variables.tf      # Definición de variables
│   └── terraform.tfvars  # Valores de las variables
├── ansible/
│   ├── ansible.cfg       # Configuración de Ansible
│   ├── inventory.yml     # Inventario dinámico
│   └── main.yml         # Playbook principal
```

## Componentes Implementados

### Terraform
- VPC con subnet pública
- Grupo de seguridad (SSH)
- Instancia EC2 (Ubuntu 20.04)
- Configuración de red completa

### Ansible
- Actualizaciones del sistema
- Configuración de seguridad
- Instalación de utilidades comunes
- Configuración de firewall (UFW)
- Actualizaciones automáticas

## Seguridad
- Firewall UFW configurado
- Actualizaciones automáticas habilitadas
- Grupo de seguridad AWS limitado

## Uso
1. Configurar credenciales AWS
2. Ejecutar Terraform
```bash
cd terraform
terraform init
terraform apply
```
3. Ejecutar Ansible
```bash
cd ../ansible
ansible-playbook main.yml
```

