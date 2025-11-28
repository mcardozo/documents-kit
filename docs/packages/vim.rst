Vim — Guía práctica definitiva
===============================

Lista compacta, ordenada por tareas. Incluye lo esencial y un bloque de avanzados con lo más
rescatable de tu doc original, ya depurado.

1) Guardar y salir
------------------
::

  :w            " Guardar
  :q            " Salir (falla si hay cambios)
  :wq / :x      " Guardar y salir
  :q!           " Salir descartando cambios
  ZZ / ZQ       " Guardar+salir / salir sin guardar

2) Modos
--------
::

  i  a  o       " Insert (antes / después / nueva línea abajo)
  I  A  O       " Insert al inicio / al final / nueva línea arriba
  <Esc>         " Volver a Normal

Sugerencia: usa ``gi`` para volver a insertar donde editaste por última vez.

3) Movimiento
-------------
::

  h j k l          " Izq / Abajo / Arriba / Der
  w  b  e          " Saltar por palabras (inicio / atrás / fin)
  0  ^  $          " Inicio / primer no-blanco / fin de línea
  gg / G           " Inicio / fin del archivo
  H  M  L          " Tope / medio / pie de pantalla
  {  }             " Párrafo anterior / siguiente
  %                " Salto a paréntesis/llave/corchete pareja
  Ctrl-d / Ctrl-u  " Media página abajo / arriba
  Ctrl-f / Ctrl-b  " Página completa abajo / arriba

4) Búsqueda y navegación de resultados
--------------------------------------
::

  /texto        " Buscar hacia adelante
  ?texto        " Buscar hacia atrás
  n / N         " Siguiente / anterior coincidencia
  * / #         " Buscar palabra bajo cursor (adelante / atrás)

Tip: ``:set hlsearch incsearch`` para resaltar y buscar incremental.

5) Edición (operador + movimiento)
----------------------------------
::

  x / X         " Borrar char (derecha / izq)
  d{mov}        " Delete (ej: dw, d$, dj)
  c{mov}        " Change (borra y entra en Insert)
  y{mov}        " Yank (copiar)
  p / P         " Pegar después / antes
  .             " Repetir última acción
  u / Ctrl-r    " Deshacer / Rehacer
  J             " Unir con línea siguiente
  ~             " Toggle may/min del char
  r / R         " Reemplazar un letra / Reemplazar varias letras

5.1) Text objects (turbo para d/y/c)
------------------------------------
::

  ciw / diw     " Cambiar / borrar palabra “in word”
  ci" / di"     " Dentro de comillas
  ci( / di(     " Dentro de paréntesis (funciona con { [ < ' ")
  dap / dip     " Borrar un párrafo (around / in paragraph)

Tip: ``vi)`` selecciona dentro de paréntesis; ``va)`` incluye paréntesis.

6) Sustituciones
----------------
::

  :s/viejo/nuevo/g             " En la línea actual
  :%s/viejo/nuevo/gc           " En todo el archivo, confirmando
  :'<,'>s/viejo/nuevo/g        " En selección visual

Pro: ``:%s/\<<C-r><C-w>\>/nuevo/gc`` reemplaza la palabra bajo el cursor en todo el archivo.

7) Visual mode
--------------
::

  v / V / Ctrl-v   " Carácteres / línea / bloque
  gv               " Re-seleccionar la última selección

8) Buffers, ventanas y pestañas
-------------------------------
::

  :ls            " Listar buffers
  :bn / :bp      " Buffer siguiente / previo
  :b#            " Volver al buffer anterior
  :bd            " Cerrar buffer actual

::

  :split / :vsplit   " Split horizontal / vertical
  Ctrl-w h/j/k/l     " Moverse entre ventanas
  Ctrl-w =           " Igualar tamaños
  Ctrl-w q           " Cerrar ventana

::

  :tabnew            " Nueva pestaña
  gt / gT            " Siguiente / anterior pestaña

Sugerencia: ``set hidden`` para cambiar de buffer sin guardar.

9) Archivos y navegación
------------------------
::

  :e ruta           " Abrir archivo
  :edit .           " Abrir navegador en cwd (netrw)
  :Ex / :Lex        " Netrw en ventana actual / lateral

Tip: ``gf`` abre el archivo bajo el cursor si es ruta válida.

10) Registros y portapapeles
----------------------------
::

  "xy / "xp         " Copiar / pegar usando registro x
  "+y / "+p         " Portapapeles del sistema
  "_d               " Borrar sin afectar el registro "" (black hole)

11) Sangría y formato
---------------------
::

  >> / << / ==      " Indentar der / izq / autoindentar línea
  =%                " Reindentar bloque entre pares
  gg=G              " Autoindentar todo el archivo

Tip: ``:set expandtab shiftwidth=2 tabstop=2`` para espacios en vez de tabs.

12) Macros
----------
::

  q{r} … q          " Grabar macro en registro {r}
  @{r} / @@         " Ejecutar macro / repetir la última

13) Hechizo (spell)
-------------------
::

  :set spell spelllang=es,en   " Activar corrector ES/EN
  ]s / [s                      " Siguiente / anterior error
  zg / zw                      " Añadir / marcar palabra incorrecta

Extra: ``z=`` sugiere correcciones.

14) Quickfix y grep
-------------------
::

  :vimgrep /pat/ **/*.py      " Grep recursivo
  :copen / :cnext / :cprev    " Abrir lista / siguiente / anterior

Alternativa rápida: ``:grep -R "pat" .`` (requiere grep/ag/rg configurado).

15) Recetas útiles
------------------
- Cambiar comillas con confirmación: ``:%s/"\(.\{-}\)"/'\1'/gc``
- Mantener solo selección: seleccionar en Visual y ``:keepjumps '<,'>write! tmp && %d | 0r tmp | bwipe! tmp``
- Repetir una acción N veces: ``10dd``, ``5>>``, ``3p``.
- Quitar espacios finales: ``:%s/\s\+$//``
