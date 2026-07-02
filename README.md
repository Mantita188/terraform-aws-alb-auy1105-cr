# Módulo de Balanceo de Carga AWS ALB - AUY1105

## Objetivos del Repositorio
Desacoplar la infraestructura del Application Load Balancer (ALB), sus Target Groups y Listeners para permitir una distribución de tráfico segura, modular y altamente disponible.

## Propósito General
Este módulo automatiza la creación de un Application Load Balancer externo, exponiendo un DNS público. Asocia un Target Group configurado con Health Checks HTTP en el puerto 80 y engancha dinámicamente la instancia EC2 cómputo provista para recibir el tráfico balanceado a través de sus subredes públicas.

## Requisitos (Inputs)
| Nombre | Descripción | Tipo | Obligatorio |
| :--- | :--- | :---: | :---: |
| `environment` | Ambiente de despliegue (ej: dev, prod) | `string` | Sí |
| `vpc_id` | ID de la VPC de red de destino | `string` | Sí |
| `alb_security_group_id` | ID del Security Group autorizado para el ALB | `string` | Sí |
| `public_subnets` | Lista de IDs de subredes públicas (mínimo 2 para HA) | `list(string)` | Sí |
| `instance_id` | ID de la instancia EC2 para el Target Group Attachment | `string` | Sí |

## Salidas (Outputs)
| Nombre | Descripción |
| :--- | :--- |
| `alb_dns_name` | Nombre DNS público generado por el Application Load Balancer |