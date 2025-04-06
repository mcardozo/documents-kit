apt (advanced package tool) & apt-get
=====================================================================
:synopsis: herramienta de línea de comandos que permite instalar, actualizar, eliminar y administrar paquetes en sistemas


apt
----------------------------------------------------------------------


Comandos útiles
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Actualiza la lista de paquetes disponibles

.. code-block:: bash

   $ sudo apt update


Actualiza el sistema instalando/actualizando paquetes

.. code-block:: bash

   $ sudo apt upgrade

Nota: similiar a `sudo aptitude safe-upgrade` que repara paquetes rotos


Actualiza los paquetes.Soluciona paquetes retenidos

.. code-block:: bash

   $ sudo apt full-upgrade


Actualiza el sistema instalando/actualizando/eliminando paquetes. Soluciona conflitos

.. code-block:: bash

   $ sudo apt dist-upgrade


apt-get
----------------------------------------------------------------------


Comandos útiles
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Resoluc


Chequea el estados de los paquetes

.. code-block:: bash

   $ sudo apt-get check


Eliminar los paquetes de caché

.. code-block:: bash

   $ sudo apt-get clean


Elimina de caché los paquetes de las versiones anteriores

.. code-block:: bash

   $ sudo apt-get autoclean


Borra paquetes huérfanos o dependencias ya instaladas

.. code-block:: bash

   $ sudo apt-get autoremove


Remover Aplicación y quitar archivos relacionados

.. code-block:: bash

   $ sudo apt --purge remove paquete
