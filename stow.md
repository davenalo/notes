# STOW - sincronizar .dotfiles

Sincronizar las .dotfiles creando un repositorio git y haciendo
symlinks con stow; la idea es que primero se crea el repositorio git,
luego lo enlazas a un origin para que esté disponible para más setups,
ese repositorio debe estar en ~/.dotfiles (debe, porque stow trabaja
con la lógica de "un directorio por encima de este", aunque puedes
explicitar el directorio donde sincronizar los archivos)

**code**
```
stow -nvSt ~ *
```

-n <--Simulación, sirve para probar el comando antes de liarla

-S no hace falta ponerlo, por defecto es S, pero lo pongo para
recordar que en caso de querer deslinkear un archivo, la alternativa
o lo contrario de -S es -D (delink?)

-v debe ser verbose pero no lo miré

-t target, hace referencia al directorio, en este caso del bloque de antes se explicita que es /home/user (~) pero podría no estar, por defecto
se hace en el directorio superior, y si se ha creado .dotfiles
en ~ entonces no haría falta.
* <-- todo, pero podrías simplemente elegir una carpeta dentro de .dotfiles
(git, bash, vim.. la que hayas creado, y dentro estaría el archivo
que realmente quieres symlinkear y sincronizar con el directorio).

**code**
```
stow --adopt -nvSt ~ *
```

Sirve para "adoptar" el archivo que realmente estás usando en la 
configuración de una setup concreta, eso hace que se sustituya el
archivo que se está usando por el que está dentro de nuesto repositorio,
con lo cual solo lo he utilizado una vez, y la otra única vez donde
debería usarlo es si quiero empezar un dotfile nuevo de algún programa
nuevo para el que no tengo y que el que está en esta máquina me sirve. 

UNA VEZ creado el directorio y subido a git y todo eso, ya solo queda
clonarlo cada vez que empiece un nuevo setup.

**code**
```
git clone URL ~
```
como el propio repositorio se llama .dotfiles ya se creará como carpeta oculta.

[YouTube](https://www.youtube.com/watch?v=CFzEuBGPPPg)


