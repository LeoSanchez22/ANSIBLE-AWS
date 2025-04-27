# Guía Rápida de Uso

## 1. Clonar el Repositorio
```bash
git clone https://github.com/LeoSanchez22/ANSIBLE-AWS.git
cd ANSIBLE-AWS
```

## 2. Configurar AWS
```bash
# Configurar credenciales AWS
aws configure
```

## 3. Desplegar Infraestructura
```bash
# Inicializar y aplicar Terraform
cd terraform
terraform init
terraform plan
terraform apply
```

## 4. Configurar Sistema
```bash
# Ejecutar playbook de Ansible
cd ../ansible
ansible-playbook main.yml
```

## 5. Verificar Instalación
```bash
# Verificar conexión SSH
ssh -i ~/.ssh/id_rsa ubuntu@<IP-INSTANCIA>

# Verificar estado del sistema
sudo systemctl status
sudo ufw status
```

## Comandos Útiles

### Terraform
```bash
terraform show     # Ver estado actual
terraform destroy  # Eliminar infraestructura
```

### Ansible
```bash
ansible all -m ping              # Verificar conectividad
ansible-playbook -v main.yml     # Ejecutar con verbose
```

### AWS
```bash
aws ec2 describe-instances       # Listar instancias
aws ec2 describe-security-groups # Ver grupos de seguridad
```

## Recordatorios Importantes
1. Mantener actualizadas las credenciales AWS
2. Verificar los costos de AWS regularmente
3. Hacer backup de los estados de Terraform
4. Revisar logs del sistema periódicamente

Para más detalles, consultar:
- DETALLES.md - Documentación técnica
- TROUBLESHOOTING.md - Solución de problemas
