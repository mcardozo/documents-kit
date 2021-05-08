pg_dump
==================================================================

:sipsonis: Extrae un base de datos en un archivo

*pg_dump* es una herramienta de línea de comandos que permite hacer respaldos
de bases de datos de servidor PostgreSQL.


Backups
-------------------------------------------------------------------
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
