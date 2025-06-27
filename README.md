# 📄 Informe de Auditoría de Sistemas  
## Auditoría al Despliegue DevIA360 basado en Vagrant y Chef  
**Nombre del Auditor**: La Torre Esquivel, José André  
**Curso**: Auditoría de Sistemas – Unidad 3  
**Repositorio**: [AS_U3_EXAMEN_PRACTICO](https://github.com/tu_usuario/AS_U3_EXAMEN_PRACTICO)  

---

## 1. Resumen Ejecutivo

Se presenta el informe de auditoría realizado sobre el proceso de despliegue continuo del entorno DevIA360, implementado con herramientas Vagrant y Chef. Durante la auditoría se identificaron configuraciones inseguras, credenciales expuestas y ausencia de prácticas de segmentación de entornos. A partir de estos hallazgos se emitieron recomendaciones orientadas a mejorar la seguridad, trazabilidad y eficiencia del despliegue automatizado.

---

## 2. Introducción

### 2.1. Contexto  
El entorno DevIA360 representa una solución de automatización para la instalación de WordPress mediante Vagrant y Chef. El propósito de esta auditoría es evaluar su configuración actual y determinar riesgos potenciales.

### 2.2. Objetivo General  
Auditar el entorno de despliegue DevIA360 con el fin de detectar vulnerabilidades y mejorar la gestión automatizada del software.

### 2.3. Objetivos Específicos  
- Validar la correcta ejecución del entorno Vagrant.  
- Revisar configuraciones de red, puertos y acceso en Vagrantfile.  
- Analizar las recetas de Chef para detectar riesgos de seguridad.  
- Realizar pruebas de seguridad sobre el entorno desplegado.  
- Elaborar una matriz de riesgos basada en los hallazgos.

### 2.4. Alcance  
Esta auditoría se limita al entorno de pruebas local generado por el repositorio Chef_Vagrant_Wp, incluyendo archivos de configuración, ejecución de comandos y pruebas de acceso.

---

## 3. Metodología

La auditoría se desarrolló en tres fases: preparación del entorno, revisión técnica de configuraciones y análisis de seguridad. Se utilizaron evidencias capturadas en tiempo real y se aplicaron criterios de buenas prácticas en DevOps y seguridad de sistemas.

---

## 4. Preparación del Entorno

### 🔹 Clonación y Ejecución

```bash
git clone https://github.com/tu_usuario/Chef_Vagrant_Wp.git
cd Chef_Vagrant_Wp
vagrant up
