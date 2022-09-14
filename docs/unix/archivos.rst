Comandos Unix
=====================================================================
:synopsis: Comando útiles de unix


Archivos
----------------------------------------------------------------------


Comando útiles
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Ver el archivo en tiempo real

.. code-block:: bash

   $ tail -f name-file.txt


Crear un link simbolico a un archivo:

.. code-block:: bash

   $ ln -s /path/to/file file_link

Remplaza una cadena en un archivo con sed

.. code-block:: bash

   $ sed -i 's/old_name/new_name/g' file.txt


Archivos ejecutables
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Darle permisos a un archivo para que sea ejecutable:

.. code-block:: bash

   $ chmod a+x <script-name>


Copia de archivos a y desde servidores remotos
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Copiar archivos de un servidor remoto a un servidor local:

.. code-block:: bash

   $ sudo scp remote_user@remote_host:/path/to/remote/file /path/to/local/file

Copiar archivos de un servidor local a un servidor remoto:

.. code-block:: bash

  $ scp /path/to/local/file remote_user@remote_host:/path/to/remote/file

Copiar archivos/carpeta de un servidor remoto a un servidor local con archivo .pem de clave privada:

.. code-block:: bash

  $ sudo scp -i <file>.pem remote_user@remote_host:/path/to/remote/file /path/to/local/file

  $ sudo scp -i <file>.pem -r remote_user@remote_host:/path/to/remote/folder /path/to/local/folder

Copiar archivos de un servidor local a un servidor remoto con archivo .pem de clave privada:

.. code-block:: bash

  $ sudo scp -i <file>.pem /path/to/local/file remote_user@remote_host:/path/to/remote/file
