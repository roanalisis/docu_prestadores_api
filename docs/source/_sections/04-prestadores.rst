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

Este es un ejemplo de salida en formato JSON. Requiere que se envie el rut del prestador, sin el dígito verificador, para obtener sus antecedentes. ``/api/prestadores/rut/{rut}``

.. code-block:: json

        {
            "nro_registro": "334583",
            "sexo": "Femenino",
            "nombres": "Rosa Elena",
            "apellido_paterno": "Fernández",
            "apellido_materno": "Mena",
            "fecha_nacimiento": "13-11-1976",
            "fecha_registro": "18-5-2012",
            "nacionalidad": "Chilena",
            "rut": 12950968,
            "dv": "6",
            "codigo_busqueda": "Técnico en Nivel Superior en Salud",
            "universidad": "No Informada",
            "observaciones": "",
            "fecha_carga": "26/08/2020",
            "antecedentes": [
                {
                    "clase_antecedente": "Título",
                    "cod_antecedente": "Técnico Laboratorista Dental",
                    "fecha_antecedente": "08/17/2000",
                    "fecha_registro": "No Informada",
                    "nro_resolucion": "412",
                    "procedencia": "CFT Santo Tomás",
                    "tipo_antecedente": "T"
                }
            ]
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




