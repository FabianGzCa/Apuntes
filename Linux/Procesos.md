* ## &
Al ejecutar un comando podemos colocarlo en segundo plano haciendo uso del `&` al final del comando
Ejemplo:
```bash
wireshark &
[1] 65488
```

* ## disown
Al dejar un comando ejecutandose en segundo plano este seguirá siendo hijo de nuestra terminal actual por lo que si la cerramos el proceso morirá aunque esté en segundo plano, para independizarlo del proceso principal debemos agregar disown al final
Ejemplo:
```bash
wireshark & disown
[1] 65488
```

* ## kill
Puedes terminar un proceso existente si conoces su ID con el comando `kill ID`, reanudarlo en terminal con `kill -CONT ID`
Ejemplo:
```bash
❯ kill 65488
Exiting due to channel error.                                     
Exiting due to channel error.
Exiting due to channel error.
[GFX1-]: CompositorBridgeChild receives IPC close with reason=AbnormalShutdown
Exiting due to channel error.
Exiting due to channel error.
```
En caso de que no se termine puedes utilizar el -9 para finalizarlo de forma forzada:
```bash
❯ kill -9 65488
Exiting due to channel error.                                     
Exiting due to channel error.
Exiting due to channel error.
[GFX1-]: CompositorBridgeChild receives IPC close with reason=AbnormalShutdown
Exiting due to channel error.
Exiting due to channel error.
```