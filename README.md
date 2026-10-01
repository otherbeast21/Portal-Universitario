<div align="center">

# 🎓 Portal Universitario

### La infraestructura digital que tu universidad necesitaba ayer

[![Status](https://img.shields.io/badge/status-production--ready-3ddc97?style=for-the-badge)]()
[![Docker](https://img.shields.io/badge/docker-ready-2496ED?style=for-the-badge&logo=docker&logoColor=white)]()
[![Flask](https://img.shields.io/badge/flask-3.0.3-000000?style=for-the-badge&logo=flask&logoColor=white)]()
[![CI/CD](https://img.shields.io/badge/CI%2FCD-Git%20workflow-FF6B6B?style=for-the-badge&logo=github&logoColor=white)]()

**Un portal web empaquetado, versionado y desplegable en minutos — no en meses.**

</div>

---

## 💡 El problema

Las universidades siguen gestionando portales estudiantiles con servidores frágiles, sin control de versiones serio y sin forma clara de saber **qué cambió, quién lo cambió y cuándo**. Un solo error 500 puede dejar a miles de estudiantes sin acceso a sus trámites — y nadie sabe cuánto tarda en resolverse.

## 🚀 La solución

Portal Universitario es una aplicación web **contenedorizada** (Docker) con un flujo de trabajo de desarrollo **auditable y reproducible** basado en Git:

| Problema típico | Cómo lo resolvemos |
|---|---|
| "Funciona en mi máquina" | Todo corre en un contenedor Docker idéntico en cualquier entorno |
| Cambios sin rastro | Cada corrección y cada feature vive en su propia rama, con historial completo (`git log --graph`) |
| Errores en producción sin plan | Flujo de *hotfix* aislado: se corrige, se valida en Docker, y se fusiona sin tocar lo demás |
| Despliegues manuales y lentos | Una sola imagen Docker, lista para desplegar en cualquier nube o servidor |

## ⚙️ Cómo funciona (60 segundos)

```bash
git clone https://github.com/otherbeast21/Portal-Universitario.git
cd Portal-Universitario
docker build -t portal-universitario .
docker run -p 5000:5000 portal-universitario
```

Y ya está corriendo en `http://localhost:5000`.

## 🧱 Arquitectura

```
┌─────────────────────┐
│   Flask (app.py)     │  → Lógica de la aplicación
├─────────────────────┤
│   requirements.txt    │  → Dependencias controladas
├─────────────────────┤
│   Dockerfile          │  → Empaquetado reproducible
└─────────────────────┘
        │
        ▼
  Contenedor Docker ──► Puerto 5000 ──► Usuarios
```

## 📡 Endpoints disponibles

| Ruta | Método | Descripción |
|---|---|---|
| `/` | GET | Página de bienvenida del portal |
| `/api/status` | GET | Health check del servicio → `{"status": "ok", "entorno": "contenedor-docker", "version": "1.1.0"}` |

El endpoint `/api/status` no es decorativo: es lo que permite monitoreo automático, integraciones con balanceadores de carga y alertas tempranas — la diferencia entre enterarte de una caída por un estudiante enojado o por un sistema que te avisa en segundos.

## 🌿 Flujo de ramas (nuestro proceso real)

```
main ──●──────────●──────────●──  (estable, siempre desplegable)
        \          \        /
         ● hotfix   ● feature/
           /error-500   status-endpoint
```

- **`main`** — única fuente de verdad, siempre en estado desplegable.
- **`hotfix/*`** — correcciones urgentes, aisladas, validadas en Docker antes de fusionar.
- **`feature/*`** — nuevas capacidades, desarrolladas sin arriesgar producción.

Cada commit queda documentado y es auditable con `git log --oneline --graph --all`.

## 📈 Por qué esto escala

- **Portable**: la misma imagen Docker corre igual en un laptop, en un servidor universitario o en la nube.
- **Versionado real**: cada cambio tiene autor, fecha y propósito — cero cajas negras.
- **Bajo riesgo**: los errores se corrigen en ramas aisladas sin detener el desarrollo de nuevas funciones.
- **Listo para crecer**: la estructura actual (Flask + Docker + endpoint de status) es la base mínima sobre la que se montan autenticación, base de datos, pagos de colegiatura, calificaciones y más — sin rehacer nada desde cero.

## 🛠️ Stack

`Python` · `Flask` · `Docker` · `Git` · `GitHub`

## 📬 Siguiente paso

Este repositorio es la prueba de que el equipo ya domina el ciclo completo: desarrollo, control de versiones, contenedorización y despliegue. Lo que falta no es tecnología — es **inversión para escalarlo** a miles de usuarios reales.

<div align="center">

**¿Hablamos de los próximos $10M?**

</div>
