===============
API Prestadores
===============

La API de Prestadores expone datos del Registro Nacional de Prestadores Individuales de Salud. Permite buscar prestadores mediante su rut o número de registro.

La API se compone de dos métodos:

    | ``/api/prestadores/rut/{rut}``
    | ``/api/prestadores/registro/{registro}``



Prestadores
===========

Los métodos ``/api/prestadores/rut/{rut}`` y ``/api/prestadores/registro/{registro}`` devuelven la ficha de un prestador en formato JSON.

En ambos casos: ``/api/prestadores/rut/{rut}`` y ``/api/prestadores/registro/{registro}`` la respuesta es un único prestador.









Estructura JSON
---------------

Este es un ejemplo de salida en formato JSON. Requiere que se envie el rut del prestador para obtener sus antecedentes. ``/api/prestadores/rut/{rut}``

.. code-block:: json

        {
          "nro_registro" : "000000",
          "sexo" : "Femenino",
          "apellido_materno" : "Uchiha",
          "apellido_paterno" : "Haruno",
          "codigo_busqueda" : "Auxiliares Paramédicos de Farmacia",
          "dv" : "9",
          "fecha_nacimiento" : "22-9-1967",
          "fecha_registro" : "17-10-2011",
          "nacionalidad" : "Chilena",
          "nombres" : "Évelin Andrea",
          "rut" : 1,
          "universidad" : "No Informada",
          "observaciones" : "",
          "antecedentes" : [
            {
              "clase_antecedente" : "Título",
              "cod_antecedente" : "Auxiliar Paramédico de Farmacia",
              "fecha_antecedente" : "12/20/92",
              "fecha_registro" : "10/17/2011",
              "nro_resolucion" : "000",
              "procedencia" : "Universidad de Chile",
              "tipo_antecedente" : "T"
            }
          ],
          "fecha_carga" : "07/08/2020"
        }


Diccionario
-----------

===================        =====================================================
Atributo                   Descripción
===================        =====================================================
nro_registro               Número de registro del prestador consultado
sexo                       Sexo
nombres                    Nombres del prestador consultado
apellido_paterno           Apellido paterno
apellido_materno           Apellido materno
fecha_nacimiento           Fecha de nacimiento expresada en formato dd-mm-yyyy
fecha_registro             Fecha de registro expresada en formato dd-mm-yyyy
nacionalidad               Nacionalidad del prestador consultado
rut                        RUT, identificador único
dv                         Dígito verificador
codigo_busqueda            Título habilitante
universidad                Universidad dónde estudió del prestador consultado
observaciones              Observaciones
clase_antecedente          Por ejemplo si corresponde a un título
cod_antecedente            Título habilitante
fecha_antecedente          Fecha antecedente
fecha_registro             Fecha registro
nro_resolucion             Número resolución
Procedencia                Nombre de la institución en la que estudió
tipo_antecedente           Tipo antecedente
===================        =====================================================




