Django
=====================================================================
:synopsis: Comando útiles para django


Información
----------------------------------------------------------------------
Mostrar la versión de django instalada::

   $ python -m django --version


Mostrar las librerias instaladas::

   $ pip freeze


Correr la terminal del proyecto::

   $ python manage.py shell

.. note::
   **manage.py**: es el empaquetador de django


Proyecto
----------------------------------------------------------------------
Creando proyecto:

.. code-block:: bash

   $ django-admin startproject <proyect-name>

   $ django-admin startproject <proyect-name> .

.. note::
   Para que una carpeta sea reconocida como un paquete debe contener el archivo __init__.py

Crear una app:

.. code-block:: bash

   $ django-admin startapp <package-name>

   $ django-admin startapp <package-name> <directory>


Modelos
----------------------------------------------------------------------
`Documentación <https://docs.djangoproject.com/en/3.2/topics/db/models/#fields>`_

Actualizar nuevos modelos:

.. code-block:: bash

   $ python manage.py makemigrations <package-name>

   $ python manage.py migrate <package-name>


Crear la migraciones::

  $ python manage.py migrate

.. note:: Django crea 10 tablas por default

Crear modelos a partir de la base de datos::

  python manage.py inspectdb > models.py

Administrador
----------------------------------------------------------------------
Crear superusuario::

    $ python manage.py createsuperuser

.. note:: Registar modelos en el archivo `admin.py` de cada paquete


Servidor
----------------------------------------------------------------------
Ejecutar el servidor de desarrollo::

    $ python manage.py runserver

Especificar el puerto::

    $ python manage.py runserver 8080

Escuchar todas las IPs públicas y especificar un puerto::

    $ python manage.py runserver 0.0.0.0:8000


Datos
----------------------------------------------------------------------
Comando para extraer datos:

.. code-block:: bash

   $ python manage.py dumpdata --indent 4 > output.json

   $ python manage.py dumpdata app.model --indent 4 > output.json

   $ python manage.py dumpdata --exclude=admin.logentry --exclude=auth.permission --exclude=contenttypes --exclude=sessions --indent 4 > output.json

Comando para importar datos::

  $ python manage.py loaddata output.json

Ignorar los campos y modelos que pueden haberse eliminado desde que se generó
originalmente el fixture::

    --ignorenonexistent, -i

Excluyendo apps::

    --exclude

Especificando app::

    --app


Reseteando migraciones
----------------------------------------------------------------------
Eliminar manualmente las migraciones::

  $ rm -r path/to/app/migrations/*

Eliminar de la base de datos la tablas relacionadas a nuestra *app*::

Crear migraciones::

  $ python manage.py makemigrations <app>

Limpiar el historial de migraciones::

  $ python manage.py migrate --fake <app> zero

Mostrar el estado de las migraciones::

  $ python manage.py showmigrations

Aplicar las migraciones a la base de datos::

  $ python manage.py migrate

Mostrar el estado de las migraciones::

  $ python manage.py showmigrations


Traducciones
----------------------------------------------------------------------

Configurar el idioma::

   LANGUAGE_CODE = "es"
   LANGUAGE_COOKIE_NAME = 'es'
   LANGUAGES = (
      ('es', _('Spanish')),
      ('en', _('English'))
   )

Extraer textos para traduccir::

  python manage.py makemessages --all

Compilar textos::

  django python manage.py compilemessages

.. note:: Luego de compilar los mensajes es necesario reiniciar el servidor


Corriendo comandos en docker
----------------------------------------------------------------------
Correr el servicio de django aparte::

  $ docker-compose stop django && docker-compose run --rm --service-ports django

Cargar datos::

  $ docker-compose run --rm django python manage.py loaddata fixtures/data.json

Correr shell plus::

  $ docker-compose run --rm django python manage.py shell_plus

Extrar datos::

  $ docker-compose run --rm django python manage.py dumpdata --exclude=admin.logentry --exclude=auth.permission --exclude=contenttypes --exclude=sessions --indent 4 > backup.json

Acceder a una base mysql::

  $ docker exec -it <container> mysql -u <user> -h <host> -p <dbname>

Acceder a una base postgresql::

  $ docker exec -it <container> psql <dbname> -U <username>

Acceder a base de datos y extrar un backup psql::

  $ echo "deb http://apt.postgresql.org/pub/repos/apt/ `lsb_release -cs`-pgdg main" |sudo tee  /etc/apt/sources.list.d/pgdg.list

  $ sudo apt update

  $ sudo apt install postgresql-client-12

  $ pg_dump -h=host -p=port -U=postgres -d=dbname -F c -f backup.sql
