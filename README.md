# 🚢 PortTrack - CI/CD & Monitoring Setup

Este repositorio contiene la configuración de integración y despliegue continuo (CI/CD) y monitoreo para la plataforma **PortTrack**, un sistema de navegación portuaria destinado a coordinar y gestionar el flujo de embarcaciones en un puerto comercial.

---

## 🛠️ Tecnologías Utilizadas

- **CI/CD**: GitHub Actions + AWS CodeDeploy
- **Monitoreo**: Prometheus, Grafana, Amazon CloudWatch
- **Contenedores**: Docker
- **Infraestructura**: Amazon EC2 + S3

---

## ⚙️ Estructura del Repositorio

📁 .github
 └── 📁 workflows
      └── deploy.yml         # Pipeline de despliegue con GitHub Actions

📁 monitoring
 ├── prometheus.yml         # Configuración de Prometheus
 └── grafana/
     └── dashboards/        # Dashboards exportables

📄 .gitignore
📄 README.md

---

## 🚀 Pipeline de Despliegue

El flujo CI/CD se ejecuta automáticamente en cada push a la rama `main`:

1. **Build & Test**: Compilación del código y validación.
2. **Deploy**: Despliegue automático a entorno STAGING o PRD mediante AWS CodeDeploy.
3. **Rollback automático** en caso de fallos.

📍 Archivo del workflow: `.github/workflows/deploy.yml`

---

## 🔐 Seguridad y Entornos

- Gestión de secretos mediante GitHub Secrets.
- Diferenciación de entornos: `DEV`, `STAGING`, `PRODUCCIÓN`.
- Pipeline incluye validación de integridad y permisos antes del despliegue.

---

## 📈 Monitoreo

- **Prometheus** para recolección de métricas.
- **Grafana** con dashboards personalizados por módulo.
- **CloudWatch** para métricas de infraestructura y alertas.
- Logs centralizados a través de `CloudWatch Logs`.

---

## 🛎️ Alertas & ChatOps

- Notificaciones de estado de despliegue vía **Slack Webhooks**.
- Configuración compatible con **Hubot** para gestión de incidentes automatizada.
- Slack recibe:
  - Estado del build
  - Inicio/fin de despliegue
  - Fallos detectados por Prometheus/CloudWatch

---

## 📌 Cómo usar este repositorio

1. Clona el proyecto:
   ```bash
   git clone https://github.com/dmontenegroh/porttrack.git
   cd porttrack-cicd
   ```

2. Configura los secretos en tu repositorio GitHub:
   - `AWS_ACCESS_KEY_ID`
   - `AWS_SECRET_ACCESS_KEY`
   - `SLACK_WEBHOOK_URL`
   - `DEPLOY_ENV` (opcional)

3. Personaliza los dashboards de Grafana y la configuración de Prometheus si lo deseas.

4. Haz push a `main` y observa el pipeline en acción 🎉

---

## 🧪 Autor / Créditos

Desarrollado como parte de la Evaluación Módulo 7 - DevOps.

Autor: Diego Montenegro  
Fecha: Julio 2025

---

## ✅ Licencia

Este proyecto es de uso académico y no tiene licencia de uso comercial.
