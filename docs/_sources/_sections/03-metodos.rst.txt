=======
Métodos
=======

Las APIs están conformadas por conjuntos de métodos que exponen los datos.

A continuación se detallan ejemplos generales. Para mayot especificidad, sugerimos revisar la documentación de cada API.


Llamadas a un método
--------------------

::

  GET   {url}/nombre-de-api/v1/metodo.json?auth_key={AUTH KEY}



Por tanto, la estructura de la ruta de la solicitud es:
``nombre-de-api`` es el nombre de la API.
``v1`` es la versión de la API.
``metodo`` es el método solicitado.
``auth_key=TU_AUTH_KEY`` es la clave que necesitarás para cada solicitud.


Estructura JSON de salida
-------------------------

El resultado es un JSON. Su formato puede variar entre métodos. A modo de ejemplo, suele utilizarse el siguiente formato:


.. code-block:: json

  {
   "headers":[
      "Fecha",
      "Valor"
   ],
   "data":[
      [
         "02-01-1984",
         "87.54"
      ],
      [
         "03-01-1984",
         "87.62"
      ],
      [
         "04-01-1984",
         "87.63"
      ]
   ],
   "cols":2,
   "rows":4,
   "length":12653,
   "timestamp":1534922262659
  }

| ``headers`` indica los atributos de los valores.
| ``data`` expone los valores correspondientes a los atributos.
| ``cols`` la cantidad de columnas de datos
| ``rows`` la cantidad de filas incluidas en la respuesta.
| ``lengt`` la cantidad de filas totales del método
| ``timestamp`` contiene el tiempo POSIX de cuando fue actualizada la fuente de datos de forma exitosa por última vez.



Consultar un método con parámetros
----------------------------------

Un método puede contener parámetros.

Por ejemplo, el siguiente método contiene el parámetro 'anio' y el parámetro 'mes':
::

  GET   {url}/indicadores/v1/metodo.json?auth_key={AUTH KEY}&anio=2010&mes=01


De manera que para consultar métodos con parámetros, debe enviarse el nombre del parámentro y un valor válido. En caso que los valores no sean válidos, la respuesta será en base a los valores por defecto.



Filtrar los resultados de una vista
------------------------------------

La API de SuperSalud Desarrolladores permite a sus usuarios filtrar los resultados obtenidos durante la solicitud de un método utilizando la siguiente sintaxis:

::

  GET   {url}/indicadores/v1/metodo.json?auth_key={AUTH KEY}&filter0=column2[>]190&filter1=column0[==]Chile&where=(filter and filter1)


Esta solicitud retorna todos los datos que sean mayores a 190 en la columna 5 y sean iguales a la palabra “Chile” en la columna 0.

Los filtros pueden ir desde 0 a N (filter0, filter1...filterN) y tienen la siguiente sintaxis::

	operando0 | operador lógico | operando1

Los operando0 pueden ser rownum (número de fila) o columnN (columna N, donde N es un entero que va desde 0 a N). El operando1 por lo general es una cadena de texto, número o fecha.

Los operadores lógicos pueden ser::

	[==], [>], [<], [!=], [contains], [>=], [<=]

Los corchetes [] deben ser incluidos. Los operandos son sensibles a mayúsculas si el contenido es una cadena de texto. En el caso del operador lógico [contains], el orden de los operandos debe invertirse.

La operación where tiene una expresión lógica para concatenar filtros de tipo AND u OR. En este caso, se utilizaría (filter0 and filter1). Las expresiones and y or sirven para diferenciar la relación entre los filtros y pueden concatenarse tanto como fuera necesario para cumplir una cierta condicion por ejemplo::

	(filter0 and filter1) or filter2.



Ordenar los Datos
-----------------

La API permite ordenar los resultados obtenidos durante la solicitud de un método utilizando el parámetro ``orderBy``. Debe indicarse la columna sobre la cual deseamos ordenar los resultados y entre corchetes si el orden debe ser ascedente [A] o descendente [D].

::

  GET   {url}/indicadores/v1/metodo.json?auth_key={AUTH KEY}&orderBy0=column0[A]&orderBy1=column1[D]

En este caso ordenamos la primer columna de forma ascendente y la segunda columnade forma descendente.


Paginar los resultados
----------------------

Los métodos pueden estar paginados o pueden paginarse en las consultas. Deben utilizarse los siguientes parámetros:

- limit: cantidad de resultados por búsqueda, su valor no puede ser superior al límite establecido en el método
- page: página sobre la cual se retornan los resultados, según lo especificado en ``limit``


Por ejemplo, esta llamada devuelve 20 filas y se ubica en la página 3:

::

  GET   {url}/indicadores/v1/metodo.json?auth_key={AUTH KEY}&limit=20&page=3



Establecer formato de valores númericos
---------------------------------------
El argumento applyFormat permite obtener los resultados de los valores númericos y de fecha en diferentes formatos.


Convierte a string con formato estadounidense: ``applyFormat=0``

Convierte a string aplicando el displayFormat configurado en la vista: ``applyFormat=1``

NUMBER y DATES como double: ``applyFormat=-1``


Agrupaciones y Funciones sobre vistas de datos
----------------------------------------------

Puedes aplicar algunas FUNCIONES y AGRUPACIONES sobre los datos de una vista. Las operaciones se realizan a demanda sobre un juego de columnas definido en una llamada API y asociados a través de dos parámetros ``groupBy`` y ``function``. El resultado puede ser reutilizado como una fuente tipo web service REST/JSON para crear nuevos recursos de datos (vistas, visualizaciones) en el área de trabajo. Las funciones disponibles actualmente son SUM (suma), COUNT (contar), y AVG (promedio).

En primer lugar definiremos la columna que servirá para agrupar mediante el parametro ``groupBy`` seguido de un número que indica la jerarquía ``(groupBy0=column0, groupBy1=column2...)``. Luego, aplicamos una función ``function`` aplicada en la columna sobre la que vamos a operar. Debes incluir paréntesis cuadrados (brackets) al ingresar la columna, pudiendo concatenar mas de una function agregandole un número entero empezando desde cero ``(function0=SUM[column0], function1=COUNT[column10])``.
