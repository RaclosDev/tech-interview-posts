# API REST de Posts - Simulación de Entrevista Técnica

Este proyecto es el resultado de una simulación de entrevista técnica para un desarrollador backend. El objetivo es construir un microservicio en Spring Boot que consume una API externa, implementa una capa de servicio y expone una API REST propia con funcionalidades CRUD completas y un manejo de errores robusto.

---

## Enunciado del Ejercicio

Se requiere desarrollar un servicio backend que cumpla con los siguientes requisitos funcionales:

1.  **Consumo de API Externa**: El servicio debe conectarse a la API pública `https://jsonplaceholder.typicode.com/posts` para obtener los datos base.
2.  **Exponer Posts**: Crear un endpoint `GET /api/v1/posts` para devolver todos los posts.
3.  **Obtener Post por ID**: Crear un endpoint `GET /api/v1/posts/{id}` para obtener un post específico.
4.  **Manejo de Errores (404)**: Si se solicita un post con un ID que no existe, la API debe devolver un error `404 Not Found` con un mensaje claro en formato JSON.
5.  **Filtrado por Parámetros**: El endpoint `GET /api/v1/posts` debe aceptar un parámetro de consulta opcional (`userId`) para filtrar los posts por autor (ej: `/api/v1/posts?userId=1`).
6.  **Crear un Nuevo Post**: Implementar `POST /api/v1/posts` para crear un nuevo recurso. La respuesta debe ser `201 Created` y devolver el objeto creado.
7.  **Validación de Entrada (400)**: La creación de posts debe validar que los campos `title` y `body` no estén vacíos. En caso de fallo, debe devolver `400 Bad Request` con detalles del error.
8.  **Actualizar un Post**: Implementar `PUT /api/v1/posts/{id}` para actualizar completamente un recurso existente.
9.  **Borrar un Post**: Implementar `DELETE /api/v1/posts/{id}` para eliminar un recurso. La respuesta debe ser `204 No Content`.
10. **Centralización de Errores**: Utilizar un gestor de excepciones global (`@ControllerAdvice`) para manejar los errores de forma centralizada y consistente.

---

## Tecnologías Utilizadas 🛠️

* Java 17
* Spring Boot 3.x
* Maven
* Spring Web
* Spring Boot Validation
* Lombok

---

## Cómo Empezar 🚀

#### Prerrequisitos

* JDK 17 o superior.
* Apache Maven 3.6 o superior.
* Git.

#### Instalación y Ejecución

1.  **Clona el repositorio:**
    ```bash
    git clone [https://github.com/tu-usuario/tu-repositorio.git](https://github.com/tu-usuario/tu-repositorio.git)
    cd tu-repositorio
    ```
2.  **Ejecuta la aplicación usando Maven:**
    ```bash
    mvn spring-boot:run
    ```
    La API estará disponible en `http://localhost:8080`.

---

## Documentación de la API 📖

La URL base para todos los endpoints es `/api/v1/posts`.

### Obtener todos los Posts
* **Endpoint:** `GET /`
* **Filtrado:** `GET /?userId={id}`
* **Respuesta Exitosa (200 OK):**
    ```json
    [
        {
            "userId": 1,
            "id": 1,
            "title": "sunt aut facere repellat provident occaecati excepturi optio reprehenderit",
            "body": "quia et suscipit..."
        }
    ]
    ```

### Obtener Post por ID
* **Endpoint:** `GET /{id}`
* **Respuesta Exitosa (200 OK):**
    ```json
    {
        "userId": 1,
        "id": 1,
        "title": "sunt aut facere repellat provident occaecati excepturi optio reprehenderit",
        "body": "quia et suscipit..."
    }
    ```
* **Respuesta de Error (404 Not Found):**
    ```json
    {
        "timestamp": "2025-07-01T12:30:00.12345",
        "message": "Post no encontrado con el ID: 999",
        "details": "uri=/api/v1/posts/999"
    }
    ```

### Crear un Nuevo Post
* **Endpoint:** `POST /`
* **Cuerpo de la Petición:**
    ```json
    {
        "userId": 1,
        "title": "Un título nuevo",
        "body": "El contenido del post."
    }
    ```
* **Respuesta Exitosa (201 Created):** Devuelve el objeto creado con su nuevo `id`.

### Actualizar un Post
* **Endpoint:** `PUT /{id}`
* **Cuerpo de la Petición:**
    ```json
    {
        "userId": 1,
        "id": 1,
        "title": "Título completamente actualizado",
        "body": "Cuerpo modificado."
    }
    ```
* **Respuesta Exitosa (200 OK):** Devuelve el objeto actualizado.

### Borrar un Post
* **Endpoint:** `DELETE /{id}`
* **Respuesta Exitosa (204 No Content):** No devuelve contenido.

---

## Herramientas Adicionales ⚙️

### Colección de Postman
Este repositorio incluye una colección de Postman con todas las peticiones de la API preconfiguradas.

* **Ubicación:** `/postman/Tech_Interview_API.postman_collection.json`
* **Uso:** Importa este archivo en Postman para empezar a probar los endpoints inmediatamente.
