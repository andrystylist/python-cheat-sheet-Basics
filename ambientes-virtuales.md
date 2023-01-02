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
# Crear un ambiente y al mismo tiempo instalar una dependencia
mkdir my-project
cd my-project

pipenv install Django==4.1.5

# Correr un script con el ambiente virtual creado por pipenv
pipenv run python main.py

# Habilitar el ambiente virtual
pipenv shell
```
