# Creación del repositorio y Gestión del mismo con uso de Git y GitHub

A continuación voy a documentar el proceso completo y correcto de configuración y despliegue de un repositorio además de su viasualización en GitHub.

## Creación del repositorio 

1. Lo primero fue crear el repositorio, en mi caso  decidí hacerlo mediante el entorno gráfico en Github ya que se me hacía más comodo que por línea de comandos.
1. Lo siguiente fue clonar el repositorio en el Desktop de mi máquina virtual mediante ssh siguiendo los pasos de las siguientes imagenes. 
![visualización desde navegador](https://raw.githubusercontent.com/vjp-naiaraAH/PPS-Unidad0-Tarea-naiara/refs/heads/main/docs/images/img1.png)
![visualización desde navegador](https://raw.githubusercontent.com/vjp-naiaraAH/PPS-Unidad0-Tarea-naiara/refs/heads/main/docs/images/img2.png)
1. Y con ayuda del comando cp -r copio toda la base del repositorio CalculadoraPython puesto que ambos proyectos tienen la misma base.
![visualización desde navegador](https://raw.githubusercontent.com/vjp-naiaraAH/PPS-Unidad0-Tarea-naiara/refs/heads/main/docs/images/img3.png)
1. Listo el contenido para verificar que tiene al estructura deseada con ayuda del siguiente comando
> ls -la

![visualización desde navegador](https://raw.githubusercontent.com/vjp-naiaraAH/PPS-Unidad0-Tarea-naiara/refs/heads/main/docs/images/img4.png)

1. Para visualizar la estructura de los archivos de la documentación tendremos que ver lo que tenemos ya creado con ayuda del comando

> tree

Y A partir de ahí ya creamos los archivos necesarios para escribir después la documentación pertinente
![visualización desde navegador](https://raw.githubusercontent.com/vjp-naiaraAH/PPS-Unidad0-Tarea-naiara/refs/heads/main/docs/images/img5.png)

Cambio al repositorio en el cual quiero que esté la documentación:

> cd docs

Creación de los archivos para tener la documentación ordenada:

> mkdir git.md gitActions.md gitPages.md docker.md conclusiones.md
 
### Subida de los cambios a GitHub

Para subir el proyecto a GitHub después de realizar los diferentes cambios será siguiendo los siguientes pasos

#### Agrega cambios al staging area

> git add .

#### Crea un commit con un comentario 

> git commit -am "Creación de archivos para documentacion"

#### Sube los cambios al repositorio remoto y en concreto a la rama main

> git push origin main

### Comprobación en GitHub de que se han subido los cambios correctamente
![Repositorio en GitHub](https://raw.githubusercontent.com/vjp-naiaraAH/PPS-Unidad0-Tarea-naiara/refs/heads/main/docs/images/img.png)