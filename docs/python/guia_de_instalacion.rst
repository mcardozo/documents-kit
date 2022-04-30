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

   $ wget https://www.python.org/ftp/python/3.9.10/Python-3.9.10.tgz

   $ tar xf Python-3.9.10.tgz

   $ cd Python-3.9.10

Instalación:

.. code-block:: bash

   $ sudo ./configure --enable-optimizations

   $ sudo make altinstall

Listo!

Gestionar multiples versiones
----------------------------------------------------------------------

Agregar python3.9 como predeterminado::

  $ sudo update-alternatives --config python

  $ sudo update-alternatives --install /usr/bin/python python /usr/local/bin/python3.9 1

  $ sudo update-alternatives --install /usr/bin/python python /usr/bin/python3.8 2

  $ sudo update-alternatives --list python

Pip
----------------------------------------------------------------------
Verifica instalación::

  $ python -m pip --version

Instalar::

  $ curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py

  $ sudo python get-pip.py

Actualizar::

  $ python -m pip install -U pip


 VirtualEnvWrapper
----------------------------------------------------------------------

Instalación::

  $ sudo pip install virtualenvwrapper

Agregar al archivo de configuración::

  source /usr/local/bin/virtualenvwrapper.sh

Problemas con virtualenv por ya estar instalado con apt::

  $ python3 -m pip uninstall virtualenv

  $ python3 -m pip install virtualenv
