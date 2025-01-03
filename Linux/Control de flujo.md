*  ## punto y coma
Con el `;` separamos varios comandos para ejecutarlos al mismo tiempo sin tener que ir ejecutandolos uno a uno, **todos se intentarán ejecutar** sin importar errores.
```bash
❯  ls; gato; comando; cat archivo
 Linux   Indice.md   README.md
zsh: command not found: gato
zsh: command not found: comando
[bat error]: 'archivo': No such file or directory (os error 2)
```
* ## Código de estado de un comando
Al ejecutar comandos estos devolveran un código de estado, donde:
**0 es que el comando se ha ejecutado correctamente.**
**1 es que el archivo o directorio especificados no han sido encontrados.**
**127 es que el comando no ha sido encontrado.**
Entre otros, podemos ver el códgio de estado al ejecutar el comando `echo $?` después del comando del que deseamos conocer su códgo de estado.

Ejemplos:
```bash
❯ ls
'hola.txt'

❯ echo $?
0

❯ comandoinexistente
zsh: command not found: comandoinexistente

❯ echo $?
127

❯  cat algo
[bat error]: 'algo': No such file or directory (os error 2)

❯ echo $?
1
```


* ## &&
Toma 2 argumentos a ejecutar y el código de estado del primero deberá ser correcto para poder ejecutar el segundo argumento, en otras palabras ejecuta 2 comandos `comando1 && comando2` donde ejecutará comando2 si y solo si comando2 devuelve un código de estado exitoso.
ejemplo de uso:
```bash
❯ echo "Esto sí se puede" && echo "Todo funciona"
Esto sí se puede
Todo funciona

❯ echo "Esto también sirve" && ElPrimerComandoSiFuncionara
Esto también sirve
zsh: command not found: ElPrimerComandoSiFuncionara

❯ estoNoSirve && ls
zsh: command not found: estoNoSirve
```

* ## ||
Tiene la misma función que `&&` solo que los comandos se ejecutarán independientemente de si alguno cuenta con código de estado inválido.
```bash
❯ comandoInexistente & echo "Sí sirve"
Sí sirve
zsh: command not found: comandoInexistente

❯ echo "Sí sirve" & comandoInexistente
Sí sirve
zsh: command not found: comandoInexistente
```

* ## stderr
Las salidas de errores de comandos son manejados con **stderr** y pueden ser referenciados con el número 2, ejemplo de uso para redirigir el error de un comando al directorio `/dev/null` (directorio que es como un basurero en el que desaparece lo que mandas).

**NOTA:** Podemos convertir el stderr a **stdout (salida estándar)** a traves de la redirección `2>&1` dado que 1 es la salida estándar.
ejemplo:
```bash
❯ comandoInexistente 2>/dev/null

❯ echo "Esto no da error" 2>/dev/null
Esto no da error
```