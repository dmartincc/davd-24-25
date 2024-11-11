# Despliegue de una Aplicación Dash en Render

Render es una plataforma sencilla y potente para desplegar aplicaciones web. Esta guía te ayudará a desplegar una aplicación Dash en Render utilizando una estructura de proyecto recomendada y los archivos necesarios. Las instrucciones están divididas en pasos para configuraciones en Linux y Windows, e incluyen cómo conectar GitHub y Render para un flujo de trabajo simplificado.

## Estructura de Proyecto Recomendada

Antes de comenzar, asegúrate de que tu proyecto esté organizado de la siguiente manera. Esta estructura ayuda a mantener el código ordenado y facilita la configuración del despliegue:

```plaintext
Tu_carpeta_de_proyecto/
│
├── src/                   # Carpeta con el código fuente de la aplicación               
│   ├── __init__.py        # Archivo vacío para definir src como módulo (opcional)
│   ├── graphics.py        # Archivo de gráficos a renderizar
│   ├── model.py           # Archivo de entrenamiento e inferencias
│   └── etl.py             # Archivo para cargar datos
│
├── app.py                 # Archivo principal de la aplicación Dash
├── requirements.txt       # Archivo de dependencias de Python
├── Procfile               # Archivo para especificar el comando de inicio en Render
├── render.yaml            # Archivo de configuración para Render
└── README.md              # Documentación del proyecto
```

### Archivos y Su Función

1. **`app.py`**: Archivo principal de la aplicación Dash. Define el objeto `app` y la estructura de la interfaz de usuario.

   ```python
   # app.py
   import dash
   
   from dash import html
   from src import graphics, etl

   app = dash.Dash(__name__)
   app.layout = html.Div(children=[
       html.H1("¡Hola, Render!"),
       html.P("Esta es una aplicación Dash desplegada en Render.")
   ])

   if __name__ == "__main__":
       app.run_server(debug=True)
   ```

2. **`requirements.txt`**: Lista de dependencias necesarias para la aplicación. Render utilizará este archivo para instalar automáticamente los paquetes.

   ```text
   dash
   gunicorn
   ```

3. **`Procfile`**: Archivo que indica a Render cómo ejecutar la aplicación en producción.

   ```plaintext
   web: gunicorn app:app
   ```

4. **`render.yaml`**: Archivo de configuración que Render usa para automatizar el despliegue de la aplicación.

   ```yaml
   services:
     - type: web
       name: dash-app
       env: python
       plan: free
       buildCommand: "pip install -r requirements.txt"
       startCommand: "gunicorn app:app"
   ```

5. **`runtime.txt`**: Archivo de configuración que Render usa para automatizar seleccionar python runtime.

   ```text
   python-3.10.7
   ```
[Cómo configurar la versión de python en render]()
   https://docs.render.com/python-version?_gl=1%2Aptov9w%2A_gcl_au%2AMjA3MTQ4NjI0NS4xNzMwNzEzMjM3%2A_ga%2AMjQ1MTk0ODY5LjE3MzA3MTMyMzg.%2A_ga_QK9L9QJC5N%2AMTczMTMyMDk0OC4yLjEuMTczMTMyMTcyMC42MC4wLjA.)

5. **`README.md`**: Documentación del proyecto.

## Paso 1: Configuración del Entorno de Desarrollo

1. **Crea o clona un repositorio Git para tu aplicación**:

   ```bash
   cd "Tu_carpeta_de_proyecto"
   ```

   Si el repositorio no está inicializado en Git, hazlo ahora:

   ```bash
   git init
   ```

2. **Crea un entorno virtual** para tu aplicación Dash, de acuerdo con tu sistema operativo:

   - **En Linux:**
     ```bash
     python3 -m venv venv
     source venv/bin/activate
     ```
   - **En Windows:**
     ```cmd
     python -m venv venv
     venv\Scripts\activate
     ```

3. **Instala las dependencias** dentro del entorno virtual:

   ```bash
   pip install -r requirements.txt
   ```

## Paso 2: Conectar GitHub con Render

1. **Sube tu proyecto a GitHub**:

   - Crea un repositorio en GitHub (puedes hacerlo desde la interfaz web de GitHub). Luego, enlaza tu repositorio local con los siguientes comandos:

     ```bash
     git add .
     git commit -m "Initial commit"
     git remote add origin https://github.com/TuUsuario/TuRepositorio.git
     git branch -M main
     git push -u origin main
     ```

2. **Inicia sesión en Render** y conecta tu cuenta de GitHub:

   - Ve a [Render](https://render.com/) y selecciona **New > Web Service**.
   - Conecta tu cuenta de GitHub y selecciona tu repositorio desde la lista de repositorios disponibles en Render.

3. **Configura las opciones de despliegue**:

   Render detectará el archivo `render.yaml` en la raíz del proyecto y configurará el servicio automáticamente.

## Paso 3: Despliegue de la Aplicación en Render

1. **Crea el servicio en Render**:

   - Una vez que Render haya detectado tu configuración en `render.yaml`, haz clic en **Create Web Service**.
   - Render comenzará a construir y desplegar la aplicación; esto puede tardar unos minutos. Al finalizar, Render proporcionará una URL para acceder a tu aplicación.

2. **Verifica la Aplicación**: Una vez que Render haya terminado el despliegue, accede a la URL proporcionada para verificar que tu aplicación está funcionando correctamente.

## Paso 4: Actualización de la Aplicación

Si realizas cambios en tu aplicación, sigue estos pasos para actualizarla en producción:

1. **Guarda los cambios** y sube el código actualizado a GitHub:

   ```bash
   git add .
   git commit -m "Descripción de los cambios realizados"
   git push origin main
   ```

2. Render detectará automáticamente los nuevos cambios en el repositorio y reconstruirá la aplicación para reflejar las actualizaciones en producción.

## Recursos Adicionales

Para obtener más información sobre el despliegue de aplicaciones Dash en Render, puedes consultar el artículo: [Cómo crear y desplegar aplicaciones Plotly Dash](https://medium.com/@ahossack07/create-and-deploy-plotly-dash-apps-to-the-internet-for-free-49ebca9633da).

¡Listo! Con esta guía, ahora tienes todo lo necesario para desplegar y mantener tu aplicación Dash en Render de manera sencilla y estructurada.