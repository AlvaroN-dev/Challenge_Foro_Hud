# 🗨️ Foro Hub - Plataforma de Discusión Digital

Una REST API robusta y moderna para gestión de foros desarrollada con Spring Boot, diseñada para proporcionar una experiencia completa de comunidad online con autenticación segura y operaciones CRUD optimizadas.

## 🎯 Objetivo del Proyecto

Foro Hub representa una solución integral para comunidades digitales que requieren un sistema de gestión de temas y discusiones. Desarrollado como parte del programa educativo Oracle Next Education (ONE) de Alura Latam, este proyecto demuestra la implementación de mejores prácticas en desarrollo de APIs REST, seguridad web y persistencia de datos.

## ⚡ Características Principales

### 🔐 **Sistema de Autenticación Avanzado**
- Implementación de JWT (JSON Web Tokens) para autenticación stateless
- Gestión segura de sesiones de usuario
- Middleware de autorización para protección de endpoints

### 📝 **Gestión Completa de Tópicos**
- **Creación**: Los usuarios pueden crear nuevos temas de discusión
- **Consulta**: Sistema de búsqueda y filtrado de contenido
- **Actualización**: Edición de tópicos existentes con historial de cambios
- **Eliminación Lógica**: Preservación de integridad de datos mediante soft delete

### 👥 **Gestión de Usuarios**
- Registro y autenticación de usuarios
- Perfiles de usuario con información de autoría
- Trazabilidad de acciones (creación y modificación de contenido)

### 🗄️ **Persistencia Robusta**
- Base de datos MySQL para almacenamiento confiable
- Modelo de datos optimizado para consultas eficientes
- Integridad referencial y validaciones a nivel de base de datos

## 🏗️ Arquitectura Técnica

### Stack Tecnológico
- **Backend Framework**: Spring Boot 3.x
- **Seguridad**: Spring Security + JWT
- **Base de Datos**: MySQL 8.0+
- **ORM**: Spring Data JPA / Hibernate
- **Validación**: Bean Validation (Hibernate Validator)
- **Documentación**: SpringDoc OpenAPI (Swagger)

### Patrón de Arquitectura
La aplicación sigue una arquitectura en capas (Layered Architecture):
- **Capa de Presentación**: Controladores REST
- **Capa de Lógica de Negocio**: Servicios y DTOs
- **Capa de Persistencia**: Repositorios JPA
- **Capa de Configuración**: Security Config, Database Config

## 🚀 Guía de Instalación

### Prerrequisitos del Sistema
```bash
- Java JDK 17 o superior
- MySQL Server 8.0+
- Maven 3.6+
- IDE compatible (IntelliJ IDEA, Eclipse, VS Code)
```

### Pasos de Configuración

1. **Clonar el Repositorio**
   ```bash
   git clone https://github.com/AlvaroN-dev/Challenge_Foro_Hud
   cd Foro-Hub
   ```

2. **Configurar Base de Datos**
   ```sql
   CREATE DATABASE foro_hub_db;
   CREATE USER 'foro_user'@'localhost' IDENTIFIED BY 'secure_password';
   GRANT ALL PRIVILEGES ON foro_hub_db.* TO 'foro_user'@'localhost';
   ```

3. **Configurar Propiedades de Aplicación**
   ```properties
   # application.properties
   spring.datasource.url=jdbc:mysql://localhost:3306/foro_hub_db
   spring.datasource.username=foro_user
   spring.datasource.password=secure_password
   jwt.secret=your-secret-key-here
   jwt.expiration=86400000
   ```

4. **Ejecutar la Aplicación**
   ```bash
   mvn spring-boot:run
   ```

La API estará disponible en: `http://localhost:8080`

## 📋 Endpoints Principales

### Autenticación
```http
POST /api/auth/login
Content-Type: application/json

{
  "email": "usuario@ejemplo.com",
  "password": "contraseña123"
}
```

### Gestión de Tópicos
```http
# Listar tópicos (con paginación)
GET /api/topicos?page=0&size=10&sort=fechaCreacion,desc

# Crear nuevo tópico
POST /api/topicos
Authorization: Bearer {jwt-token}

# Obtener tópico específico
GET /api/topicos/{id}

# Actualizar tópico
PUT /api/topicos/{id}
Authorization: Bearer {jwt-token}

# Eliminar tópico (lógicamente)
DELETE /api/topicos/{id}
Authorization: Bearer {jwt-token}
```

## 🖼️ Capturas del Sistema

### Panel de Documentación API (Swagger)
La API incluye documentación interactiva generada automáticamente, facilitando la integración y testing de endpoints.

### Gestión de Autenticación
Sistema de login seguro con validaciones tanto en frontend como backend.

### CRUD de Tópicos
Interfaz intuitiva para la gestión completa del ciclo de vida de los temas de discusión.

## 🔧 Tecnologías y Herramientas

| Categoría | Tecnología | Propósito |
|-----------|------------|-----------|
| **Backend** | ![Java](https://img.shields.io/badge/Java_17-%23ED8B00.svg?style=flat-square&logo=openjdk&logoColor=white) | Lenguaje principal |
| **Framework** | ![Spring Boot](https://img.shields.io/badge/Spring_Boot-%236DB33F.svg?style=flat-square&logo=spring&logoColor=white) | Framework de aplicación |
| **Seguridad** | ![JWT](https://img.shields.io/badge/JWT-black?style=flat-square&logo=JSON%20web%20tokens) | Autenticación stateless |
| **Base de Datos** | ![MySQL](https://img.shields.io/badge/MySQL-%2300f.svg?style=flat-square&logo=mysql&logoColor=white) | Sistema de gestión de BD |
| **IDE** | ![IntelliJ IDEA](https://img.shields.io/badge/IntelliJ_IDEA-000000.svg?style=flat-square&logo=intellij-idea&logoColor=white) | Entorno de desarrollo |
| **Testing** | ![Postman](https://img.shields.io/badge/Postman-FF6C37?style=flat-square&logo=postman&logoColor=white) | Pruebas de API |
| **Control de Versiones** | ![Git](https://img.shields.io/badge/Git-%23F05033.svg?style=flat-square&logo=git&logoColor=white) | Sistema de control de versiones |

## 📄 Licencia

Este proyecto está bajo la Licencia MIT. Consulta el archivo `LICENSE` para más detalles.
