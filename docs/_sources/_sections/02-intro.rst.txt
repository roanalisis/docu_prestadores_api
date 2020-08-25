============
Introducción
============

Registro
========

Para hacer llamadas a esta API se requerirá un código de acceso (AUTH KEY) que se enviará como parámetro en cada solicitud. Para solicitar tu código de acceso debes registrarte haciendo click `aquí <https://desarrolladores.superdesalud.gob.cl/signup/>`_.


Autorización
============

Una vez autenticado en SuperSalud Desarrolladores podrás obtener tu AUTH KEY ingresando a cada API.

Las AUTH KEY son únicas y deben mantenerse en secreto. En caso requieran una AUTH KEY pública deben contactarse con el equipo de SuperSalud Desarrolladores.

Los métodos públicos podrán ser consultados mediante la registración en SuperSalud Desarrolladores. En cambio, para acceder a métodos privados, el equipo de SuperSalud Desarrolladores debe previamente autorizarlo.

Si un método es despublicado o borrado, no podrá consultarlo.

Las limitaciones de consultas se definen a nivel global de API o por método consultado. Puede ver el detalle de los límites en cada método.

Las AUTH KEY solo permiten operaciones de lectura.


Errores
=======

La API de SuperSalud Desarrolladores por defecto usa respuesta HTTP convencionales para indicar el éxito o el fracaso de una llamada a la API. Siguiendo los lineamientos HTTP los códigos de rango 2xx indican éxito y los códigos de rango 4xx indican un error.


- ParseError: Se han enviado erróneamente los argumentos al método "400 Bad Request".
- AuthenticationFailed: Error de autenticación "401 Unauthenticated"
- NotAuthenticated: El query viene sin autenciación "401 Unauthenticated"
- PermissionDenied: Error de acceso no permitido "403 Forbidden".
- NotFound: El recurso no se encuenta "404 Not Found".
- MethodNotAllowed: Se quiere ejecutar un método (POST, PUT, ect) no permitido "405 Method Not Allowed".
- NotAcceptable: Se pide que se devuelva la inforamción en un tipo de dato que no es válido "406 Not Acceptable".
- UnsupportedMediaType: Se intenta subir un tipo de dato que no es válido "415 Unsupported Media Type".
- Throttled: Se superó el límite de accesos "429 Too Many Requests".
- ValidationError: Parámetros inválidos "400 Bad Request".
- UnexpectedError: Error inesperado "500 internal Server".

Algunos métodos pueden responder con errores específicos que se encuentran documentados en la sección correspondiente a cada método.


Paginación
==========

Todos los métodos de listado de recursos de la API tienen el funcionamiento de paginado. Cualquiera puede recibir el siguiente parámetro:

- from: página de resultados


Versiones
=========

Puede identificar las versiones de cada API en su página de detalles.
