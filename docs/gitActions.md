# Creación de WorkFlow de GitHub Actions6

A continuación se va a documentar el proceso de creación e implementación del workflow de GitHub Actions que automatiza la generación y publicación de la documentación del proyecto

## Código del Workflow

~~~yaml
name: Generar documentación con MkDocs

on:
  push:
    branches:
      - main
  workflow_dispatch:

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    
    permissions:
      contents: write
    
    steps:
      - name: Checkout del repositorio
        uses: actions/checkout@v4
      
      - name: Configurar Python
        uses: actions/setup-python@v4
        with:
          python-version: '3.x'
      
      - name: Instalar dependencias
        run: |
          pip install mkdocs
          pip install mkdocs-material
      
      - name: Generar documentación
        run: mkdocs build
      
      - name: Publicar en GitHub Pages
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./site
~~~

+++

## Explicación

### 1. Nombre del workflow
```yaml
name: Generar documentación con MkDocs
```
Seleccionar un nombre explicativo que se mostrará en la sección "Actions" de GitHub para facilitar su reconocimiento

+++

### 2. Eventos disparadores
```yaml
on:
  push:
    branches:
      - main
  workflow_dispatch:
```


- `push: branches: - main`: El workflow se ejecuta automáticamente cada vez que se realiza un push a la rama `main`
- `workflow_dispatch`: Permite ejecutar el workflow manualmente desde la interfaz de GitHub, útil para pruebas o regeneraciones bajo demanda

+++

### 3. Definición del Job
```yaml
jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
```


- `build-and-deploy`: Nombre descriptivo del trabajo que se va a ejecutar
- `runs-on: ubuntu-latest`: Especifica que el job se ejecutará en una máquina virtual con Ubuntu en su última versión estable. Ubuntu es ideal por ser ligero, rápido y compatible con la mayoría de herramientas de desarrollo

+++

### 4. Permisos
```yaml
permissions:
  contents: write
```

 Otorga permisos de escritura al workflow para que cree y modifique la rama `gh-pages` donde se publicará la documentación. Sin este permiso, el workflow fallaría al intentar hacer push.

+++

### 5. Step 1: Checkout del repositorio
```yaml
- name: Checkout del repositorio
  uses: actions/checkout@v4
```

 Este step clona el repositorio en la máquina virtual del runner. Es necesario para acceder a todos los archivos del proyecto, incluida la configuración de MkDocs y los archivos Markdown.

+++

### 6. Step 2: Configurar Python
```yaml
- name: Configurar Python
  uses: actions/setup-python@v4
  with:
    python-version: '3.x'
```

 Instala Python en la máquina virtual, necesario porque MkDocs es una herramienta escrita en Python. La versión `3.x` garantiza que se use la última versión estable de Python 3.
+++

### 7. Step 3: Instalar dependencias
```yaml
- name: Instalar dependencias
  run: |
    pip install mkdocs
    pip install mkdocs-material
```


- Instala MkDocs, la herramienta que genera la documentación estática
- Instala el tema Material (opcional pero recomendado) que proporciona un diseño moderno y responsive
- El símbolo `|` permite ejecutar múltiples comandos en secuencia

+++

### 8. Generar documentación
```yaml
- name: Generar documentación
  run: mkdocs build
```

 Ejecuta el comando que lee todos los archivos Markdown del proyecto y genera los archivos HTML estáticos en la carpeta `site/`. Esta carpeta contendrá la web completa lista para ser servida.

+++

### 9. Step Publicar en GitHub Pages
```yaml
- name: Publicar en GitHub Pages
  uses: peaceiris/actions-gh-pages@v3
  with:
    github_token: ${{ secrets.GITHUB_TOKEN }}
    publish_dir: ./site
```


- Utiliza una acción predefinida especializada en publicar contenido en GitHub Pages
- `github_token`: Token de autenticación automático que GitHub proporciona a cada workflow
- `publish_dir: ./site`: Especifica que el contenido de la carpeta `site` (generada por MkDocs) debe publicarse en la rama `gh-pages`
  
