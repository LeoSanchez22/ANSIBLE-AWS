# Guía de Solución de Problemas

## Verificación de Conexión

### AWS
```bash
# Verificar credenciales AWS
aws sts get-caller-identity

# Verificar VPC
aws ec2 describe-vpcs

# Verificar instancia EC2
aws ec2 describe-instances
```

### SSH
```bash
# Verificar conexión SSH
ssh -i ~/.ssh/id_rsa ubuntu@<IP-INSTANCIA>

# Verificar permisos de llave SSH
ls -l ~/.ssh/id_rsa
chmod 600 ~/.ssh/id_rsa
```

### Terraform
```bash
# Limpiar estado de Terraform
terraform init
terraform workspace show
terraform state list

# Problemas comunes
terraform plan -refresh-only
terraform validate
```

### Ansible
```bash
# Verificar sintaxis del playbook
ansible-playbook --syntax-check main.yml

# Ejecutar playbook en modo verbose
ansible-playbook -vv main.yml

# Verificar conectividad
ansible all -m ping
```

## Problemas Comunes

### Error de Conexión SSH
1. Verificar grupo de seguridad
2. Confirmar IP pública correcta
3. Verificar permisos de llave SSH
4. Comprobar usuario correcto (ubuntu)

### Error de Terraform
1. Verificar credenciales AWS
2. Limpiar cache: rm -rf .terraform
3. Reinicializar: terraform init
4. Verificar versión: terraform version

### Error de Ansible
1. Verificar inventory.yml
2. Comprobar ansible.cfg
3. Verificar permisos sudo
4. Revisar logs: /var/log/ansible.log

## Comandos de Depuración

### Sistema
```bash
# Verificar estado del sistema
systemctl status

# Verificar firewall
sudo ufw status verbose

# Verificar actualizaciones
sudo apt update
sudo apt list --upgradable
```

### Logs
```bash
# Logs del sistema
tail -f /var/log/syslog

# Logs de seguridad
tail -f /var/log/auth.log

# Logs de AWS
tail -f /var/log/cloud-init.log
```

## Contacto y Soporte
Para problemas adicionales, crear un issue en el repositorio o contactar al equipo de mantenimiento.

## Referencias
- [Documentación de Terraform](https://www.terraform.io/docs)
- [Documentación de Ansible](https://docs.ansible.com)
- [AWS CLI Documentation](https://aws.amazon.com/cli)

