# Informe: Integración de Terraform, AWS y Ansible

## 1. Descripción General del Proyecto

Este proyecto implementa una solución de Infraestructura como Código (IaC) que integra Terraform y Ansible para aprovisionar y configurar infraestructura en AWS de manera automatizada. El proyecto permite:

- **Aprovisionar infraestructura en AWS** utilizando Terraform
- **Configurar automáticamente** los recursos aprovisionados mediante Ansible
- **Asegurar la infraestructura** con medidas de seguridad básicas
- **Mantener la consistencia** en todas las implementaciones

La integración entre Terraform y Ansible se logra mediante la generación automática de archivos de inventario, permitiendo un flujo de trabajo fluido desde el aprovisionamiento hasta la configuración de los recursos.

## 2. Configuración de Infraestructura (Terraform)

### Componentes Aprovisionados

Utilizando Terraform, se han aprovisionado los siguientes recursos en AWS:

| Recurso | Descripción |
|---------|-------------|
| VPC | Red virtual privada con CIDR 10.0.0.0/16 |
| Subred pública | Subred con CIDR 10.0.1.0/24 en la zona de disponibilidad us-east-1a |
| Internet Gateway | Para permitir el acceso a Internet desde la VPC |
| Tablas de enrutamiento | Configuradas para dirigir el tráfico público |
| Grupo de seguridad | Reglas de acceso para SSH (puerto 22) |
| Instancia EC2 | Máquina virtual t2.micro ejecutando Ubuntu 20.04 LTS |

### Archivos de Configuración Terraform

La configuración de Terraform se divide en varios archivos:

- **main.tf**: Contiene la definición principal de los recursos de AWS
- **variables.tf**: Define las variables utilizadas en la configuración
- **terraform.tfvars**: Establece los valores específicos para las variables

### Flujo de Aprovisionamiento

1. Inicialización del directorio de trabajo de Terraform (`terraform init`)
2. Planificación de la infraestructura (`terraform plan`)
3. Aplicación de los cambios para crear la infraestructura (`terraform apply`)
4. Generación automática del archivo de inventario de Ansible con la IP pública de la instancia EC2

## 3. Configuración del Sistema (Ansible)

### Tareas de Configuración

Ansible fue utilizado para configurar automáticamente la instancia EC2 con:

| Categoría | Acciones |
|-----------|----------|
| Actualizaciones | Actualización de paquetes del sistema |
| Software | Instalación de utilidades comunes (vim, curl, wget, git, etc.) |
| Desarrollo | Instalación de herramientas de desarrollo (python3, pip, etc.) |
| Seguridad | Configuración de actualizaciones automáticas y firewall UFW |
| Zona horaria | Configuración de zona horaria a America/New_York |

### Archivos de Configuración Ansible

La configuración de Ansible se organizó en:

- **ansible.cfg**: Configuración general de Ansible
- **inventory.yml**: Inventario dinámico que obtiene la IP de la instancia EC2
- **main.yml**: Playbook principal con todas las tareas de configuración

### Verificación

Para verificar la correcta configuración, Ansible:
- Realizó un ping para confirmar la conectividad
- Ejecutó tareas con verificaciones de estado
- Creó un archivo de verificación (`ansible_was_here.txt`) en la instancia
- Mostró la información del sistema configurado

## 4. Medidas de Seguridad

### Seguridad de la Red

Se implementaron las siguientes medidas de seguridad en la infraestructura:

- **Acceso restringido**: Solo se permite tráfico SSH (puerto 22) entrante
- **VPC aislada**: La infraestructura se implementa en una VPC dedicada
- **Subred pública controlada**: Diseño de red con rutas definidas explícitamente

### Seguridad del Sistema

En el nivel del sistema operativo, se configuraron:

- **Actualizaciones automáticas de seguridad**: Mediante unattended-upgrades
- **Firewall UFW**: Habilitado con política de denegación por defecto para tráfico entrante
- **SSH**: Configuración segura para el acceso remoto

### Consideraciones Adicionales

Para entornos de producción, se recomienda:
- Restringir el acceso SSH a rangos IP específicos
- Implementar un host bastión para acceso SSH
- Utilizar AWS Systems Manager Session Manager en lugar de SSH directo
- Considerar la implementación de VPN para el acceso seguro

## 5. Resultados y Verificación

### Resultados del Aprovisionamiento

La infraestructura fue aprovisionada correctamente, como se verifica por:
- Estado exitoso de `terraform apply`
- Creación de todos los recursos definidos en AWS
- Generación correcta del archivo de IP para Ansible

### Resultados de la Configuración

La configuración del sistema fue exitosa, como se confirma por:
- Conexión SSH establecida correctamente
- Actualización e instalación de todos los paquetes
- Configuración correcta del firewall
- Creación del archivo de verificación en la instancia

### Estado Final

El sistema está completamente aprovisionado y configurado, listo para:
- Desplegar aplicaciones
- Implementar servicios adicionales
- Ser utilizado como base para entornos más complejos

## 6. Conclusiones

La integración de Terraform y Ansible proporciona una solución poderosa para la gestión de infraestructura como código, permitiendo:

1. **Automatización completa** desde el aprovisionamiento hasta la configuración
2. **Reproducibilidad** de la infraestructura en cualquier momento
3. **Control de versiones** de la infraestructura junto con el código
4. **Escalabilidad** para gestionar desde una hasta cientos de instancias

Este proyecto demuestra la efectividad de combinar estas herramientas para crear un flujo de trabajo DevOps completo para la gestión de infraestructura en la nube.

---

