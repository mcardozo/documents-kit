Mantenimiento del montaje de ``/home``
=====================================================================

Este procedimiento describe cómo desmontar temporalmente el directorio
``/home`` para realizar un chequeo del sistema de archivos y posteriormente
volver a montarlo. Además, se incluyen verificaciones adicionales para
asegurarse de que el volumen se encuentra en buen estado.

Pasos principales
----------------------------------------------------------------------

Desmontar ``/home`` para poder chequearlo::

   cd /
   sudo umount /home

Chequear y reparar el sistema de archivos de ``/home``::

   sudo e2fsck -f /dev/sda1

Montar ``/home`` desde ``fstab``::

   sudo mount /home

Reiniciar el gestor gráfico (SDDM)::

   sudo systemctl restart sddm

Verificaciones complementarias
----------------------------------------------------------------------

Verificar el montaje actual de ``/home``::

   findmnt /home

Consultar el estado del montaje de ``/home`` en este arranque::

   systemctl status home.mount

Confirmar que el UUID de ``/dev/sda1`` coincide con la entrada en ``fstab``::

   sudo blkid /dev/sda1

Revisar el estado SMART del disco::

   sudo smartctl -H /dev/sda

Forzar un chequeo ``ext4`` ocasional::

   sudo tune2fs -c 30 -i 6m /dev/sda1

