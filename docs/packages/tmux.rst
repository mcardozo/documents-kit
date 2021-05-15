Tmux
==================================================================

:sipsonis: Terminal multiplexer

Terminal multiplexer que permite habilitar múltiples sesiones,
ventanas y paneles para ser controladas mediante el mismo terminal.


Instalación
-------------------------------------------------------------------
Instalar mediante *apt*::

  $ sudo apt install tmux


Sesiones
-------------------------------------------------------------------
Iniciar::

  $ tmux

Listar sesiones::

  $ tmux ls

  shortcut: Ctrl + b, s

Unirse a una sesión::

  $ tmux a -t <nombre>

  shortcut: Ctrl + b, s

Agregar una nueva sesión::

  $ tmux new -s <nombre>

Renombrar una sesión::

  shortcut: Ctrl + b, $

Salir de una sesión sin cerrarla::

  shortcut: Ctrl + b, d

Cerrar sesión::

  $ tmux kill-session -t <nombre>



Ventanas
-------------------------------------------------------------------
Dividir la terminal en ventanas horizontales::

  shortcut: Ctrl + b, %

Dividir la terminal en ventanas verticales::

  shortcut: Ctrl + b, ""

Activar el modo scroll::

  Ctrl + b, :

  :set -g mouse on


Texto
-------------------------------------------------------------------
Copiar texto::

  Ctrl + b, [

  Ctrl + space

  Alt + w

  Ctrl + b, ]


Extras
-------------------------------------------------------------------
Mostrar reloj::

  Ctrl + b, t
