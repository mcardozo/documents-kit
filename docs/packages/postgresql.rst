PostgreSQL
==================================================================

:sipsonis: Base de datos PostgreSQL

PostgreSQL es un sistema de gestión de bases de datos objeto-relacional,
distribuido bajo licencia BSD y con su código fuente disponible libremente.


Instalación
-------------------------------------------------------------------
Agregar repositorio::

  $ sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'

Agregar clave pública del repositorio::

  $ wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -

Actualizar repositorios e instalar PostgreSQL 9.6::

  $ sudo apt-get update

  $ sudo apt-get -y install postgresql

Verificar la instalación y levantar el servicio::

  $ psql --version

  $ sudo service postgresql start

Cambiar la contraseña por defecto del usuario postgres::

  # su - postgres

  $ psql

  postgres=# ALTER ROLE postgres WITH PASSWORD 'postgres';

  postgres=# \q

Habilitar el acceso por contraseña. Abrir el archivo pg_hba.conf::

  $ sudo vi /etc/postgresql/9.6/main/pg_hba.conf

Cambiar el método de acceso::

  local all postgres peer

  local all all peer

por::

  local all postgres md5

  local all all md5

Reiniciar el servicio::

  $ sudo service postgresql restart


Exportación e importación
-------------------------------------------------------------------
Exportar a un archivo con formato CSV:

.. code:: bash(code)

   COPY (
       SELECT name FROM stores WHERE city = 'Buenos Aires'
   ) TO '/path/to/csv/stores_dump.csv' WITH CSV HEADER DELIMITER ';';

Importar desde un archivo con formato CSV::

  COPY cms_title FROM '/path/to/csv/stores_dump.csv' DELIMITER ';' CSV;


Backups
-------------------------------------------------------------------
*pg_dump* es una herramienta de línea de comandos que permite hacer respaldos
de bases de datos de servidor PostgreSQL.


Crear un backup formato binario::

  $ pg_dump -h <host> -U <usuario> -d <db> -p <port> -F c -f output.sql

Crear un backup formato de texto plano, este formato luego permite cambiar el nombre de los esquema::

  $ pg_dump -h <host> -U <usuario> -d <db> -p <puerto> -F p -f output.sql

Crear un backup de una tabla en formato binario::

  $ pg_dump -h <host> -U <usuario> -t <esquema>.<tabla> <db> -F c -f output.sql

Crear un backup de un schema en formato custom::

  $ pg_dump -h <host> -U <usuario> --schema <esquema> <db> -F c -f output.sql

Extraer los datos de una tabla en formato plano::

  $ pg_dump -h <host> -U <usuario> -d <db> -t <tabla> -F p -f <file>.sql --data-only


Restore
-------------------------------------------------------------------
Para restaurar el backup en formato custom o binario usar la herramienta *pg_restore*::

  $ pg_restore -h <host> -U <usuario> -d <db> : output.sql

Para restaurar el backup en formato plano usar la herramienta *psql*::

  $ psql -h <host> -U <usuario> -d <db> -f output.sql


Sentencias utiles
-------------------------------------------------------------------
Directorio donde se guardan las base de datos::

  SHOW data_directory;

Por cada base de datos se crea un directorio con nombre de "id", para conocer el id de cada base de datos ejecutar::

  SELECT datname, oid FROM pg_database;

Reemplazar caracteres inválidos:

.. code:: bash(code)

   update tabla set campo = replace(campo, 'Ã±', 'ñ');
   update tabla set campo = replace(campo, 'Ã¡', 'á');
   update tabla set campo = replace(campo, 'Ã³', 'ó');
   update tabla set campo = replace(campo, 'Ã', 'í');
   update tabla set campo = replace(campo, 'íº', 'ú');
   update tabla set campo = replace(campo, 'í©', 'é');
   update tabla set campo = replace(campo, 'Ãº', 'ú');
   update tabla set campo = replace(campo, 'í‘', 'Ñ');

Agregar pkey::

  ALTER TABLE <table_name> ADD COLUMN id SERIAL PRIMARY KEY;

Mantenimiento de tablas::

  ANALYZE optimiza cuando usar o no índices. Guarda y actualiza estadísticas de lso datos

Examinar Query::

  EXPLAIN ANALYZE SELECT * FROM <table_name>;

Optimización::

  ANALYZE <table_name>

Mantenimiento rutinario de tablas::

  VACUUM ANALYZE <table_name>;

Crear tabla geométrica con índice::

  CREATE INDEX <tabla_name>_geom_idx
  ON <table_name>
  USING GIST (geom);
