# Creación de un contenedor de servicios NGINX con Docker
En este documento se va a proceder a la documentación del proceso completo para desplegar la documentación generada por MkDocs usando un contenedor de Docker con NGINX como servidor web redirigiendo además el tráfico del puerto al 8085.
----------------------------------------------------------------------------------------------------------------------------------------
## ¿Qué es Docker?
Comencemos con una breve explicación de lo que es Docker, que de manera resumida es una plataforma de virtualización que permite a los desarrolladores empaquetar aplicaciones con todas sus dependencias en unidades estandarizadas llamadas contendores.
----------------------------------------------------------------------------------------------------------------------------------------
## ¿Qué es NGINX?
Nginx es un servidor web de código abierto de alto rendimiento que se usa principalmente para entragar contenido de contenido estátivo o como proxy inverso, balanceador de carga...
----------------------------------------------------------------------------------------------------------------------------------------
###  Ejecución del contenedor Docker
 
> docker run -d \
--name PPSUnidad-Tarea_Naiara_Aguado \
-p 8085:80 \
-v $(pwd):/usr/share/nginx/html:ro \
--restart unless-stopper \
nginx:alpine


#### Explicación del comando usado:

~~~
 docker run -d 
~~~
Crea un nuevo contenedor desde una imágen y lo inicia automáticamente. -d lo que hace es el ejecutarlo en segundo plano sin bloquear la terminal

~~~ 
--name PPSUnidad0-Tarea-Naiara_Aguado
~~~
El nombre exacto que se le va a poner al contenedor para poder identificarlo y usarlo más tarde.

~~~
 -p 8085:80 
~~~
Redirección de puertos. Lo que hace es asociar el puerto 8085 de la máquina en este caso kali al puerto 80 del contenedor.

~~~
 -v "$(pwd)":/usr/share/nginx/html:ro
~~~
Montaje de la carpeta donde estes en el momento en el que ejecutas el comando dentro del contenedor en la ruta donde Nginx busca las páginas web, y en modo solo lectura (:ro)
![Ejecución del comando](https://raw.githubusercontent.com/vjp-naiaraAH/PPS-Unidad0-Tarea-naiara/refs/heads/main/docs/images/img12.png)

### Verificar el despliegue
1. A continuación se ve como si entro en cualquier navegador dela máquina virtual y busco 
~~~
 http://localhost:8085
~~~
Sale la documentación que hemos creado con el contenedor de docker
![visualización desde navegador](https://raw.githubusercontent.com/vjp-naiaraAH/PPS-Unidad0-Tarea-naiara/refs/heads/main/docs/images/img13.png)

2. Comprobación de  que el contenedor está corriendo:
```bash
docker ps
```
![docker ps](https://raw.githubusercontent.com/vjp-naiaraAH/PPS-Unidad0-Tarea-naiara/refs/heads/main/docs/images/img12.png)