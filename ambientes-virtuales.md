# Cómo trabajar con Ambientes Virtuales

# Virtual Environment

```sh
mkdir my-project
cd my-project
python3 -m venv venv

# activar el virtual environment
source venv/bin/activate

# desactivar el virtual environment
deactivate
```

# Pipenv

```sh
# Instalar Pipenv en caso de no tenerlo instalado
pip3 install pipenv

# Crear un ambiente y al mismo tiempo instalar una dependencia
mkdir my-project
cd my-project

# Instalar la dependencia y crear el ambiente vistual para ése directorio
pipenv install Django==4.1.5

# Habilitar el ambiente virtual del directorio donde estás
pipenv shell

# Correr un script con el ambiente virtual creado por pipenv
pipenv run python main.py

```
