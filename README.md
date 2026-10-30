# Blog Web — Proyecto Final

Blog web desarrollado con Django: publicaciones con imagen, registro/login/logout, perfil de usuario con avatar, rutas protegidas y buscador de posts.

## Tecnologías utilizadas

- Python 3.10 o superior
- Django 5.2
- Pillow (manejo de imágenes)
- python-decouple (variables de entorno)
- SQLite (base de datos de desarrollo)
- HTML / CSS

## Funcionalidades principales

- CRUD completo de posts (listar, ver detalle, crear, editar, eliminar) desde la interfaz web.
- Carga y visualización de imagen por post; el template no se rompe si el post no tiene imagen.
- Registro, login y logout de usuarios.
- Perfil de usuario editable, con avatar opcional.
- El sistema distingue entre usuario anónimo y autenticado (la barra de navegación cambia según la sesión).
- Rutas protegidas con `@login_required`: crear, editar y eliminar posts, y ver/editar el perfil.
- Solo el autor de un post puede editarlo o eliminarlo.
- Buscador de posts por título o contenido, con aviso cuando no hay resultados.

## Instalación y ejecución local

1. Clonar el repositorio y entrar a la carpeta del proyecto:
   ```bash
   git clone <URL-DEL-REPOSITORIO>
   cd <nombre-de-la-carpeta>
   ```

2. Crear y activar un entorno virtual:
   ```bash
   python -m venv venv
   source venv/bin/activate      # En Windows: venv\Scripts\activate
   ```

3. Instalar las dependencias:
   ```bash
   pip install -r requirements.txt
   ```

4. (Opcional) Configurar variables de entorno: copiar `.env.example` como `.env` y completar los valores. Si se omite este paso, el proyecto arranca con valores de desarrollo por defecto.
   ```bash
   cp .env.example .env          # En Windows: copy .env.example .env
   ```

5. Crear la base de datos aplicando las migraciones:
   ```bash
   python manage.py migrate
   ```

6. (Opcional) Crear un superusuario para entrar al panel de administración (`/admin/`):
   ```bash
   python manage.py createsuperuser
   ```

7. Iniciar el servidor:
   ```bash
   python manage.py runserver
   ```

8. Abrir `http://127.0.0.1:8000/` en el navegador.

## Probar el proyecto desde cero

El repositorio **no incluye** `db.sqlite3` ni la carpeta `media/` (están en `.gitignore`), por lo que al clonarlo el blog arranca vacío. Para probarlo:

1. Entrar a **Registrarme** y crear una cuenta; luego **Iniciar sesión**.
2. Usar **Nuevo post** para crear publicaciones, con y sin imagen.
3. Desde el detalle de un post (siendo su autor) se puede **Editar** o **Eliminar**.
4. Cerrar sesión y verificar que `/nuevo/` y `/usuarios/perfil/` redirigen al login.
5. Probar el buscador en **Buscar**.

Las imágenes subidas se guardan en `media/`, que se crea automáticamente al subir la primera.

## Estructura del proyecto

```
blog_config/   configuración del proyecto (settings, urls)
posts/         app de publicaciones (modelo, vistas, formularios, templates)
usuarios/      app de usuarios (registro, perfil, templates de login)
templates/     template base
static/        archivos estáticos (CSS)
```

## Autor

**[Leandro Gómez]** — Proyecto Final Diplomatura Python — CoderHouse.
