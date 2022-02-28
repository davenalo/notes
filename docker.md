## Docker

```
docker system prune
```
borra todo lo que tengas sin correr en docker, pero no las imágenes guardadas en local

### para ver qué imágenes tienes en local
```
docker images
```
### parar un contenedor

```
docker stop id-o-nombre
```

### mostrar contenedores activos o inactivos

```
docker ps -a
```




### Desde la Dockerfile abierta en vscode por ejemplo, usando fórmulas declarativas
```
FROM nginx:1.19.0-alpine (es decir, la aplicación y su "flag" que es lo que va después del :, y hace referencia a la imagen en sí)

COPY . /usr/share/nginx/html (es decir, copia lo que "haya en este directorio (.) que es la Dockerfile y también el código que tengas preparado, a la carpeta desde la cual el sistema operativo (en este caso, alpine) hace que tu código se ejecute)

```
### Después desde consola en el directorio del proyecto:
```
docker build -t elnombrequequieras .
```
### una vez construida la imagen, se ejecuta

```
docker run -it -p 80:80 iddelaimagenoelnombrequepusiste
```
comprueba si funciona con:
```
docker ps

```
O yendo al localhost:80 en este caso.

---



Las dependencias se pueden instalar, pero también puedes buscar la "imagen correcta" en docker hub de alguien que ya la haya puesto. Si necesitas algo que compile C, no va a ser buena idea usar alpine, pero hay otras slim.

Cómo se guarda el código que luego queremos empaquetar con un motor web o una distro linux o lo que sea...?

1. Copiando el código en su directorio correspondiente (interpretados, como js o python)

2. Copiando el empaquetado (angular)

3. copiando el ejecutable (java, go)


### un ejemplo de Dockerfile para python

```Dockerfile
FROM python:3.8.5-alpine...blabla

COPY . /usr/src/app
WORKDIR /usr/src/app

RUN pip install -r requirements.txt

ENTRYPOINT python main.py

```

y por tanto una vez construida (build) se puede entrar con:

```
docker run -it -p 5000:5000 nombredelaimagen

```


tips de Nana:

- usa imágenes oficiales, verificadas y específicas

- Utiliza tag/flag disponible específico, no instales simplemente "ubuntu", sino "ubuntu:1.19 bla bla por ejemplo".

-Ordenar los comandos declarativos de la dockerfile de los que menos a más cambian, así se aprovecha mejor la caché del propio docker.

-use a .dockerignore for ignore "*.git, *.md,..." etc, but you can use files as requirements.txt in python, and others for other techs.

- Multistage builds: crear muchas imágenes para llegar a una imagen final, pero únicamente quedarse con la última

```Dockerfile

#Build stage
FROM maven AS BUILD
WORKDIR /app
...

#Run Stage
FROM tomcat
COPY --from=build /app/target.. /usr/local...


```

con este método multistage se hacen menos layers!!! (se hacen los mismos, pero como luego se descartan, cuentan solo los de la última imagen)


- crea un usuario dedicado y un grupo dedicado, para que tenga los privilegios solo para esa app, y así evitar problemas de seguridad; lo importante es no darle privilegios de root.

```Dockerfile

RUN group add -r nombre && useradd -g nombre nombre

RUN chown -R nombre:nombre /directoriodelaapp

USER nombre

CMD (el comando que sea, supongo)

```

Algunas imágenes ya traen el usuario genérico.

- Scan your images for vulneravilities

```
docker scan imagename
```

this command uses "snyk".