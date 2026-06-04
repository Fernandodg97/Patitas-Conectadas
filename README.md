# Patitas Conectadas 🐾

[![Java](https://img.shields.io/badge/Java_21-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)](https://openjdk.org/)
[![Spring Boot](https://img.shields.io/badge/Spring_Boot_3-6DB33F?style=for-the-badge&logo=spring-boot&logoColor=white)](https://spring.io/projects/spring-boot)
[![React](https://img.shields.io/badge/React_19-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)](https://reactjs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)](https://www.postgresql.org/)
[![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)](https://www.docker.com/)
[![Scrum](https://img.shields.io/badge/Metodología-Scrum-0052CC?style=for-the-badge&logo=trello&logoColor=white)]()

**Proyecto Final de Grado · Desarrollo de Aplicaciones Web (DAW)**
Desarrollado en equipo por **Fernando Diaz** y **Mouad Sedjari**.

Red social fullstack especializada en mascotas: API REST con Java y Spring Boot, frontend SPA con React y TypeScript, autenticación JWT, almacenamiento de imágenes en Cloudinary, base de datos PostgreSQL en Supabase, despliegue con Docker en Render y metodología ágil Scrum.

---

### 🚀 Demo en vivo — Usuario: `usuario@usuario.com` · Contraseña: `usuario`

| | Enlace |
|---|---|
| 🌐 **Frontend** | [front-patitas-conectadas-render-com.onrender.com](https://front-patitas-conectadas-render-com.onrender.com) |
| 🔧 **API (Swagger UI)** | [api-patitasconectadas-docker.onrender.com/swagger-ui](https://api-patitasconectadas-docker.onrender.com/swagger-ui/index.html) |
| 🗄️ **Repositorio Backend** | [API-PatitasConectadas-Docker](https://github.com/Fernandodg97/API-PatitasConectadas-Docker) |
| 💻 **Repositorio Frontend** | [Front-Patitas-Conectadas-render.com](https://github.com/Fernandodg97/Front-Patitas-Conectadas-render.com) |

> ⏱️ Los servicios en Render pueden tardar ~30 segundos en arrancar si llevan un rato sin recibir tráfico (plan gratuito).

---

## ¿Qué es Patitas Conectadas?

Redes como Instagram o Facebook no están pensadas para gestionar perfiles de mascotas ni para conectar a personas que comparten el cuidado de sus animales. Patitas Conectadas cubre ese hueco: una red social vertical donde los dueños pueden publicar en un feed, seguirse entre sí, chatear, crear grupos y eventos, y gestionar el perfil de sus mascotas, todo en un entorno pensado exclusivamente para ello.

El proyecto es el TFG de DAW de Fernando y Mouad, desarrollado con metodología Scrum, gestión de tareas en Trello y desplegado en producción.

---

## Arquitectura del sistema

```
[Usuario]
    │
    ▼
[React SPA]  ──── JWT en headers ────▶  [Spring Boot API]
                                               │
                     ┌─────────────────────────┼──────────────────┐
                     ▼                         ▼                  ▼
               [PostgreSQL               [Cloudinary]        [Supabase]
                en Supabase]             (imágenes)          (hosting DB)
```

---

## Stack tecnológico

### Backend

| Categoría | Tecnología |
|---|---|
| Lenguaje | Java 21 |
| Framework | Spring Boot 3.4 |
| Seguridad | Spring Security + JWT (jjwt) |
| ORM | Spring Data JPA + Hibernate |
| Base de datos | PostgreSQL en Supabase |
| Almacenamiento | Cloudinary |
| Documentación | SpringDoc OpenAPI (Swagger UI) |
| Contenedores | Docker (build multi-stage) |
| Despliegue | Render (desde imagen Docker) |

**→ Repositorio:** [API-PatitasConectadas-Docker](https://github.com/Fernandodg97/API-PatitasConectadas-Docker)

### Frontend

| Categoría | Tecnología |
|---|---|
| UI | React 19 + TypeScript |
| Build | Vite 6 |
| Estilos | Tailwind CSS |
| Routing | React Router v6 |
| HTTP | Axios |
| Despliegue | Render (static site) |

**→ Repositorio:** [Front-Patitas-Conectadas-render.com](https://github.com/Fernandodg97/Front-Patitas-Conectadas-render.com)

### Gestión del proyecto

| | |
|---|---|
| Metodología | Scrum |
| Tablero | Trello (sprints, backlog, revisiones) |
| Control de versiones | Git + GitHub |

---

## Funcionalidades

| Módulo | Descripción |
|---|---|
| **Feed** | Publicaciones con imagen, comentarios y reacciones |
| **Perfil** | Foto, bio, seguidores/seguidos, valoraciones 1–5 ⭐ |
| **Mascotas** | Registro con foto, especie, género y fecha de nacimiento |
| **Eventos** | Crear y apuntarse a eventos con ubicación y fecha |
| **Grupos** | Comunidades con roles Administrador / Miembro y feed propio |
| **Chat** | Mensajería directa con estado visto/no visto |
| **Notificaciones** | Centro de notificaciones en tiempo real por usuario |
| **Protectoras** | Sección dedicada a organizaciones de rescate animal |

---

## Retos técnicos resueltos

### Autenticación y seguridad
- Registro y login con emisión de JWT firmado
- Filtros de Spring Security que validan el token en cada request entrante
- Contraseñas hasheadas con BCrypt
- Rutas protegidas en el frontend con React Router; sesión persistida en `localStorage`
- Validaciones de entrada en todos los endpoints de la API

### Chat y notificaciones en tiempo real
- Sistema de mensajería directa con estado de lectura (visto/no visto)
- Centro de notificaciones por usuario integrado en el backend y consumido desde el frontend
- Gestión del estado de conversaciones activas sin WebSockets: polling ligero desde el cliente

### Relación usuarios–mascotas
- Un usuario puede tener varias mascotas con perfil propio (foto, especie, género, edad)
- Los posts y eventos pueden asociarse a una mascota concreta del perfil
- Diseño de entidades JPA con relaciones `@OneToMany` / `@ManyToOne` correctamente mapeadas

### Subida y gestión de imágenes en la nube
- Integración completa con Cloudinary: posts, comentarios, perfiles y mascotas
- El frontend envía archivos como `multipart/form-data`; el backend los sube y devuelve la URL pública
- Eliminación automática de la imagen anterior al actualizar, para evitar archivos huérfanos

### API REST con documentación interactiva
- 14 controladores cubriendo: auth, usuarios, perfiles, posts, comentarios, mascotas, eventos, grupos, chat, notificaciones, valoraciones y protectoras
- DTOs para desacoplar la capa de persistencia de la API pública
- Swagger/OpenAPI navegable sin autenticación previa

### Docker y despliegue
- Build multi-stage: Maven compila en la primera etapa, el `.jar` final se copia sobre una imagen JRE ligera
- Variables de entorno para base de datos, Cloudinary y JWT key fuera del código fuente
- La imagen se despliega directamente en Render sin pasos manuales adicionales

### Diseño responsive
- Dos modos de navegación: `Sidebar` en escritorio, `MobileBottomNav` en móvil
- Layouts construidos íntegramente con Tailwind, sin librerías de componentes externas

---

## Cómo probarlo

**Desde el frontend:**
1. Abre [front-patitas-conectadas-render-com.onrender.com](https://front-patitas-conectadas-render-com.onrender.com)
2. Inicia sesión con `usuario@usuario.com` / `usuario`
3. Explora el feed, crea un post, entra en un grupo o abre el chat

**Desde Swagger (API directa):**
1. Abre [Swagger UI](https://api-patitasconectadas-docker.onrender.com/swagger-ui/index.html)
2. Ejecuta `POST /auth/login` con las credenciales de prueba
3. Copia el token, pulsa **Authorize** e introduce `Bearer <token>`
4. Llama a cualquier endpoint protegido

---

## Visión de futuro

- 📱 Aplicación móvil nativa (React Native)
- 🏥 Integración con veterinarias y ONGs de rescate
- 🛒 Marketplace de productos para mascotas
- 💳 Sistema freemium con suscripciones premium

---

## 🚀 Mejoras Post-Práctica

El proyecto entregado como TFG funcionaba en local. Tras la defensa, Fernando continuó el desarrollo de forma autónoma para dejarlo listo para producción:

| Mejora | Detalle |
|---|---|
| 🐳 **Dockerización** | Creación de un `Dockerfile` con build multi-stage: Maven compila en la primera etapa y solo el `.jar` final se copia sobre una imagen JRE ligera, reduciendo el tamaño de la imagen al mínimo |
| ☁️ **Despliegue en producción** | La imagen Docker se despliega automáticamente en Render. El frontend se sirve como static site, también en Render. Ambos servicios están activos y accesibles públicamente |
| 🖼️ **Cloudinary** | Sustitución del almacenamiento local de imágenes por Cloudinary. Las imágenes de posts, perfiles, mascotas y comentarios se suben a la nube y se eliminan automáticamente al actualizar o borrar |
| 🗄️ **Supabase** | Migración de la base de datos local a PostgreSQL en Supabase con conexión SSL, eliminando la necesidad de tener una instancia local para ejecutar el proyecto |

---

## Documentación del proyecto

Este repositorio agrupa toda la documentación generada durante el desarrollo del TFG:

| Archivo | Descripción |
|---|---|
| [`DAW M12 - Patitas conectadas - Fernando Diaz y Mouad Sedjari.pdf`](./DAW%20M12%20-%20Patitas%20conectadas%20-%20Fernando%20Diaz%20y%20Mouad%20Sedjari.pdf) | Memoria técnica completa del proyecto (M12 · DAW): análisis, diseño, implementación y conclusiones |
| [`DEFENSA DEL PROYECTO - PATITAS CONECTADAS.pdf`](./DEFENSA%20DEL%20PROYECTO%20-%20PATITAS%20CONECTADAS.pdf) | Guión de la defensa oral: exposición comercial, desarrollo técnico, demo guiada y conclusiones |
| [`Patitas Conectadas.pdf`](./Patitas%20Conectadas.pdf) | Presentación en diapositivas usada durante la defensa del TFG |
| [`Patitas Conectadas.pptx`](./Patitas%20Conectadas.pptx) | Versión editable de la presentación (PowerPoint) |
| [`Casos de uso.pdf`](./Casos%20de%20uso.pdf) | Diagrama de casos de uso del sistema |
| [`patitasconectadas_alpha07.excalidraw`](./patitasconectadas_alpha07.excalidraw) | Diseño de wireframes y arquitectura visual elaborado en Excalidraw |
| [`Wireframe Patitas Conectadas.png`](./Wireframe%20Patitas%20Conectadas.png) | Exportación visual del wireframe completo de la aplicación |

---

## Autores

| | |
|---|---|
| **Fernando Diaz** | [github.com/Fernandodg97](https://github.com/Fernandodg97) |
| **Mouad Sedjari** | [github.com/Msedjari](https://github.com/Msedjari) |

Proyecto Final de Grado · Ciclo Superior de Desarrollo de Aplicaciones Web (DAW)

---

## Licencia

[CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/deed.es)

---

<p align="center">Made with ❤️ for animals everywhere</p>

