=====================================================================
Pantalla congelada
=====================================================================

Este procedimiento describe cómo recuperar el entorno gráfico cuando la
pantalla se congela, reiniciando el gestor de pantalla (*display manager*)
sin necesidad de reiniciar el equipo.

.. warning::
   Reiniciar el *display manager* cierra la sesión gráfica: se pierde el
   trabajo sin guardar de las aplicaciones abiertas.


Pasos principales
----------------------------------------------------------------------

Si la pantalla no responde, cambiar a una consola de texto (TTY) e iniciar
sesión con el usuario::

   Ctrl + Alt + F3

Nota: también sirven F2 a F6.

Reiniciar el gestor de pantalla::

   sudo systemctl restart display-manager

Si no vuelve automáticamente al entorno gráfico, cambiar a la TTY de la
sesión gráfica::

   Ctrl + Alt + F1

Nota: según la distribución puede ser F1 o F7.
