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