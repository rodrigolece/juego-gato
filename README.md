# juego-gato

En este repositorio presentamos una versión en Julia de un juego de Gato. Las ventanas y la interacción con los usuarios se manejan con la biblioteca [Gtk](https://github.com/JuliaLang/Gtk.jl).


## Instalación

El código corre en Julia 0.4, que se puede descargar precompilado [aquí](http://julialang.com/). El código fuente y las instrucciones para una instalación manual se encuentran [aquí](https://github.com/JuliaLang/julia/).

Para instalar Gtk, en el REPL de Julia ejecutamos:

```julia
Pkg.add("Gtk")
Pkg.build("Gtk")
```

La instalación toma un par de minutos.


## Estructura del repo

* `gato.jl` contiene el módulo con las funciones que definen las reglas del juego (la condición con la que un jugador gana, los turnos, etc).
* En `gui.jl` se define la interfaz gráfica.
* En `juego.jl` hacemos que la interfaz y el juego se comuniquen cuando los usuarios hacen click sobre los botones.


## Para jugar

Después de clonar este repositorio, desde la terminal se ejecuta:

```
$ julia juego.jl
```

Los jugadores "X" y "O" alternan turnos, haciendo click sobre los botones que son las casillas del juego. El juego termina cuando uno de los jugados alínea 3 piezas, o cuando hay un empate. Si un jugador hace click sobre una casilla ocupada, no sucede nada; tiene que escoger una casilla vacía.

[!](https://github.com/rodrigolece/juego-gato/blob/master/screen.tiff)


## Limitaciones del código

Queríamos que cuando los usuarios hicieran click sobre un botón, éste cambiara a "X" o "O" simulando las piezas del juego. Ésto se hace al cambiar la etiqueta del botón que se apretó. Sin embargo [un bug](https://github.com/JuliaLang/Gtk.jl/issues/161) de Gtk impide leer una etiqueta y después modificarla, así que no logramos concretar esta idea. Desafortunadamente, la interfaz sólo sirve para escoger las tiradas, pero el juego se tiene que seguir en la terminal.

Por otro lado, imprimer mensajes directamente en el juego también da un error que no supimos resolver. Por lo tanto, los mensajes también se imprimen en la terminal.


## Conclusión

El código que desarrollamos en su estado actual es impráctico; no funciona verdaderamente como una aplicación aislada y se tiene que usar junto con la terminal. Sin embargo, resolvimos casi todos los problemas y tenemos un juego funcional, con una interfaz gráfica en su mayoría funcional. Faltó muy poco para resolver los únicos dos problemas que quedan y tener una aplicación completa.
