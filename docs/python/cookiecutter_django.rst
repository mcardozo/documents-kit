Cookiecutter Django
=====================================================================

:synopsis: Una utilidad de línea de comandos para crear un proyecto de paquete de Python a partir
	   de una plantilla de proyecto de paquete de Python.


Comando útiles
----------------------------------------------------------------------

Backup
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Crear un backup::

   $ docker-compose -f <file>.yml exec postgres backup

Listar backups::

   $ docker-compose -f <file>.yml exec postgres backups

Copiar backup al entorno local::

   $ docker cp <container>:/backups/backup_2022_12_18T18_00_00.sql.gz $PWD


Restore
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Pasos para restaurar una base de datos.

Copiar el archivo backup obtenido con el comando de `backup` al contenedor PostgreSQL::

  $ docker cp backup_2022_12_18T18_00_00.sql.gz <container_db>:/backups/

Restaurar la backup::

  $ docker-compose -f <file>.yml exec postgres restore backup_2022_12_18T18_00_00.sql.gz
