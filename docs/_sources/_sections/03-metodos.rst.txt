=======
Métodos
=======

Las APIs están conformadas por conjuntos de métodos que exponen los datos.

A continuación se detallan ejemplos generales. Para mayor detalle sugerimos revisar la documentación de cada API.


Llamadas a un método
--------------------

::

  GET   {url}/api/nombre-de-api/rut/{rut}/?apikey={apikey}



Por tanto, la estructura de la ruta de la solicitud es:
``api`` es parte del nombre de la API.
``nombre-de-api`` es el nombre del servicio o de la API.
``rut`` es parte del nombre de la API e indica el parámetro por el que se hará la consulta, en este ejemplo por el rut.
``{rut}`` es el parámetro de ruta correspondiente al rut por el que se realiza la búsqueda.
``{apikey}`` es la clave que necesitarás para cada solicitud.


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

  GET   {url}/indicadores/v1/metodo.json?auth_key={apikey}&anio=2010&mes=01


De manera que para consultar métodos con parámetros, debe enviarse el nombre del parámentro y un valor válido. En caso que los valores no sean válidos, la respuesta será en base a los valores por defecto.



