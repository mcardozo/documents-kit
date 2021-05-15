Guía de instalación
=====================================================================

:synopsis: Guía de instalación de python 3.8.9

Python 3.8.9
----------------------------------------------------------------------

Actualizar paquetes e instalar dependecias:

.. code-block:: bash

   $ sudo apt install build-essential libssl-dev zlib1g-dev

   $ sudo apt install libffi-dev libbz2-dev libreadline-dev libsqlite3-dev


Descargar los archivos binarios:

.. code-block:: bash

   $ wget https://www.python.org/ftp/python/3.8.9/Python-3.8.9.tar.xz

   $ tar xf Python-3.8.9.tgz

   $ cd Python-3.8.9

Instalación:

.. note::
   Los siguientes comandos deben ejecutarse como superusuario

.. code-block:: bash

   # ./configure --enable-optimizations

   # make altinstall

Listo!


Pip
----------------------------------------------------------------------
Verifica instalación::

  $ python -m pip --version

Instalar::

  $ curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py

  $ python get-pip.py

Actualizar::

  $ python -m pip install -U pip
