# Patitas Conectadas 🐾

[![Java](https://img.shields.io/badge/Java_21-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)](https://openjdk.org/)
[![Spring Boot](https://img.shields.io/badge/Spring_Boot_3-6DB33F?style=for-the-badge&logo=spring-boot&logoColor=white)](https://spring.io/projects/spring-boot)
[![React](https://img.shields.io/badge/React_19-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)](https://reactjs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)](https://www.postgresql.org/)
[![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)](https://www.docker.com/)
[![Scrum](https://img.shields.io/badge/Scrum-Trello-0052CC?style=for-the-badge&logo=trello&logoColor=white)]()

**TFG · Ciclo Superior de Desarrollo de Aplicaciones Web (DAW)**
**Fernando Diaz** · **Mouad Sedjari**

---

## 👋 Para recruiters

Red social fullstack para dueños de mascotas, construida de cero como Proyecto Final de Grado y llevada a producción de forma autónoma tras la entrega.

**¿Qué demuestra este proyecto?**

- ✅ Diseñar e implementar una API REST completa en **Java + Spring Boot** con seguridad JWT, JPA y documentación Swagger
- ✅ Construir un SPA en **React + TypeScript** que la consume, con rutas protegidas y diseño responsive
- ✅ Trabajar en equipo con **metodología Scrum** y gestión de tareas en Trello
- ✅ Dockerizar una aplicación, migrarla a servicios cloud (**Supabase**, **Cloudinary**) y desplegarla en **producción**

| | |
|---|---|
| 🌐 **App** | [front-patitas-conectadas-render-com.onrender.com](https://front-patitas-conectadas-render-com.onrender.com) |
| 🔧 **API (Swagger)** | [api-patitasconectadas-docker.onrender.com/swagger-ui](https://api-patitasconectadas-docker.onrender.com/swagger-ui/index.html) |
| 🗄️ **Backend** | [API-PatitasConectadas-Docker](https://github.com/Fernandodg97/API-PatitasConectadas-Docker) |
| 💻 **Frontend** | [Front-Patitas-Conectadas-render.com](https://github.com/Fernandodg97/Front-Patitas-Conectadas-render.com) |

> ⏱️ Usuario demo: `usuario@usuario.com` · Contraseña: `usuario` · Los servicios pueden tardar ~30s en arrancar (plan gratuito de Render).

---

## 🚀 Mejoras Post-Práctica

El TFG entregado funcionaba en local. Tras la defensa, Fernando continuó de forma autónoma para llevarlo a producción real:

| Mejora | Detalle |
|---|---|
| 🐳 **Dockerización** | `Dockerfile` con build multi-stage: Maven compila en la primera etapa y solo el `.jar` se copia sobre una imagen JRE ligera |
| ☁️ **Despliegue en producción** | Backend desplegado como contenedor Docker en Render; frontend como static site. Ambos accesibles públicamente |
| 🖼️ **Cloudinary** | Sustitución del almacenamiento local por Cloudinary. Subida automática de imágenes y eliminación al actualizar o borrar |
| 🗄️ **Supabase** | Migración de PostgreSQL local a Supabase con conexión SSL. Sin necesidad de instancia local para arrancar el proyecto |

---

## Stack tecnológico

**Backend** — Java 21 · Spring Boot 3.4 · Spring Security + JWT · JPA/Hibernate · PostgreSQL (Supabase) · Cloudinary · Docker · Swagger/OpenAPI

**Frontend** — React 19 · TypeScript · Vite 6 · Tailwind CSS · React Router v6 · Axios

**Proyecto** — Scrum · Trello · Git + GitHub

---

## Arquitectura

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

## Funcionalidades implementadas

| Módulo | Descripción |
|---|---|
| **Feed** | Publicaciones con imagen, comentarios y reacciones |
| **Perfil** | Foto, bio, seguidores/seguidos, valoraciones 1–5 ⭐ |
| **Mascotas** | Registro con foto, especie, género y fecha de nacimiento |
| **Eventos** | Crear y apuntarse a eventos con ubicación y fecha |
| **Grupos** | Comunidades con roles Administrador / Miembro y feed propio |
| **Chat** | Mensajería directa con estado visto/no visto |
| **Notificaciones** | Centro de notificaciones por usuario |
| **Protectoras** | Sección dedicada a organizaciones de rescate animal |

---

## Retos técnicos resueltos

**Autenticación y seguridad** — JWT firmado, filtros de Spring Security en cada request, BCrypt para contraseñas, rutas protegidas en el frontend y validaciones en todos los endpoints.

**Chat y notificaciones** — Mensajería directa con estado de lectura. Notificaciones por usuario sin WebSockets: polling ligero desde el cliente.

**Relación usuarios–mascotas** — Entidades JPA con `@OneToMany` / `@ManyToOne`. Un usuario tiene varias mascotas; posts y eventos pueden asociarse a una mascota concreta.

**Imágenes en la nube** — Subida `multipart/form-data` al backend, que delega en Cloudinary y devuelve la URL pública. Eliminación automática de la imagen anterior al actualizar.

**API con 14 controladores** — Auth, usuarios, perfiles, posts, comentarios, mascotas, eventos, grupos, chat, notificaciones, valoraciones y protectoras. DTOs para desacoplar la capa de persistencia. Swagger sin autenticación previa.

**Responsive** — Dos modos de navegación: `Sidebar` en escritorio y `MobileBottomNav` en móvil, construidos íntegramente con Tailwind.

---

## Documentación del proyecto

| Archivo | Descripción |
|---|---|
| [`DAW M12 - Patitas conectadas.pdf`](./DAW%20M12%20-%20Patitas%20conectadas%20-%20Fernando%20Diaz%20y%20Mouad%20Sedjari.pdf) | Memoria técnica completa: análisis, diseño, implementación y conclusiones |
| [`DEFENSA DEL PROYECTO.pdf`](./DEFENSA%20DEL%20PROYECTO%20-%20PATITAS%20CONECTADAS.pdf) | Guión de la defensa oral |
| [`Patitas Conectadas.pdf`](./Patitas%20Conectadas.pdf) | Presentación de diapositivas usada en la defensa |
| [`Patitas Conectadas.pptx`](./Patitas%20Conectadas.pptx) | Versión editable de la presentación |
| [`Casos de uso.pdf`](./Casos%20de%20uso.pdf) | Diagrama de casos de uso del sistema |
| [`patitasconectadas_alpha07.excalidraw`](./patitasconectadas_alpha07.excalidraw) | Wireframes y arquitectura visual (Excalidraw) |
| [`Wireframe Patitas Conectadas.png`](./Wireframe%20Patitas%20Conectadas.png) | Exportación visual del wireframe completo |

---

## Nota obtenida
9 /10

---

## Autores

| | |
|---|---|
| **Fernando Diaz** | [github.com/Fernandodg97](https://github.com/Fernandodg97) |
| **Mouad Sedjari** | [github.com/Msedjari](https://github.com/Msedjari) |

---

## Licencia

[CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/deed.es)

---

<p align="center">Made with ❤️ for animals everywhere</p>
