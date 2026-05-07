# gh-cep-b

# Laboratorio GitHub Actions - Hangman 🚀

Este repositorio contiene la automatización de CI/CD para el proyecto Hangman utilizando GitHub Actions.

## Workflows Detallados

### 1. CI (Integración Continua) - Frontend
- **Archivo:** `frontend-ci.yml`
- **Disparador (Trigger):** Se activa automáticamente ante un `pull_request` siempre que se modifiquen archivos dentro de la carpeta `hangman-front/`.
- **Pasos:** 1. Checkout del código.
  2. Instalación de dependencias de Node.js.
  3. Construcción del proyecto (`npm run build`).
  4. Ejecución de pruebas unitarias (`npm test`).
- **Acciones usadas:** `actions/checkout@v4`, `actions/setup-node@v4`.

### 2. CD (Despliegue Continuo) - Frontend
- **Archivo:** `frontend-cd.yml`
- **Disparador:** Manual (`workflow_dispatch`).
- **Pasos:**
  1. Autenticación en el registro de contenedores de GitHub (GHCR).
  2. Construcción de la imagen Docker basada en el `Dockerfile` de `hangman-front`.
  3. Publicación de la imagen en GHCR.
- **Acciones usadas:** `docker/login-action@v3`, `docker/build-push-action@v5`.

### 3. Tests End-to-End (E2E)
- **Archivo:** `e2e-tests.yml`
- **Disparador:** Manual y cada vez que hay un `push` a la rama `main`.
- **Descripción:** Ejecuta las pruebas de integración usando Cypress sobre la carpeta `hangman-e2e`.
- **Acciones usadas:** `cypress-io/github-action@v6`.

---
*Entregado por: Miguel Ángel*