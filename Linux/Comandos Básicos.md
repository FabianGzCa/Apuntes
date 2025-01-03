¿Quién soy? Mira el usuario con el que estás ejecutando comandos.
ejemplo del comando:
```bash
❯ whoami
myuser
```

* ## sudo
Utiliza comandos como súper usuario.
ejemplo del comando:
```bash
❯ whoami
myuser

❯ sudo whoami
[sudo] password for myuser:              
root
```

* ## pwd
¿Dónde estoy? Por lo regular las shells muestran en su estructura la ruta en la que nos encontramos, pero en caso de requerirlo el comando pwd nos muestra nuestra ruta actual absoluta.
Ejemplo del comando:
```bash
❯ pwd
/home/myuser/Documents/TmpFiles/DirectorioAleatorio
```

* ## ls
Muestra los archivos y directorios del directorio en el que nos encontramos.
-> Como parámetro adicional se puede agregar un -l para agregar información más específica de los archivos/directorios.
-> Como parámetro adicional se puede agregar un -a para mostrar aquellos archivos/directorios que se encuentren ocultos.
Ejemplo del comando:
```bash
❯ ls
DirectorioAleatorio  miArchivo

❯ ls -l
total 16
drwxrwxr-x 2 fabiangzca fabiangzca 4096 Dec 17 23:04 DirectorioAleatorio
-rw-rw-r-- 1 fabiangzca fabiangzca   47 Dec 17 22:52 miArchivo

❯ ls -a
.  ..  DirectorioAleatorio  miArchivo  .oculto

❯ /bin/ls -la
total 36
drwxrwxr-x 3 fabiangzca fabiangzca 4096 Dec 17 23:21 .
drwxr-xr-x 6 fabiangzca fabiangzca 4096 Dec 17 22:51 ..
drwxrwxr-x 2 fabiangzca fabiangzca 4096 Dec 17 23:04 DirectorioAleatorio
-rw-rw-r-- 1 fabiangzca fabiangzca   47 Dec 17 22:52 miArchivo
-rw-rw-r-- 1 fabiangzca fabiangzca   27 Dec 17 23:21 .oculto
```

* ## cd
Cambia de directorio dentro de la shell.
-> Utiliza `cd {directorio}` para cambiar al {directorio}.
-> `..` representa retroceso, `.` representa la ruta actual (su uso es opcional dado que se suele tomar por defecto pero es útil cuando hay que pasar parámetros en otros comandos) y `/` separa rutas.
-> Si solamente utilizamos el comando `cd` sin argumentos nos mandará al directorio de nuestro usuario.
-> Si solamente utilizamos / se considera como la ruta absoluta, la raíz de nuestro Linux.
-> El directorio de los usuarios se almacena en el archivo `/etc/passwd`
Ejemplos:
```bash
❯ pwd
/home/myuser/Documents/TmpFiles

❯ cd ../../
❯ pwd
/home/myuser

❯ cd ./Documents/TmpFiles
❯ pwd
/home/myuser/Documents/TmpFiles

❯ cd /
❯ pwd
/

❯ cd
❯ pwd
/home/myuser
```

* ## which
Muestra la ruta absoluta del comando que le pasamos como parámetro, en caso de ser un alias nos lo hará saber.
-> En caso de que el comando no exista tenemos la alternativa `command -v` que hace exactamente lo mismo que el which.
Ejemplo del comando:
```bash
❯ which id
/usr/bin/id

❯ which cat
cat: aliased to /usr/bin/batcat

❯ command -v sudo
/usr/bin/sudo
```

* ## cat
Muestra el contenido de un archivo.
Ejemplo del comando:
```bash
❯ cat miArchivo
Este es un archivo de prueba.
¿Puedes leerme?
```

* ## id
¿A que grupos pertenezco?
Este comando se desglosa en 3 secciones, en las cuales muestra:
**uid:** user id, este es el identificador de nuesto usuario.
**gid:** group id, este es el identificador del grupo principal al que pertenece nuestro usuario.
**groups:** Grupos a los que pertenece nuestro usuario.
-> Cada usuario suele tener un grupo creado con su mismo nombre.
-> Los grupos están almacenados en el archivo `/etc/groups`.
Ejemplo del comando:
```bash
❯ id
uid=1000(myuser) gid=1000(myuser) groups=1000(myuser),27(sudo),105(lpadmin),125(sambashare)
```

* ## echo
Escribe un mensaje en tu terminal.
-> Podemos utilizar el símbolo `$` y una palabra para llamar a una variable del sistema y `#` para comentar todo el texto siguiente para que no se imprima.
-> Podemos meter el texto entre "" para ignorar **algunos** caracteres como ? y dar un mejor formato.
Ejemplo del comando:
```bash
❯ echo Esta es una prueba
Esta es una prueba

❯ echo $MIVARIABLEPERSONALIZADA
Esto estaba almacenado en una variable del sistema.

❯ echo "Hola ¿Cómo estás?"
Hola ¿Cómo estás?
```