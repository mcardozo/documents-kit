MySQL
==================================================================

:sipsonis: Base de datos relacional MySQL

MySQL es un sistema de gestión de bases de datos relacional


Instalación
-------------------------------------------------------------------

Actualizar el índice de packages::

  $ sudo apt update

Instalar packages `mysql-server`::

  $ sudo apt install mysql-server


Comandos útiles
-------------------------------------------------------------------

Conexión
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Conectarse a la base de datos::

  $ mysql -h <host> -u <user> <database> -p

Backups
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Crear un backup::

  $ mysqldump -u <user> <db_name> > mibackup.sql

Restore
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Restaurar una base de datos::

  $ mysql -u <user> -<password> < <backup_file>.sql

Consultas
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Consultar lista de usuarios::

  mysql> select User from mysql.user;

Cambiar clave de acceso::

  mysql> ALTER USER 'mcardozo'@'localhost' IDENTIFIED BY 'admin';


Docker
-------------------------------------------------------------------

Crear un backup de la base de datos dockerizada::

  $ docker exec -it <container_db> mysqldump -u <user> -p <db_name> > <file_backup>.sql

Restaurar un backup a la base de datos::

  $ docker exec -it <container_db> mysql -u <user> -<password> < <backup_file>.sql
