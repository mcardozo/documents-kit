Zellij
==================================================================

:synopsis: Terminal multiplexer

Terminal multiplexer, alternativa a tmux, que permite manejar
sesiones, pestañas y paneles desde la misma terminal. Funciona por
*modos*: cada modo agrupa sus atajos y la barra inferior muestra los
que están disponibles en todo momento.


Instalación
-------------------------------------------------------------------
Descargar el binario precompilado desde GitHub y moverlo al *PATH*::

  $ wget https://github.com/zellij-org/zellij/releases/latest/download/zellij-x86_64-unknown-linux-musl.tar.gz
  $ tar -xvf zellij-x86_64-unknown-linux-musl.tar.gz
  $ chmod +x zellij
  $ sudo mv zellij /usr/local/bin/

Instalar mediante *cargo* (requiere Rust)::

  $ cargo install --locked zellij

Verificar la instalación::

  $ zellij --version


Modos
-------------------------------------------------------------------
Desde el modo normal se entra a cada modo con su atajo; ``Esc`` o
``Enter`` vuelven al modo normal::

  Ctrl + p    Paneles
  Ctrl + t    Pestañas
  Ctrl + n    Redimensionar
  Ctrl + h    Mover paneles
  Ctrl + s    Scroll y búsqueda
  Ctrl + o    Sesión
  Ctrl + g    Bloquear (desactiva los atajos de zellij)
  Ctrl + q    Salir

Bloquear los atajos es útil cuando chocan con los de otro programa
(por ejemplo Vim o Emacs)::

  shortcut: Ctrl + g


Sesiones
-------------------------------------------------------------------
Iniciar::

  $ zellij

Crear una sesión con nombre::

  $ zellij -s <nombre>

Listar sesiones::

  $ zellij ls

Unirse a una sesión::

  $ zellij a <nombre>

Unirse a una sesión o crearla si no existe::

  $ zellij a -c <nombre>

Administrador de sesiones (listar, cambiar y renombrar)::

  shortcut: Ctrl + o, w

Renombrar la sesión actual::

  $ zellij action rename-session <nombre>

Salir de una sesión sin cerrarla::

  shortcut: Ctrl + o, d

Cerrar una sesión::

  $ zellij kill-session <nombre>

Cerrar todas las sesiones::

  $ zellij kill-all-sessions

Eliminar una sesión cerrada (para que no pueda recuperarse)::

  $ zellij delete-session <nombre>


Pestañas
-------------------------------------------------------------------
Crear pestaña::

  Ctrl + t, n

Pestaña siguiente / anterior::

  Ctrl + t, l
  Ctrl + t, h

Ir a número de pestaña::

  Ctrl + t, <num>

Alternar con la última pestaña usada::

  Ctrl + t, Tab

Renombrar pestaña::

  Ctrl + t, r

Cerrar pestaña::

  Ctrl + t, x

Enviar lo que se escribe a todos los paneles de la pestaña::

  Ctrl + t, s


Paneles
-------------------------------------------------------------------
Nuevo panel (sin cambiar de modo)::

  Alt + n

Dividir la terminal en paneles horizontales (nuevo panel abajo)::

  Ctrl + p, d

Dividir la terminal en paneles verticales (nuevo panel a la derecha)::

  Ctrl + p, r

Moverse entre paneles (y pestañas en los bordes)::

  Alt + ←/↓/↑/→

Panel en pantalla completa::

  Ctrl + p, f

Mostrar u ocultar los paneles flotantes::

  Alt + f

Renombrar panel::

  Ctrl + p, c

Cerrar panel::

  Ctrl + p, x

Agrandar o achicar el panel actual::

  Alt + +
  Alt + -

Ejecutar un comando en un panel nuevo (``-f`` para que sea flotante)::

  $ zellij run -- htop
  $ zellij run -f -- htop


Texto
-------------------------------------------------------------------
Activar el modo scroll (moverse con las flechas o ``j``/``k``)::

  Ctrl + s

Buscar en el historial (``n`` siguiente, ``p`` anterior)::

  Ctrl + s, s

Abrir el historial de la terminal en el editor (``$EDITOR``)::

  Ctrl + s, e

Copiar texto: seleccionar con el mouse; se copia al soltar el botón.


Configuración
-------------------------------------------------------------------
Generar el archivo de configuración con los valores por defecto::

  $ mkdir -p ~/.config/zellij
  $ zellij setup --dump-config > ~/.config/zellij/config.kdl

Verificar la configuración::

  $ zellij setup --check

Iniciar con un layout compacto (una sola barra)::

  $ zellij --layout compact
