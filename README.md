# ulern-login-register-test

## Descripción del Proyecto
Este proyecto es un sistema de login y registro de usuarios desarrollado utilizando Laravel 11 para el backend y Vue 3 para el frontend, con estilos proporcionados por TailwindCSS y SQLite como base de datos.

## Estructura del Proyecto
El proyecto está organizado en dos carpetas principales: `backend` y `frontend`.

### Backend
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

### Frontend
- **src/assets**: Activos estáticos como imágenes y fuentes.
- **src/components**: Componentes de Vue para formularios de registro y login.
- **src/views**: Vistas de Vue para la aplicación.
- **src/App.vue**: Componente raíz de Vue.
- **src/main.js**: Inicializa la aplicación Vue.
- **public**: Archivos accesibles públicamente para la aplicación Vue.
- **tailwind.config.js**: Configuración de TailwindCSS.
- **package.json**: Configuración de npm para la aplicación Vue.

## Instrucciones de Instalación y Ejecución

### Requisitos Previos
- PHP 8.1 o superior
- Composer
- Node.js y npm

### Instalación del Backend
1. Navega a la carpeta `backend`.
2. Copia el archivo `.env.example` a `.env` y configura la conexión a la base de datos SQLite.
3. Ejecuta `composer install` para instalar las dependencias de PHP.
4. Ejecuta `php artisan migrate` para crear las tablas en la base de datos.
5. Ejecuta `php artisan serve` para iniciar el servidor de desarrollo.

### Instalación del Frontend
1. Navega a la carpeta `frontend`.
2. Ejecuta `npm install` para instalar las dependencias de JavaScript.
3. Ejecuta `npm run serve` para iniciar el servidor de desarrollo de Vue.

## Acceso a la Aplicación
- El backend estará disponible en `http://localhost:8000`.
- El frontend estará disponible en `http://localhost:3000`.

## Funcionalidades
- Registro de usuario con nombre, apellido, número de teléfono, email y contraseña.
- Inicio de sesión con email y contraseña.
- Página de perfil que muestra los datos del usuario registrado.

## Buenas Prácticas
Este proyecto sigue buenas prácticas de desarrollo, incluyendo una estructura de código clara y coherente, manejo adecuado de errores y documentación detallada.

## Contribuciones
Las contribuciones son bienvenidas. Por favor, abre un issue o un pull request para discutir cambios o mejoras.