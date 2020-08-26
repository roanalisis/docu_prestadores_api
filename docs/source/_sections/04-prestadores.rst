===============
API Prestadores
===============

La API de Prestadores expone datos del Registro Nacional de Prestadores Individuales de Salud. Permite buscar prestadores mediante su rut o número de registro.

La API se compone de dos métodos:

    | ``/prestadores/rut/{rut}``
    | ``/prestadores/registro/{registro}``



Prestadores
===========

Los métodos ``/prestadores/rut/{rut}`` y ``/prestadores/registro/{registro}`` devuelven la ficha de un prestador en formato JSON.

En ambos casos: ``/prestadores/rut/{rut}`` y ``/prestadores/registro/{registro}`` la respuesta es un único prestador.









Estructura JSON
---------------

Este es un ejemplo de salida en formato JSON del metódo ``/prestadores/rut/{rut}``

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
rut                        RUT, identificador único
nombres                    Nombres del prestador consultado
apellidoPaterno            Apellido paterno
apellidoMaterno            Apellido materno
sexo                       Sexo
fechaNacimiento            Fecha de nacimiento expresada en formato dd-mm-yyyy
titulos                    Títulos habilitantes
especialidad               Especialidad principal registrada
habilitadora               Nombre de la institución que entrega la matrícula habilitante
vigencia                   Vigencia de la matrícula
codigoBusqueda             Título habilitante
regionPrestador            Región en la que se registró el prestador
comunaPrestador            Comuna en la que se encuentra inscripto
searchRegionTrabajo        Regiones en las que se encuentra inscripto el prestador
telefonos                  Teléfonos de contacto
direccion                  Dirección
email                      Correo electrónico de contacto
estado                     Estado del prestador, su único valor es "Registrado"
===================        =====================================================




Antecedentes
============

El método `/prestadores/antecedentes/{rut}` devuelve los antedecentes de un prestador en formato JSON. Requiere que se envie el rut del prestador para obtener sus antecedentes.


Ejemplo de salida
-----------------

.. code-block:: json

      {
          "apiVersion": "1.0",
          "antecedentes": [
              {
              "rut": 16329928,
              "nombres": "Bernarda Ivette",
              "apellidoPaterno": "Neira" ,
              "apellidoMaterno": "Macaya" ,
              "sexo": "Femenino" ,
              "fechaNacimiento": "02-12-1986" ,
              "codigoBusqueda": "Técnico en Nivel Superior en Salud" ,
              "comuna": null,
              "direccion": null,
              "rutEstablecimiento": null,
              "nomEstablecimiento": null,
              "nombreFantasia": "CFT INACAP" ,
              "regionEst": null,
              "comunaEst": null,
              "dirEstablecimiento": null,
              "fechaAntecedente": "06-06-2008" ,
              "codAntecedente": "Técnico de Nivel Superior en Enfermería" ,
              "tipoAntecedente": "T" ,
              "claseAntecedente": "Título" ,
              "observacion": null,
              "procedencia": "Centro de Formación Técnica INACAP" ,
              "fechaActivacion": "28-09-2011" ,
              "nroRegistro": 131072,
              "estado": "Registrado"
              }
          ],
          "filas": 1,
          "total": 1,
          "timestamp": 0
      }


Diccionario
-----------

===================        =====================================================
Atributo                   Descripción
===================        =====================================================
rut                        RUT, identificador único
nombres                    Nombres del prestador consultado
apellidoPaterno            Apellido paterno
apellidoMaterno            Apellido materno
sexo                       Sexo
fechaNacimiento            Fecha de nacimiento expresada en formato dd-mm-yyyy
codigoBusqueda             Nombre descriptivo del antecedente
comuna                     Comuna en la que se encuentra inscripto
direccion                  Dirección
rutEstablecimiento         RUT, idendificador único del establecimiento
nomEstablecimiento         Nombre del establecimiento
nombreFantasia             Nombre de fantasía del establecimiento
regionEst                  Región del establecimiento
comunaEst                  Comuna del establecimiento
dirEstablecimiento         Dirección del establecimiento
fechaAntecedente           Fecha del antecedente
codAntecedente             Código del antecedente
tipoAntecedente            Tipo del antecedente
claseAntecedente           Clase del antecedente
observacion                Observaciones complementarias
procedencia                Nombre del establecimiento que otorgó el antecedente
fechaActivacion            Fecha de alta del antecedente
nroRegistro                Identificador interno de la Superintendencia de Salud
estado                     Estado del prestador, su único valor es "Registrado"
===================        =====================================================
