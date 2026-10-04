# CRUD Vue 3 + Axios + Flask

Aplicación web de ventas desarrollada para el curso de Desarrollo Web (036), utilizando Vue 3 en el frontend y Flask en el backend.

El sistema permite administrar clientes, productos y pedidos mediante una API REST, con persistencia de información en una base de datos SQLite.

---

## Descripción del proyecto

La aplicación implementa un sistema básico de ventas que permite realizar operaciones CRUD sobre tres entidades principales:

- Clientes
- Productos
- Pedidos

El frontend está desarrollado con Vue 3 y utiliza Axios para consumir los servicios REST proporcionados por Flask.

El proyecto está dividido en dos aplicaciones independientes:

- `backend`: API REST desarrollada con Flask.
- `frontend`: interfaz web desarrollada con Vue 3 y Vite.

La aplicación permite navegar entre las diferentes vistas sin recargar el navegador.

---

## Tecnologías utilizadas

### Backend

- Python 3.11 o superior
- Flask
- Flask-SQLAlchemy
- Flask-Migrate
- Flask-CORS
- python-dotenv
- pytest
- SQLite

### Frontend

- Vue 3
- Vite
- Vue Router
- Axios
- JavaScript
- HTML
- CSS

### Herramientas

- Git
- GitHub
- Visual Studio Code
- PowerShell

---

## Requisitos previos

Antes de ejecutar el proyecto se debe contar con:

- Python 3.11 o superior
- Node.js
- npm
- Git
- PowerShell en Windows

Para comprobar las instalaciones:

```powershell
py --version
node --version
npm --version
git --version

Estructura del proyecto
El proyecto está dividido en dos aplicaciones principales: backend y frontend. Esta separación permite organizar las responsabilidades del sistema y facilitar su mantenimiento.
Backend
El backend está desarrollado con Flask y se encarga de la lógica del servidor, la conexión con la base de datos y la API REST.
- app/: contiene la aplicación principal de Flask.
- models.py: define los modelos y las relaciones de las tablas Clientes, Productos y Pedidos.
- extensions.py: configura las extensiones utilizadas por Flask, como SQLAlchemy, Flask-Migrate y CORS.
- errors.py: contiene funciones para manejar errores y validar campos obligatorios.
- api/: contiene las rutas de la API para realizar las operaciones CRUD de clientes, productos y pedidos.
- migrations/: contiene las migraciones utilizadas para crear y actualizar la estructura de la base de datos.
- tests/: contiene las pruebas automatizadas del backend.
- run.py: es el punto de entrada para ejecutar la aplicación Flask.
- .env.example: muestra las variables de entorno necesarias para configurar el backend.
Frontend
El frontend está desarrollado con Vue 3, Vite y Axios y proporciona la interfaz con la que interactúa el usuario.
- src/api/: contiene las funciones encargadas de comunicarse con la API mediante Axios.
- src/components/: contiene componentes reutilizables como botones, campos de entrada, tablas y mensajes de alerta.
- src/views/: contiene las vistas principales de Dashboard, Clientes, Productos y Pedidos.
- src/router/: configura las rutas y la navegación entre las diferentes vistas.
- App.vue: contiene la estructura principal de la interfaz y el menú de navegación.
- main.js: inicia la aplicación Vue.
- assets/main.css: contiene los estilos generales de la aplicación.
Funcionamiento general
El usuario interactúa con el frontend Vue, que realiza las solicitudes mediante Axios hacia la API REST de Flask. El backend procesa las solicitudes utilizando los modelos de SQLAlchemy y almacena la información en la base de datos.
El proyecto implementa operaciones CRUD para las tres entidades principales:
- Clientes: crear, consultar, actualizar y eliminar.
- Productos: crear, consultar, actualizar y eliminar.
- Pedidos: crear, consultar, actualizar el estado y eliminar bajo las condiciones establecidas.
Esta organización sigue la estructura propuesta en el manual, donde components contiene elementos reutilizables, views las páginas, api las llamadas HTTP y router la navegación.     Manual_Windows_CRUD_Vue3_Axios_…
Validaciones
El sistema cuenta con validaciones tanto en el frontend como en el backend. Entre ellas se encuentran:
- Validación de campos obligatorios.
- Validación de precios y cantidades.
- Validación de existencia de clientes y productos.
- Validación de stock disponible al crear pedidos.
- Validación de estados de los pedidos.
- Un pedido solamente puede eliminarse cuando está cancelado.
- Los registros relacionados no pueden eliminarse cuando existen restricciones establecidas.