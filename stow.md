# STOW - sincronizar .dotfiles

Sincronizar las .dotfiles creando un repositorio git y haciendo
symlinks con stow; la idea es que primero se crea el repositorio git,
luego lo enlazas a un origin para que esté disponible para más setups,

ese repositorio debe estar en ~/.dotfiles (debe, porque stow trabaja
con la lógica de "un directorio por encima de este", aunque puedes
explicitar el directorio donde sincronizar los archivos, y de hecho
es aconsejable).


**code**
```
stow -nvSt ~ *
```
-n <--Simulación, sirve para probar el comando antes de liarla
-S no hace falta ponerlo, po defecto es S, pero lo pongo para
recordar que en caso de querer deslinkear un archivo, la alternativa
o lo contrario de -S es -D (delink?)
-v debe ser verbose pero no lo miré
-t target, hace referencia al directorio, en este caso de arriba
se explicita que es home/user pero podría no estar, por defecto
se hace en el directorio superior, y si se ha creado .dotfiles
en ~ entonces no haría falta. Pero para árboles de directorios
más complejos es mejor explicitarlo.
* <-- todo, pero podrías simplemente elegir una carpeta dentro de .dotfiles
(git, bash, vim.. la que hayas creado, y dentro estaría el archivo
que realmente quieres simlinkear y sincronizar con el directorio).

**code**
```
stow --adopt -nvSt ~ *
```
ESTO sirve para "adoptar" el archivo que realmente estás usando en la 
configuración de una máquina concreta, eso hace que se SUSTITUYA el
archivo que se está usando por el que está dentro de nuesto repositorio,
con lo cual solo lo he utilizado UNA VEZ, y la otra única vez donde
debería usarlo es si quiero empezar un dotfile nuevo de algún programa
nuevo para el que no tengo confi y que la que está en la máquina me sirve,
pero vamos, que no, que lo dejo solo para que se vea que existe pero... 

UNA VEZ creado el directorio y subido a git y todo eso, ya solo queda
clonarlo cada vez que empiece un nuevo setup.

**code**
```
git clone URL ~
```
como el propio repositorio se llama .dotfiles ya se creará como carpeta oculta.

Sources:



[text](URL)


