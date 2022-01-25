youtube-dl
======================================================================

:sipsonis: Descargar videos de youtube.com u otras plataformas de video

`GitHub`_

.. _GitHub: https://github.com/rg3/youtube-dl

Instalación
-------------------------------------------------------------------
Instalar mediante *snap*::

  $ snap install youtube-dl

Descargar sonido en formato mp3::

  $ youtube-dl --extract-audio --audio-format mp3 <url>

Descargar video en un formato específico::

   $ youtube-dl --format 18 <url>

Tabla de códigos de formatos::

  37 - mp4        [1080x1920]
  46 - webm       [1080x1920]
  22 - mp4        [720x1280]
  45 - webm       [720x1280]
  35 - flv        [480x854]
  44 - webm       [480x854]
  34 - flv        [360x640]
  18 - mp4        [360x640]
  43 - webm       [360x640]
   5 - flv        [240x400]
  17 - mp4        [144x176]
