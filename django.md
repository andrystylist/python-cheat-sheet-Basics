# Notas de estudio del Framework Django

## [Instalación](https://www.djangoproject.com/download/) con [Pipenv](https://pipenv.pypa.io/en/latest/install/)

```sh
cd ~/Workspace/python

mkdir my-project
cd my-project

pipenv install Django==4.1.5
```

## Inicio de un proyecto

```sh
# Habilitar el entorno virtual
pipenv shell

# Comenzar un proyecto
django-admin startproject [nombre_del_proyecto] . <= el punto me ayuda a crear los archivos ahi mismo sin crear otra carpeta



# CLI de administración del proyecto 
./manage.py
python manage.py

# Ejecutando el comando de proyecto ejecutar servidor  (puede recibir parametros ) me importa el enlace que aparece http:... le damos command CLICK, abre pagina aparte. este comando tambien crea carpeta de base datos por defecto db sqlite3

python manage.py runserver 

```
# Estructura del proyecto

```sh
#  ver todos los comandos disponibles en el proyecto
python manage.py --help

```


