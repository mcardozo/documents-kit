Guía de instalación
=====================================================================

:synopsis: Guía de instalación de Python 3.12.x en Linux (Ubuntu/Kubuntu 24.04) y uso de entornos virtuales con ``venv``

Python 3.12.x (desde código fuente)
----------------------------------------------------------------------
Requisitos de compilación (Ubuntu/Kubuntu 24.04)::

  sudo apt update
  sudo apt install -y \
    build-essential \
    libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev \
    libncursesw5-dev tk-dev uuid-dev libffi-dev \
    liblzma-dev xz-utils libxml2-dev libxmlsec1-dev wget curl

Descargar y compilar (ajusta la versión estable de 3.12.x si corresponde)::

  PYVER=3.12.6
  cd /tmp
  wget https://www.python.org/ftp/python/${PYVER}/Python-${PYVER}.tgz
  tar xf Python-${PYVER}.tgz
  cd Python-${PYVER}

Configurar y compilar con optimizaciones (esto instala en ``/usr/local`` sin pisar el Python del sistema)::

  ./configure --enable-optimizations --with-lto --prefix=/usr/local
  make -j"$(nproc)"
  sudo make altinstall

Verifica la instalación::

  /usr/local/bin/python3.12 --version
  /usr/local/bin/python3.12 -m pip --version


Gestionar múltiples versiones (sin alterar el Python del sistema)
----------------------------------------------------------------------
Recomendación: invocar explícitamente ``/usr/local/bin/python3.12`` y ``pip3.12`` para evitar conflictos con el Python provisto por la distribución.

Opcionalmente, crea alias en tu shell (``~/.bashrc`` o ``~/.zshrc``)::

  echo 'alias py312="/usr/local/bin/python3.12"' >> ~/.bashrc
  echo 'alias pip312="/usr/local/bin/pip3.12"'   >> ~/.bashrc
  # luego recarga tu shell:
  source ~/.bashrc


Pip
----------------------------------------------------------------------
Python 3.12 incluye ``pip``. Si lo necesitas, asegúrate de tenerlo al día::

  /usr/local/bin/python3.12 -m ensurepip --upgrade
  /usr/local/bin/python3.12 -m pip install --upgrade pip setuptools wheel


Entornos virtuales con venv (recomendado)
----------------------------------------------------------------------
A partir de Python 3.3, la forma estándar de crear entornos virtuales es con ``venv`` (no se usa ``virtualenvwrapper``).

### Crear un entorno local en el proyecto

Desde la carpeta de tu proyecto::

  # Crea el entorno .venv usando Python 3.12
  /usr/local/bin/python3.12 -m venv .venv

  # Activa el entorno (bash/zsh)
  source .venv/bin/activate

  # Verifica que estás dentro del entorno
  python -V
  python -m pip -V

### Comandos útiles en el día a día

Instalar dependencias::

  python -m pip install -r requirements.txt

Guardar dependencias actuales::

  python -m pip freeze > requirements.txt

Actualizar ``pip`` y herramientas básicas dentro del entorno::

  python -m pip install --upgrade pip setuptools wheel

Instalar un paquete puntual::

  python -m pip install nombre-paquete

Salir/desactivar el entorno virtual::

  deactivate

Eliminar el entorno (cuando necesites recrearlo)::

  deactivate  # si está activo
  rm -rf .venv

### Recrear el entorno desde cero (patrón recomendado)

Cuando cambies de versión de Python o sospeches de conflictos, recrea el entorno limpio::

  rm -rf .venv
  /usr/local/bin/python3.12 -m venv .venv
  source .venv/bin/activate
  python -m pip install --upgrade pip setuptools wheel
  python -m pip install -r requirements.txt


Solución de problemas
----------------------------------------------------------------------
* ``_ssl`` o ``lzma`` no disponibles al compilar: asegúrate de tener instaladas las dev libs: ``libssl-dev`` y ``liblzma-dev`` antes de compilar.
* Evita cambiar el ``python``/``python3`` del sistema: usa únicamente ``/usr/local/bin/python3.12`` (o alias) para tu trabajo diario.
* Si ``pip`` no aparece dentro del entorno: ejecuta ``python -m ensurepip --upgrade`` y luego ``python -m pip install --upgrade pip``.

Listo!
