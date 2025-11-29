# Vinculación con GitHub Pages

A continuación se explica el proceso para activar y configurar GitHub Pages, permitiendo publicar la documentación del proyecto de manera que sea accesible y vista de manera pública en internet

## Configurar GitHub Pages

Entrar en el menú de arriba del repositorio -> Actions... Y ahí ya estará configurado

![Ejecución del comando](https://raw.githubusercontent.com/vjp-naiaraAH/PPS-Unidad0-Tarea-naiara/refs/heads/main/docs/images/img8.png)

## Creación y prueba del workflow en GitHub Actions

Al crear el archivo .github/workflows/deploy-mkdocs.yml y añadirle la configuración pertinente cada push a la rama main ejecutará automáticamente el workflow "Deploy MkDocs". Además se creará la rama gh-pages que es la rama que tendremos que seleccinar al seguir los pasos de la siguiente captura:

![gh-pages 1](https://raw.githubusercontent.com/vjp-naiaraAH/PPS-Unidad0-Tarea-naiara/refs/heads/main/docs/images/img9.png)

## Resultado final
Si hacemos clic en el siguiente lado de nuestro repositorio de GitHub

![Ghpages en repositorio](https://raw.githubusercontent.com/vjp-naiaraAH/PPS-Unidad0-Tarea-naiara/refs/heads/main/docs/images/img10.png)

Esto es lo que vermos si hemos hecho correctamente los pasos para que todo funcione.

![Visual gh-pages](https://raw.githubusercontent.com/vjp-naiaraAH/PPS-Unidad0-Tarea-naiara/refs/heads/main/docs/images/img14.png)
