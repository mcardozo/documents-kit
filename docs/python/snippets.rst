Snippets
======================================================================

:synopsis: Snippets útiles


Funciones útiles
----------------------------------------------------------------------

Tomar el tiempo de una función

.. code-block:: python

   import time
   start_time = time.time()
   # something
   print("--- %.2f seconds ---" % (time.time() - start_time))
