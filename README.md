# Integración Terraform-Ansible con AWS

## Descripción
Este proyecto implementa una integración completa entre Terraform y Ansible para automatizar el aprovisionamiento y la configuración de infraestructura en AWS.

## Características Principales

### Infraestructura (Terraform)
- VPC personalizada
- Subnet pública
- Grupo de seguridad para SSH
- Instancia EC2 con Ubuntu 20.04
- Gateway de Internet y configuración de rutas

### Configuración (Ansible)
- Actualización completa del sistema
- Instalación de paquetes comunes
- Configuración de seguridad
- Firewall UFW
- Actualizaciones automáticas

## Requisitos Previos
- AWS CLI configurado
- Terraform instalado
- Ansible instalado
- Cuenta AWS con permisos adecuados

## Estructura del Proyecto
```
.
├── terraform/
│   ├── main.tf           # Configuración principal de AWS
│   ├── variables.tf      # Variables de Terraform
│   └── terraform.tfvars  # Valores de las variables (no incluido en git)
├── ansible/
│   ├── ansible.cfg      # Configuración de Ansible
│   ├── inventory.yml    # Inventario dinámico
│   ├── main.yml        # Playbook principal
│   └── files/          # Archivos de configuración
└── README.md
```

## Guía de Uso

### 1. Configuración Inicial
```bash
# Configurar AWS CLI
aws configure

# Inicializar Terraform
cd terraform
terraform init
```

### 2. Despliegue de Infraestructura
```bash
# En el directorio terraform/
terraform plan
terraform apply
```

### 3. Configuración del Sistema
```bash
# En el directorio ansible/
ansible-playbook main.yml
```

## Seguridad
- Grupo de seguridad limitado a SSH
- Firewall UFW configurado
- Actualizaciones automáticas habilitadas
- Configuraciones de seguridad básicas implementadas

## Mantenimiento
- Las actualizaciones del sistema están automatizadas
- Los logs se mantienen para auditoría
- Backup configurado para datos críticos

## Contribución
Las contribuciones son bienvenidas. Por favor, asegúrate de seguir las mejores prácticas y mantener la consistencia del código.

## Licencia
Este proyecto está bajo la licencia MIT.

