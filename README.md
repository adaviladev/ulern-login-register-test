# Proyecto de Prueba Técnica - Ulern

## Descripción

Este proyecto es una prueba técnica para el puesto de desarrollador Fullstack Jr. en Ulern. El objetivo es implementar un sistema de login y registro utilizando Laravel 11 para el backend, Vue 3 para el frontend, TailwindCSS para los estilos y SQLite como base de datos.

## Tecnologías Utilizadas

- **Backend:** Laravel 11
- **Frontend:** Vue 3
- **Estilos:** TailwindCSS
- **Base de Datos:** SQLite

## Funcionalidades Principales

- **Registro de Usuario:**
  - Campos: nombre, apellido, número de teléfono, email y contraseña.
- **Inicio de Sesión:**
  - Campos: email y contraseña.
- **Página de Perfil:**
  - Visualización de los datos del usuario registrado.

## Instrucciones de Instalación y Ejecución

### Requisitos Previos

- PHP 8.1 o superior
- Composer
- Node.js y npm

### Instalación del Backend

1. Navega a la carpeta `backend`.
2. Copia el archivo `.env.example` a `.env` y configura la conexión a la base de datos SQLite.
3. Genera la clave de la aplicación: php artisan key:generate
4. Ejecuta composer install para instalar las dependencias de PHP.
5. Ejecuta php artisan migrate para crear las tablas en la base de datos.
6. Ejecuta php artisan serve para iniciar e servidor de desarrollo.

### Instalación del Frontend

1. Ejecuta npm install para instalar las dependencias de JavaScript.

### Acceso a la Aplicación

La aplicación estará disponible en http://localhost:8000.

## Estructura del Proyecto

### Backend:
- **app**: Contiene la lógica principal de la aplicación, incluyendo modelos, controladores y middleware.
- **bootstrap**: Archivos para inicializar la aplicación Laravel.
- **config**: Archivos de configuración para la aplicación.
- **database/migrations**: Migraciones para crear y modificar tablas en la base de datos.
- **database/seeders**: Archivos para poblar la base de datos con datos iniciales.
- **public**: Archivos accesibles públicamente, incluyendo el punto de entrada de la aplicación.
- **resources/views**: Plantillas Blade para renderizar vistas.
- **routes/web.php**: Define las rutas web de la aplicación.
- **storage**: Almacena logs, caché y otros archivos generados.
- **tests**: Archivos de prueba para asegurar la funcionalidad de la aplicación.
- **artisan**: Interfaz de línea de comandos para Laravel.
- **composer.json**: Configuración de dependencias para Composer.
- **.env.example**: Archivo de configuración de entorno de ejemplo.


### Frontend:
- **src/assets**: Activos estáticos como imágenes y fuentes.
- **src/components**: Componentes de Vue para formularios de registro y login.
- **src/views**: Vistas de Vue para la aplicación.
- **src/App.vue**: Componente raíz de Vue.
- **src/main.js**: Inicializa la aplicación Vue.
- **public**: Archivos accesibles públicamente para la aplicación Vue.
- **tailwind.config.js**: Configuración de TailwindCSS.
- **package.json**: Configuración de npm para la aplicación Vue.

## Buenas Prácticas
Este proyecto sigue buenas prácticas de desarrollo, incluyendo una estructura de código clara y coherente, manejo adecuado de errores y documentación detallada.

## Contribuciones
Las contribuciones son bienvenidas. Por favor, abre un issue o un pull request para discutir cambios o mejoras.

## Contacto
Si tienes alguna pregunta o necesitas más información, no dudes en contactarme a través de tu-email@example.com.