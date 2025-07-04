# CloudFormation PBMC - Laboratorio 16

Este repositorio contiene una plantilla de AWS CloudFormation diseñada para desplegar la infraestructura básica de un laboratorio de computación en la nube, siguiendo las mejores prácticas de nomenclatura y etiquetado para entornos formativos y proyectos.

## ¿Qué despliega este script?
- **VPC principal** con subredes públicas para alta disponibilidad.
- **Internet Gateway** y tabla de rutas para acceso a Internet.
- **Instancia EC2** (Amazon Linux 2023) configurada como servidor web Apache, con acceso SSH y HTTP.
- **Bucket S3** para almacenar imágenes y activos web, con acceso público de solo lectura.
- **Roles IAM** y perfil de instancia para permitir que la EC2 lea desde S3.
- **Grupo de seguridad** que habilita acceso SSH (puerto 22) y HTTP (puerto 80).
- **Etiquetas** y parámetros personalizables para identificar el contexto, usuario, fechas y ciclo/sección.

## Uso típico
1. Personaliza los parámetros en la sección `Parameters` del archivo `cloudformation.yaml` según tu contexto, usuario y fechas.
2. Sube la plantilla a AWS CloudFormation y lanza el stack.
3. Sube tus imágenes al bucket S3 creado automáticamente.
4. Accede a la IP pública de la instancia EC2 para ver la página web dinámica que carga imágenes desde S3.

## Requisitos previos
- Tener un par de claves SSH existente en tu cuenta de AWS.
- Contar con permisos para crear recursos de red, EC2, S3 e IAM en tu cuenta.

## Notas
- El acceso SSH está abierto por defecto (`0.0.0.0/0`). Para mayor seguridad, cambia este parámetro a tu IP pública.
- El bucket S3 permite lectura pública solo para mostrar imágenes en la web.
- El script está pensado para fines educativos y de laboratorio.

---

**Autor:** paulo melendez corrales 
**Proyecto:** PBMC - Asesores TI
**Fecha de creación:** 2025-07-04
