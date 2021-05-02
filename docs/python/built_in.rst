Funciones built-in
======================================================================

:synopsis: El intérprete de Python tiene una serie de funciones y tipos incluidos en él que están siempre disponibles

La función dir
----------------------------------------------------------------------
``dir``: Nos dice todos los métodos que podemos utilizar dentro de un objeto.


La función hasattr
----------------------------------------------------------------------
Toma como argumento un objeto y el nombre de un atributo y retorna ``True`` si el objeto tiene el atributo

.. code-block:: python

   class Rectangulo:
       def __init__(self, b, h):
           self.b = b
           self.h = h

   rect = Rectangulo(10, 5)
   print(hasattr(rect, "b"))     # True
   print(hasattr(rect, "area"))  # False


La función help
----------------------------------------------------------------------
``help``: nos imprime en pantalla el docstrings o comentario de ayuda o instrucciones que posee la función.
Casi todas las funciones en Python las tienen.


La función map
----------------------------------------------------------------------
Ejecuta una función sobre cada uno de los elementos de un iterador. Retorna un lista
o tupla que son el resultado de esa operación.

.. code-block:: python

   def dup(n):
       return n * 2

   list(map(dup, [1, 2, 3, 4]))

Output:

.. code:: bash(code)

   >>> [2, 4, 6, 8]


La función range
----------------------------------------------------------------------
Retorna una sucesión de números enteros.
Cuando se le pasa un único argumento ``n``, la sucesión empieza desde el cero y culmina en ``n-1``.

.. code-block:: bash(code)

   >>> list(range(10))
   >>> [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

Si se especifican dos argumentos, el primero pasa a indicar el comienzo de la sucesión:

.. code-block:: bash(code)

   >>> list(range(1, 11))
   [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]


La función super
----------------------------------------------------------------------
La función ``super()`` permite invocar el método de una clase padre desde una clase hija

.. code-block:: python

   class ClassA:
       def message(self):
           print("Hola")

   class ClassB(ClassA):
       def message(self):
           super().message()
           print("mundo!")

   b = ClassB()
   b.message()


La función zip
----------------------------------------------------------------------
``zip`` toma como argumento dos o más objetos iterables(idealmente con la misma
cantidad de elementos) y retorna un nuevo iterable.

.. code-block:: python

   names = ['Morena', 'Bárbara']
   ages = [18, 25]
   list(zip(names, ages))


Output:

.. code:: bash(code)

   >>> [('Morena', 18), ('Bárbara', 25)]


Usando strings
----------------------------------------------------------------------

   - **upper**: convierte todo el string a mayúsculas
   - **lower**: convierte todo el string a minúsculas
   - **find**: encuentra el indice en donde existe un patrón que nosotros definimos
   - **startswith**: significa que empieza con algún patrón.
   - **endswith**: significa que termina con algún patrón
   - **capitalize**: coloca la primera letra en mayúscula y el resto en minúscula

``in`` y ``not in`` nos permite saber con cualquier secuencia si una subsecuencia o substrings se encuentra adentro de la secuencia mayor.
