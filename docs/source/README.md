=====================
Generar documentación
=====================


Requereimientos e instalación de Sphinx
=======================================

Instalar Sphinx en Windows

1. Instalar Python
	Descargar el ejecutable de https://www.python.org/downloads/ e instalar. 

2. Instalar paquete pip
	Descargar paquete https://bootstrap.pypa.io/get-pip.py  
	Guardarlo en la carpeta C:/Python27/Scripts 
	Abrir consola y ejecturar: python get-pip.py
	
3. Instalar Sphinx
	Abrir consola y ubicarse en la carpeta C:/Python27/Scripts 
	Ejecutar comando: pip install sphinx 
	Para confirmar instalación ejecutar comando: sphinx-build -h

4. Instalar tema
	Ejecutar comando: pip install sphinx_rtd_theme


En Windows:
 Puede ser necesario agregar la ruta a C:/Python27/Scripts como variable de entorno para poder ejecutar el tercer paso.
 Ir a Control Panel\System and Security\System. 
 Luego a Advanced System Settings. 
 En la pestaña Advanced, abrir Enviromental Variables...
 Editar la variable Path. Agregar al final: ;C:\Python27\Scripts


Documentación
-------------
http://www.sphinx-doc.org/en/stable/install.html
https://github.com/sphinx-doc/sphinx



Generar archivos de documentación
---------------------------------

Ejecutar en la consola:

		`sphinx-build -b html C:\...\documentacion_api_prestadores\docs\source\ C:\Users\...\documentacion_api_prestadoreses\docs`
