# Controlando nuestra aplicación con flask-script

La extensión [flask-script](https://flask-script.readthedocs.io/en/latest/) nos proporciona la posibilidad de gestionar nuestra aplicación flask desde un comando (Interfaz de línea de comando).

Nos permite escribir pequeños programa (scripts) que gestionen nuestra aplicación, por defecto nos ofrece el servidor web de desarrollo y un interprete (shell) con nuestra aplicación cargada.

## Instalación de la extensión flask-script

Con nuestro entorno virtual activado, ejecutamos:

	$ pip install Flask-Script

Por lo tanto en nuestro fichero `requirements.txt` añadimos el nuevo módulo:

	Flask
	Flask-Script

## Estructura de nuestra aplicación

Vamos a organizar nuestra aplicación web en un paquete con la siguiente estrucutra de directorios:

	manage.py
	requirements.txt
	aplicacion
		app.py
		__init__.py

* `manage.py`: Será el script que utilizaremos para gestionar la aplicación (flask-script).
* `requirements.txt`: Fichero con los módulos necesarios para nuestra aplicación funcione.
* `aplicacion`: Paquete python (hemos creado el fichero `__init__.py`) donde vamos a guardar los ficheros de nuestra aplicación, por ahora guardamos el módulo principal `app.py`.

## CLI con flask-script

El contenido del fichero mangage.py será el siguiente:

	from flask_script import Manager
	from aplicacion.app import app
	
	manager = Manager(app)
	app.config['DEBUG'] = True # Ensure debugger will load.
	
	if __name__ == '__main__':
		manager.run()

## Utilización de manage.py

Por defecto el CLI flask-script nos proporciona dos funciones: el servidor web de desarrollo y una shell interactiva con el contexto de la aplicación.

	python3 manage.py runserver
	 * Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)
	 * Restarting with stat
	 * Debugger is active!
	 * Debugger PIN: 106-669-497

Si queremos cambiar la dirección y el puerto:

	python3 manage.py runserver -h 0.0.0.0 -p 8080

Y para accedr a la shell:

	python3 manage.py shell 

	In [1]: app
	Out[1]: <Flask 'aplicacion.app'>	

	In [2]: app.config
	Out[2]: <Config {'JSON_AS_ASCII': True, ...>

## Código ejemplo de esta unidad

[Código](../../ejemplos/u8)