# Despliegue de una Aplicación Dash en Heroku

Heroku es una plataforma de despliegue de aplicaciones web fácil de usar. A continuación, se detallan los pasos para desplegar una aplicación Dash en Heroku.

## Paso 1: Registro en Heroku

Primero, regístrate en Heroku y obtén un nombre de usuario y contraseña. Luego, instala la [CLI de Heroku](https://devcenter.heroku.com/articles/heroku-cli).

## Paso 2: Configuración Inicial

Crea un repositorio y un entorno virtual para tu aplicación Dash.

```bash
git init
virtualenv venv
source venv/bin/activate
```

## Paso 3: Instalación de Dependencias

Asegúrate de que todas las dependencias estén instaladas ejecutando el siguiente comando:

```bash
pip install -r requirements.txt
```

## Paso 4: Crea una estructura para tu aplicación

1. Crea un repositorio de git en tu carpeta de proyecto

```bash
cd "Your folder"
git init
git add .
git commit -m “Initial commit”
```

2. Arranca dashtools dentro de tu repositorio de git

```bash
dashtools gui
```

3. Crea un proyecto en la pestaña crear

## Paso 5: Programa tu Aplicación

Modifica el archivo __src/app.py__ y añade el código necesario para tu aplicación Dash.

## Paso 6: Despliegue de la Aplicación

1. Utiliza DashTools Deploy para desplegar en render.com utilizando la pestaña deploy

2. Darse de alta en render.com

3. Push código a github

[Cómo crear y desplegar plotly dash apps](https://medium.com/@ahossack07/create-and-deploy-plotly-dash-apps-to-the-internet-for-free-49ebca9633da)

## Paso 6: Actualización de la Aplicación

Si necesitas actualizar tu aplicación, sigue estos pasos:

```bash
git status # visualiza los cambios realizados
git add . # añade todos los cambios
git commit -m 'Descripción de los cambios realizados'
git push heroku master # actualiza la aplicación en Heroku
```

¡Listo! Ahora puedes desplegar y actualizar tu aplicación Dash en Heroku de manera sencilla.