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

## Para comprobar las instalaciones

```powershell
py --version
node --version
npm --version
git --version
```

---

## Estructura del proyecto

El proyecto está dividido en dos aplicaciones principales: `backend` y `frontend`.

### Backend

El backend está desarrollado con Flask y se encarga de la lógica del servidor, la API REST y la conexión con la base de datos.

- `app/`: contiene la aplicación principal de Flask.
- `app/models.py`: contiene los modelos de Clientes, Productos y Pedidos.
- `app/api/`: contiene las rutas de la API para las operaciones CRUD.
- `app/extensions.py`: configura las extensiones utilizadas por Flask.
- `app/errors.py`: contiene el manejo de errores y validaciones.
- `migrations/`: contiene las migraciones de la base de datos.
- `tests/`: contiene las pruebas automatizadas del backend.
- `run.py`: punto de entrada para ejecutar la aplicación Flask.
- `.env.example`: ejemplo de las variables de entorno necesarias para el backend.

### Frontend

El frontend está desarrollado con Vue 3, Vite y Axios.

- `src/api/`: contiene la comunicación con la API mediante Axios.
- `src/components/`: contiene componentes reutilizables.
- `src/views/`: contiene las vistas de Dashboard, Clientes, Productos y Pedidos.
- `src/router/`: configura las rutas de navegación.
- `src/App.vue`: contiene la estructura principal y el menú de navegación.
- `src/main.js`: inicia la aplicación Vue.
- `src/assets/main.css`: contiene los estilos generales de la aplicación.

---

## Funcionamiento

El frontend Vue realiza solicitudes mediante Axios hacia la API REST de Flask.

El backend procesa las solicitudes utilizando SQLAlchemy y realiza las operaciones correspondientes sobre la base de datos.

El sistema implementa operaciones CRUD para:

- Clientes
- Productos
- Pedidos

Además, se incluyen validaciones tanto en el frontend como en el backend.

---

## Ejecución del proyecto

El proyecto se ejecuta con el backend y el frontend en terminales independientes.

### Backend

Desde la carpeta raíz:

```powershell
cd backend
.venv\Scripts\Activate.ps1
```

Aplicar las migraciones:

```powershell
flask --app run.py db upgrade
```

Iniciar Flask:

```powershell
flask --app run.py run --debug
```

El backend estará disponible en:

`http://127.0.0.1:5000`

### Frontend

Abrir una segunda terminal desde la carpeta raíz:

```powershell
cd frontend
npm install
npm run dev
```

El frontend estará disponible en:

`http://localhost:5173`

### Acceso a la aplicación

Con ambos servicios en ejecución, abrir:

`http://localhost:5173`

Desde la aplicación se puede acceder a:

- Dashboard
- Clientes
- Productos
- Pedidos

---

## Funcionalidades

### Clientes

Permite:

- Crear clientes.
- Consultar clientes registrados.
- Editar información de clientes.
- Eliminar clientes.

### Productos

Permite:

- Crear productos.
- Consultar productos registrados.
- Editar productos.
- Eliminar productos.
- Registrar precio y cantidad disponible.
- Activar o desactivar productos.

### Pedidos

Permite:

- Crear pedidos.
- Consultar pedidos.
- Asociar un cliente con un producto.
- Registrar la cantidad solicitada.
- Calcular el total del pedido.
- Actualizar el estado del pedido.
- Eliminar pedidos cancelados.

---

## Componentes reutilizables

El frontend cuenta con componentes reutilizables para evitar duplicación de código:

- `BaseButton.vue`: botón reutilizable.
- `BaseInput.vue`: campo de entrada reutilizable.
- `DataTable.vue`: tabla reutilizable para mostrar información.
- `AlertMessage.vue`: mensajes de información o error.

---

## Rutas principales

La aplicación cuenta con las siguientes rutas:

- `/dashboard`: página principal.
- `/clientes`: administración de clientes.
- `/productos`: administración de productos.
- `/pedidos`: administración de pedidos.

Las rutas inexistentes son redirigidas al Dashboard.

---

## API REST

El backend proporciona endpoints para administrar las principales entidades del sistema.

### Clientes

- `GET /api/clientes`
- `GET /api/clientes/<id>`
- `POST /api/clientes`
- `PUT /api/clientes/<id>`
- `DELETE /api/clientes/<id>`

### Productos

- `GET /api/productos`
- `GET /api/productos/<id>`
- `POST /api/productos`
- `PUT /api/productos/<id>`
- `DELETE /api/productos/<id>`

### Pedidos

- `GET /api/pedidos`
- `GET /api/pedidos/<id>`
- `POST /api/pedidos`
- `PUT /api/pedidos/<id>`
- `DELETE /api/pedidos/<id>`

---

## Validaciones

El sistema incorpora validaciones para evitar información incorrecta o incompleta.

Entre las validaciones implementadas se encuentran:

- Campos obligatorios.
- Validación de precios.
- Validación de cantidades.
- Verificación de existencia de clientes.
- Verificación de existencia de productos.
- Validación del stock disponible.
- Validación de los estados de los pedidos.
- Los pedidos solamente pueden eliminarse cuando se encuentran cancelados.

Las validaciones también se realizan en el backend para evitar depender únicamente de las validaciones del navegador.

---

## Pruebas

El backend incluye pruebas automatizadas utilizando `pytest`.

Para ejecutar las pruebas:

```powershell
cd backend
.venv\Scripts\Activate.ps1
python -m pytest
```

Las pruebas verifican principalmente el funcionamiento de las operaciones de la API.

---

## Seguridad y mantenimiento

Se consideran las siguientes prácticas:

- Las variables sensibles se almacenan en archivos `.env`.
- Los archivos `.env` no deben subirse al repositorio.
- Se proporciona un `.env.example` como referencia.
- Las consultas a la base de datos utilizan SQLAlchemy.
- Se realizan validaciones en el backend.
- Las migraciones permiten mantener controlada la estructura de la base de datos.
- Las dependencias del proyecto se registran en los archivos correspondientes.

---

## Arquitectura

La aplicación utiliza una arquitectura dividida entre frontend y backend.

El flujo principal de comunicación es:

```text
Usuario
   ↓
Frontend Vue 3
   ↓
Axios
   ↓
API REST Flask
   ↓
SQLAlchemy
   ↓
Base de datos SQLite
```

Esta separación permite mantener organizada la interfaz de usuario, la lógica del servidor y el acceso a los datos.

---