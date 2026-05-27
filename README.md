cat > README.md << 'EOF'
# TaskFlow - Sistema de Gestión de Tareas

Proyecto grupal del módulo **Énfasis Profesional I (Integración Continua)**  
Politécnico Grancolombiano — Grupo 4

## Integrantes
- Julián García
- Freizer Rozo
- Sebastián Molina

---

## Descripción

TaskFlow es una API REST desarrollada en Python con Flask para la gestión de tareas. Usa PostgreSQL como base de datos. El proyecto está completamente contenerizado con Docker, demostrando el uso de herramientas de integración continua.

## Tecnologías

- Python 3.11 + Flask
- PostgreSQL 15
- Docker & Docker Compose
- GitHub

## Arquitectura de contenedores

| Contenedor | Imagen | Puerto |
|---|---|---|
| `taskflow_api` | Python 3.11 + Flask | 5001 |
| `taskflow_db` | PostgreSQL 15 | 5432 |

Los dos contenedores se comunican a través de la red interna `taskflow_network`.

## Cómo ejecutar el proyecto

### 1. Clonar el repositorio
```bash
git clone https://github.com/freizerrozo/Intg-cont-grupo4.git
cd Intg-cont-grupo4
```

### 2. Levantar los contenedores
```bash
docker-compose up --build
```

### 3. Probar la API

| Método | Endpoint | Descripción |
|---|---|---|
| GET | `/` | Estado de la API |
| GET | `/tasks` | Listar todas las tareas |
| POST | `/tasks` | Crear una tarea |
| PUT | `/tasks/<id>` | Actualizar una tarea |
| DELETE | `/tasks/<id>` | Eliminar una tarea |

**Ejemplo — Crear una tarea:**
```bash
curl -X POST http://localhost:5001/tasks \
  -H "Content-Type: application/json" \
  -d '{"title": "Mi primera tarea", "description": "Descripción de ejemplo"}'
```

### 4. Detener los contenedores
```bash
docker-compose down
```
EOF
