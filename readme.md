# Full Stack FastAPI – Local (Windows, sin Docker)

Repositorio **full-stack funcional en entorno local (Windows)**, basado en FastAPI y Vite, **sin Docker ni Copier**, orientado a usuarios que desean ejecutar y comprender el proyecto de forma directa.

Este README documenta **exclusivamente lo que fue ejecutado y validado** en este repositorio.

---

## 📌 Origen del proyecto

Este repositorio es una **modificación y adaptación** del template oficial:

👉 https://github.com/fastapi/full-stack-fastapi-template

El repositorio original es **más completo y mejor documentado**, e incluye:

- Docker y docker-compose
- Inicialización automática de servicios
- Creación automática de superusuario
- Uso de **Copier** para generar el proyecto
- Enfoque orientado a entornos avanzados o productivos

### 🎯 Propósito de esta versión

Esta adaptación fue creada para:

> **Usuarios no familiarizados con Docker ni con Copier**, que desean ejecutar el template Full Stack FastAPI **en local**, de forma explícita y controlada.

Por ello, esta versión:

- ❌ No utiliza Docker
- ❌ No utiliza Copier
- ✅ Usa ejecución local directa
- ✅ Gestiona dependencias del backend con **`uv`**
- ✅ Conecta a **PostgreSQL externo** vía variables de entorno
- ✅ Requiere **creación manual del superusuario**
- ✅ Prioriza la comprensión del flujo por sobre la automatización

Si necesitas un stack productivo y totalmente automatizado, se recomienda usar el **template oficial**.

---

## 📁 Estructura del proyecto

```text
full-stack-fastapi-template/
├── backend/
│   ├── app/
│   │   └── main.py
│   ├── pyproject.toml
│   ├── uv.lock
│   ├── alembic.ini
│   └── .env
├── frontend/
├── hooks/
├── img/
├── scripts/
├── .env
├── .gitignore
└── LICENSE
```

---

## ⚙️ Requisitos del entorno (probados)

- Sistema operativo: **Windows**
- Python instalado
- **uv** instalado y operativo
- Node.js + npm
- PostgreSQL (local o remoto)
- Visual Studio Code

---

## 📥 Clonar el repositorio

```powershell
git clone https://github.com/jrpino59/full-stack-fastapi-local-windows.git
cd full-stack-fastapi-template
```

---

## 🐍 Backend – FastAPI (sin Docker)

### 📍 Ruta

```text
full-stack-fastapi-template\backend
```

### 📦 Instalación de dependencias

Este proyecto **no usa `pip` ni `requirements.txt`**. Las dependencias se instalan con **uv**, a partir de `pyproject.toml` y `uv.lock`:

```powershell
uv sync
```

---

## 🗄️ Configuración de PostgreSQL

El backend se conecta a **PostgreSQL externo**, sin contenedores.

Las credenciales se definen mediante variables de entorno, normalmente en:

```text
backend/.env
```

### 🔐 Variables requeridas (ejemplo)

```env
POSTGRES_SERVER=localhost
POSTGRES_PORT=5432
POSTGRES_DB=app_db
POSTGRES_USER=app_user
POSTGRES_PASSWORD=app_password
```

Los valores concretos dependen de tu instalación de PostgreSQL.

---

## ▶️ Levantar el backend (validado)

```powershell
fastapi dev app/main.py
```

### ✅ Resultado

- API disponible en: http://127.0.0.1:8000
- Swagger (OpenAPI): http://127.0.0.1:8000/docs

---

## 👤 Creación del superusuario (OBLIGATORIO)

⚠️ **Al no usar Docker, el superusuario NO se crea automáticamente**.

Debe crearse **manualmente mediante código o script**, antes del primer login.

Este paso:
- Se ejecuta **una sola vez por base de datos**
- Es necesario para acceder al panel admin y al CRUD

Sin este paso, el sistema levantará pero **no será usable**.

---

## 🎨 Frontend – Vite

### 📍 Ruta

```text
full-stack-fastapi-template\frontend
```

### 📦 Instalación de dependencias

```powershell
npm install
```

### ▶️ Levantar frontend (validado)

```powershell
npm run dev
```

Frontend disponible en:

```text
http://localhost:5173
```

---

## 🔐 Autenticación

- Página de login: http://localhost:5173/login
- Autenticación JWT funcional
- Integración real frontend ↔ backend

---

## 🧭 Panel principal (Dashboard)

Tras login exitoso:

- Dashboard operativo
- Menú lateral funcional (Dashboard / Items / Admin)
- Sesión activa

---

## 📦 CRUD de Items (validado)

El CRUD fue probado **end-to-end**:

- CREATE
- READ
- UPDATE
- DELETE
- Persistencia real en PostgreSQL
- Acceso protegido por autenticación

---

## 🔁 Flujo funcional validado

1. Clonar repositorio
2. Instalar dependencias backend con `uv`
3. Configurar PostgreSQL vía `.env`
4. Crear superusuario manualmente
5. Levantar backend
6. Instalar y levantar frontend
7. Login
8. Dashboard
9. CRUD operativo

---

## 📌 Alcance documentado

### ✅ Incluido

- Entorno local Windows
- Backend FastAPI sin Docker
- PostgreSQL externo
- Autenticación
- CRUD completo
- Frontend integrado

### ❌ No incluido

- Docker
- Producción
- CI/CD
- Despliegue cloud

---

## 📝 Nota final

Este README describe **únicamente el comportamiento real observado**.

Si algo no aparece aquí, **no fue validado**.

