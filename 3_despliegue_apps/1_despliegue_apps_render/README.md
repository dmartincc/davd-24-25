# Despliegue de una Aplicación Dash en Render

Render es una plataforma de despliegue de aplicaciones web fácil de usar. A continuación, se detallan los pasos para desplegar una aplicación Dash en Render.

## Paso 1: Registro en Render

Primero, regístrate en Render y crea un repositorio en github.

## Paso 2: Configuración Inicial

Crea un repositorio y un entorno virtual para tu aplicación Dash.

```bash
cd "Your folder"
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

## Paso 6: Actualización de la Aplicación

Si necesitas actualizar tu aplicación, sigue estos pasos:

```bash
git status # visualiza los cambios realizados
git add . # añade todos los cambios
git commit -m 'Descripción de los cambios realizados'
git push -u origin main
```

¡Listo! Ahora puedes desplegar y actualizar tu aplicación Dash en Render de manera sencilla.

En el siguiente artículo puedes entender el proceso en más detalle.

[Cómo crear y desplegar plotly dash apps](https://medium.com/@ahossack07/create-and-deploy-plotly-dash-apps-to-the-internet-for-free-49ebca9633da)
