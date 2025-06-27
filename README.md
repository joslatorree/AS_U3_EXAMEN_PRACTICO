
# ![Logo](https://upload.wikimedia.org/wikipedia/commons/thumb/8/84/Logo_UPT.png/600px-Logo_UPT.png)

## Facultad de Ingeniería - Carrera Profesional de Sistemas  
### Examen de Unidad  
### Informe de Auditoría de Sistemas  
**Auditor:** La Torre Esquivel, José André  
**Fecha:** 27 de junio de 2025  
**Repositorio**: [AS_U3_EXAMEN_PRACTICO](https://github.com/tu_usuario/AS_U3_EXAMEN_PRACTICO)  

---

## 1. Resumen Ejecutivo

A continuación, se presenta el informe de auditoría del entorno de despliegue DevIA360, el cual se basa en el uso de herramientas como Vagrant y Chef para la automatización de infraestructura.  
Durante la auditoría se evaluó la ejecución, configuración y seguridad del entorno desplegado, identificando vulnerabilidades asociadas al manejo de credenciales, configuración de red y prácticas DevOps.  
Se propone una matriz de riesgos y recomendaciones para mitigar los hallazgos críticos y mejorar la eficiencia operativa.

---

## 2. Introducción

Este informe se elabora como parte del examen práctico de la asignatura Auditoría de Sistemas, enfocado en la revisión del entorno de despliegue continuo DevIA360, desplegado localmente con Vagrant y Chef.

### Objetivo General
Auditar el entorno DevIA360 para detectar vulnerabilidades en su configuración automatizada mediante Vagrant y Chef.

### Objetivos Específicos
1. Validar la correcta ejecución del entorno con `vagrant up`.
2. Revisar configuraciones de red, puertos y acceso en `Vagrantfile`.
3. Analizar las recetas de Chef para detectar riesgos de seguridad.
4. Realizar pruebas de seguridad sobre el entorno desplegado.
5. Elaborar una matriz de riesgos basada en los hallazgos.

---

## 3. Hallazgos Preliminares

### 3.1 Evidencia de ejecución

- **Anexo A**: `vagrant status`
  ![Anexo A](evidencias/anexo_a_vagrant_status.png)

- **Anexo B**: WordPress en ejecución
  ![Anexo B](evidencias/anexo_b_wordpress.png)

### 3.2 Configuraciones inseguras detectadas

- **Anexo C**: Vagrantfile expone IPs estáticas sin validación
  ```ruby
  db.vm.network "private_network", ip: ENV["DB_IP"]
  ```

- **Anexo D**: `.env` contiene credenciales en texto plano
  ```env
  DB_USER = 'wordpress'
  DB_PSWD = 'Epnewman123'
  ```

- **Anexo E**: Falta de versión específica en `metadata.rb` (pendiente de captura)

- **Anexo F**: `/var/log/` sin logs de aplicación visibles (pendiente)

- **Anexo G**: No hay segregación de entornos (todo apunta a entorno único)

---

## 4. Recomendaciones

- Reemplazar uso de `.env` por variables seguras y cifradas.
- Validar disponibilidad de IPs antes del despliegue.
- Agregar versionado en `metadata.rb` para cada receta.
- Implementar roles separados para desarrollo y producción.
- Configurar logging estructurado y rotación de logs.

---

## 5. Conclusiones

El entorno DevIA360 cumple su función técnica de desplegar WordPress, pero presenta fallas de seguridad y trazabilidad que lo hacen vulnerable.  
Las mejoras sugeridas deben ser implementadas antes de utilizar este entorno en producción.

---

## 6. Referencias

- Vagrant Docs: https://developer.hashicorp.com/vagrant/docs  
- Chef Infra Docs: https://docs.chef.io/chef/  
- OWASP DevSecOps Guide: https://owasp.org/www-project-devsecops-guideline/

---

## 7. Matriz de Riesgos

| Riesgo                        | Causa (Anexo)             | Impacto | Probabilidad | Nivel de Riesgo |
|------------------------------|---------------------------|---------|--------------|-----------------|
| Credenciales sin cifrado     | `.env`, `Vagrantfile` (D) | Alto    | 90%          | Crítico         |
| IPs fijas no validadas       | `.env` (C)                | Medio   | 75%          | Alto            |
| Ausencia de segregación      | Recetas y red (G)         | Medio   | 80%          | Alto            |
| Logs no gestionados          | `/var/log/` vacío (F)     | Alto    | 70%          | Alto            |
