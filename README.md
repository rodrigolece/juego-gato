# juego-gato

En este repositorio presentamos una versión en Julia de un juego de Gato. Las ventanas y la interacción con los usuarios se hace con la biblioteca [Gtk](https://github.com/JuliaLang/Gtk.jl).

## Instalación

El código corre en Julia 0.4, que se puede descargar precompilado [aquí](http://julialang.com/). El código fuente y las instrucciones para una instalación manual se encuentran [aquí](https://github.com/JuliaLang/julia/).

Para instalar Gtk, desde el REPL de Julia basta ejecutar:

```julia
Pkg.add("Gtk")
Pkg.build("Gtk")
```

Esto va a tomar un par de minutos.

## Estructura del repo

* `gato.jl` contiene el módulo con las funciones que le dan forma al juego.
* `gui.jl` define la interfaz gráfica.
* En `juego.jl` la interfaz le habla al juego, a través de una función que se ejecuta cuando los usuarios hacen click sobre los botones.


## Limitaciones del código

Queríamos que cuando los usuarios hicieran click sobre un botón, éste cambiara a "X" o "O" simulando las piezas del juego. Ésto se hace al cambiar la etiqueta del botón que se apretó. Sin embargo [un bug](https://github.com/JuliaLang/Gtk.jl/issues/161) de Gtk impide leer una etiqueta y después modificarla, así que no logramos concretar esta idea. Desafortunadamente, a lo más que llegamos es a que la interfaz sólo sirve para escoger las tiradas, pero el juego se tiene que seguir en la terminal.

Por otro lado, los mensajes directamente en el juego también dan un error que no supimos resolver, así que éstos también se tienen que imprimir en la terminal.

## Conclusión

El código que desarrollamos en su estado actual es impráctico; no funciona verdaderamente como una aplicación aislada y se tiene que usar junto con la terminal. Sin embargo, resolvimos casi todos los problemas y tenemos un juego que funciona con una interfaz gráfica que funciona. Falta muy poco para resolver los únicos dos problemas que quedan y tener una aplicación completa.
