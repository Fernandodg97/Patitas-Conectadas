# Patitas Conectadas 🐾

[![Java](https://img.shields.io/badge/Java_21-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)](https://openjdk.org/)
[![Spring Boot](https://img.shields.io/badge/Spring_Boot_3-6DB33F?style=for-the-badge&logo=spring-boot&logoColor=white)](https://spring.io/projects/spring-boot)
[![React](https://img.shields.io/badge/React_19-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)](https://reactjs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)](https://www.postgresql.org/)
[![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)](https://www.docker.com/)

Red social fullstack para dueños de mascotas, desarrollada de forma autónoma como proyecto de portafolio. Cubre el stack completo: API REST con Java y Spring Boot, frontend SPA con React y TypeScript, autenticación JWT, almacenamiento de imágenes en la nube (Cloudinary), base de datos PostgreSQL en Supabase y despliegue con Docker en Render.

---

### Demo en vivo — Usuario: `usuario@usuario.com` · Contraseña: `usuario`

| | Enlace |
|---|---|
| 🌐 **Frontend** | [front-patitas-conectadas-render-com.onrender.com](https://front-patitas-conectadas-render-com.onrender.com) |
| 🔧 **API (Swagger UI)** | [api-patitasconectadas-docker.onrender.com/swagger-ui](https://api-patitasconectadas-docker.onrender.com/swagger-ui/index.html) |
| 🗄️ **Repositorio Backend** | [API-PatitasConectadas-Docker](https://github.com/Fernandodg97/API-PatitasConectadas-Docker) |
| 💻 **Repositorio Frontend** | [Front-Patitas-Conectadas-render.com](https://github.com/Fernandodg97/Front-Patitas-Conectadas-render.com) |

> Los servicios en Render pueden tardar ~30 segundos en arrancar si llevan un rato sin recibir tráfico (plan gratuito).

---

## ¿Qué es Patitas Conectadas?

Una red social donde los dueños de mascotas pueden publicar en un feed, seguirse entre sí, chatear, crear grupos y eventos, y gestionar el perfil de sus mascotas. Funcionalmente es similar a una combinación de Instagram y Facebook Groups, acotada al mundo animal.

El objetivo del proyecto no es el dominio en sí, sino demostrar la capacidad de diseñar, construir y desplegar una aplicación fullstack completa de forma autónoma.

---

## Arquitectura del sistema

```
[Usuario]
    │
    ▼
[React SPA]  ──── JWT en headers ────▶  [Spring Boot API]
                                               │
                          ┌────────────────────┼───────────────┐
                          ▼                    ▼               ▼
                    [PostgreSQL           [Cloudinary]     [Supabase]
                     en Supabase]         (imágenes)       (hosting DB)
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

---

## Qué he resuelto en este proyecto

### Autenticación y seguridad
- Registro y login con emisión de JWT firmado
- Filtros de Spring Security que validan el token en cada request entrante
- Contraseñas hasheadas con BCrypt
- Rutas protegidas en el frontend con React Router; token persistido en `localStorage`

### Subida y gestión de imágenes en la nube
- Integración completa con Cloudinary: posts, comentarios, perfiles y mascotas
- El frontend envía los archivos como `multipart/form-data`; el backend los sube y devuelve la URL pública
- Eliminación automática de la imagen anterior al actualizar, para evitar archivos huérfanos

### API REST con documentación interactiva
- 14 controladores cubriendo: auth, usuarios, perfiles, posts, comentarios, mascotas, eventos, grupos, chat, notificaciones, valoraciones y protectoras
- DTOs para separar la capa de persistencia de la API pública
- Documentación Swagger/OpenAPI accesible y navegable sin autenticación previa

### Docker y despliegue
- Build multi-stage: primera etapa compila con Maven, segunda etapa copia solo el `.jar` sobre una imagen JRE ligera
- Variables de entorno para base de datos, Cloudinary y JWT key fuera del código fuente
- La imagen se despliega directamente en Render sin pasos manuales adicionales

### Diseño responsive
- Dos modos de navegación: `Sidebar` en escritorio, `MobileBottomNav` en móvil
- Layouts construidos íntegramente con Tailwind, sin librerías de componentes externas

---

## Funcionalidades de la aplicación

| Módulo | Descripción |
|---|---|
| **Feed** | Publicaciones con imagen, comentarios y reacciones |
| **Perfil** | Foto, bio, seguidores/seguidos, valoraciones 1–5 estrellas |
| **Mascotas** | Registro con foto, especie, género y fecha de nacimiento |
| **Eventos** | Crear y apuntarse a eventos con ubicación y fecha |
| **Grupos** | Comunidades con roles Administrador / Miembro y feed propio |
| **Chat** | Mensajería directa con estado visto/no visto |
| **Notificaciones** | Centro de notificaciones por usuario |
| **Protectoras** | Sección dedicada a organizaciones de rescate animal |

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

## Autor

Desarrollador fullstack con foco en Java/Spring Boot en backend y React/TypeScript en frontend. Este proyecto lo construí de principio a fin para demostrar que puedo tomar una idea, diseñar la arquitectura, implementar ambos lados del stack y dejarlo funcionando en producción.

- **GitHub:** [github.com/Fernandodg97](https://github.com/Fernandodg97)
- **Email:** ferdiaz1997@gmail.com
