# Práctica 12. Programación Gráfica Orientada a Eventos. El framework Bulma CSS. Balatro.

### Factor de ponderación: 10 
### Estimación de horas de trabajo para realizar la práctica: 10


### Objetivos
Los objetivos de esta tarea son poner en práctica:
* La arquitectura Modelo-Vista-Controlador (MVC)
* El uso del framework Bulma para dotar de estilos a una aplicación web simple.
* Programación orientada a eventos en TypeScript.
* Programación Gráfica en TypeScript usando la API Canvas.
* Metodologías y conceptos de diseño y Programación Orientada a Objetos en TypeScript.
* Principios y Buenas prácticas de programación Orientada a Objetos.
* Algunos de los patrones de diseño que se han estudiado en la asignatura.
* El uso de elementos HTML.

### Rúbrica de evaluacion del ejercicio
Se señalan a continuación los aspectos más relevantes (la lista no es exhaustiva)
que se tendrán en cuenta a la hora de evaluar esta práctica:
* Se valorará la realización de las diferentes tareas que se proponen
* El comportamiento del programa debe ajustarse a lo descrito en este documento
* Capacidad de la programadora de introducir cambios en el programa desarrollado
* Conocer y ser capaz de trabajar con el Framework
  [Bulma CSS](https://bulma.io/)
* La documentación de la aplicación incluirá un fichero README.md con la información correspondiente al
  proyecto desarrollado
* La estructura de directorios del proyecto será conforme a los requisitos establecidos en la asignatura
* Se acredita conocimiento y puesta en práctica de principios y buenas prácticas de programación orientada a objetos
* Saber corregir bugs en sus programas utilizando un depurador 
* Deben usarse estructuras de datos adecuadas para representar los diferentes elementos que intervienen en el problema
* Ser capaz de desarrollar programas simples en TypeScript en el entorno Linux de la VM de la asignatura usando
  `ts-node`
* Ser capaz de generar documentación para sus programas TS utilizando
  [TypeDoc](https://typedoc.org/)
  y de visualizar dicha documentación en un servidor web
* El alumnado debe ser capaz de resolver problemas tanto en JS como en TS en la plataforma Exercism subiendo sus soluciones a la misma
* Acreditar su capacidad para configurar y utilizar 
  [ESLint](https://eslint.org/)
y que es capaz de trabajar con la misma en Visual Studio Code
* Acreditar que conoce las etiquetas de 
  [JSDoc](https://jsdoc.app/)
* Se comprobará que el código que el alumnado escribe se adhiere a las reglas de las Guías de Estilo de Google
  para Javascript y/o TypeScript
* Todas las prácticas realizadas hasta la fecha, incluída la que se presenta para su evaluación, se encuentran alojadas en repositorios privados de GitHub.
* Acreditar que es capaz de editar ficheros de forma remota en su VM usando Visual Studio Code

### El juego Balatro
[Balatro](https://en.wikipedia.org/wiki/Balatro)
es un juego *roguelike* de construcción de mazos basado en 
[el póker](http://en.wikipedia.org/wiki/Poker), 
en el que en cada partida se juegan manos de póker para conseguir puntos 
(“chips”) suficientes en cada ronda, mientras se compran mejoras (especialmente *jokers*) que multiplican tu puntuación. 
Su interés viene de cómo se combinan manos, cartas modificadas y jokers para crear combos cada vez más explosivos dentro de una partida.

Cada partida se divide en niveles llamados *Small Blind*, *Big Blind* y *Boss Blind*.
Cada nivel exige alcanzar un número objetivo de chips jugando un número limitado de manos y descartes. 
Si la jugadora supera el objetivo antes de quedarse sin manos, gana ese blind y avanza en el juego.

Se juega con un 
[mazo de 52 cartas](https://en.wikipedia.org/wiki/Standard_52-card_deck)
de póker estándar (baraja francesa).
La baraja francesa está dividida en cuatro palos (*suits*), dos de color rojo y dos de color negro:

* ♠ Spades (picas).
* ♥ Hearts (corazones).
* ♦ Diamonds (diamantes).
* ♣ Clubs (tréboles).

Cada palo está formado por 13 cartas, de las cuales 9 son numerales y 4 literales. 
Se ordenan de menor a mayor "rango" de la siguiente forma: A, 2, 3, 4, 5, 6, 7, 8, 9, 10, J, Q, K. 
Las cartas con letras (figuras), se llaman Jack (J), Queen (Q), King (K) y Ace (A, *As*).
Dependiendo del juego, un As puede ser más alto que el Rey o más bajo que 2.

Si se quiere definir una clase para representar una carta de juego, 
es obvio cuáles deben ser los atributos **mínimos** imprescindibles: valor, palo y la imagen asociada con la carta.
El directorio `public/img` de este proyecto contiene ficheros gráficos correspondientes a 
todas las cartas de la baraja francesa, que puede Ud. usar en su desarrollo.
Siéntase libre de usar otras imágenes si lo prefiere.

En cada turno el jugador puede descartar algunas cartas para robar nuevas o seleccionar hasta cinco 
cartas para formar una 
[mano de póker](https://en.wikipedia.org/wiki/List_of_poker_hands)
(pareja, color, full, etc. o *One pair*, *Flush*, *Full House* de acuerdo a sus denominaciones en inglés). 

Las siguientes son las posibles manos en el póquer, en orden creciente de valor e indicando la puntuación
(“chips” y “multiplicador”) 
* *High Card*: la carta de mayor valor numérico. Chips: 5 Mult: 1 
* *Pair* (Pareja): dos cartas con el mismo valor. Chips: 10 Mult: 2 
* *Two Pair* (Doble par): dos pares de cartas con el mismo valor. Chips: 20 Mult: 2
* *Three of a kind* (Trío): tres cartas con el mismo valor. Chips: 30 Mult: 3 
* *Straight* (Escalera): cinco cartas con valores en secuencia (los ases pueden ser altos o bajos, 
  así que el Ace-2-3-4-5 es una escalera y también lo es el 10-Jack-Queen-King-Ace, pero el Queen-King-Ace-2-3 no lo es). Chips: 30 Mult: 4
* *Flush* (Color): cinco cartas con el mismo palo. Chips: 35 Mult: 4 
* *Full House* (Full): tres cartas con un valor, dos cartas con otro. Chips: 40 Mult: 4
* *Four of a Kind* (Poker): cuatro cartas con el mismo valor. Chips: 60 Mult: 7 
* *Straight Flush* (Escalera real): cinco cartas en secuencia (como se definió anteriormente) y con el mismo palo. Chips: 100 Mult: 8

Cada mano jugada se traduce en una puntuación según el tipo de jugada (base de “chips” y “multiplicador”) 
más el valor de las cartas individuales; la puntuación total se acumula contra el objetivo de chips del nivel actual.

En cada blind el jugador tiene un número fijo de manos que puede jugar y un número de descartes; 
si los “chips” acumulados alcanzan el objetivo, el nivel se considera superado y se pasa al siguiente.
Si el juagador acaba sus manos sin alcanzar el objetivo, la partida termina. 

Utilice la aplicación
[Mini Balatro](https://alu0101549491.github.io/TFG-Fabian-Gonzalez-Lence/3-MiniBalatro/)
para jugar y sobre todo, conocer el juego.
Mini Balatro está siendo desarrollada por D. Fabián G. Lence, estudiante del grado en informática en el marco
de su Trabajo Fin de Grado.

En la aplicación el botón *Hand Info* muestra en pantalla los tipos de manos del póker que utiliza así como el
valor de cada una de ellas, de modo que para empezar, basta con saber reconocer las jugadas básicas de póker 
y tratar de hacer siempre la mano más valiosa con las cartas que se tiene.

En esta práctica se propone desarrollar en Vanilla TypeScript una primera aproximación simplificada del Blatro a través de una
aplicación web web en formato SPA (*Single Page Application*) conforme al patrón MVC.

### Indicaciones de caracter general
El programa que desarrolle ha de ser orientado a objetos y utilizar una arquitectura MVC.
Ponga en práctica en su desarrollo los fundamentos, principios y buenas prácticas de la OOP así como los
conocimientos que haya adquirido en el uso de patrones de diseño.

Utilice un fichero distinto para el código de cada una de las clases que intervienen en su programa.

Encapsule las clases en módulos que exporten la correspondiente clase a quien precise usarla.

La estructura de directorios de su proyecto de práctica debe ser conforme con la establecida para las prácticas de PAI.

Configure adecuadamente ficheros `package.json` y `tsconfig.json` en el directorio raíz de su ejercicio 
que permitan la instalación de las dependencias de su proyecto.

Actualice el fichero `README.md` con la información que considere relevante de su proyecto de práctica y haga que ese fichero
sea la primera página de la documentación (TypeDoc) de la práctica.

Haga que en el elemento `title` del código HTML de todas las páginas web de su poroyecto figure su nombre y apellidos.

Utilice el depurador integrado en el navegador para confirmar que el flujo de ejecución de su programa es el correcto.

No intente desarrollar su aplicación en un único paso.

Previo al desarrollo, realice un diseño de su aplicación identificando las diferentes clases que
intervienen en el programa. 
Utilice lápiz y papel para hacer un esquema de las relaciones entre las diferentes clases.

Después de esa planificación inicial, trabaje mediante sucesivos refinamientos de una primera aproximación.
También puede resultarle conveniente realizar pequeñas aplicaciones auxiliares que le sirvan para comprobar y
aprender el funcionamiento de algún aspecto concreto de la aplicación.

Cuando finalice su aplicación, utilice 
[Mermaid.js](https://mermaid.js.org/), 
[Lucidchart](https://www.lucidchart.com/pages) o cualquier otra herramienta que conozca para trasladar sus
diseños en papel a un diagrama en formato digital que pueda mostrar a través de una web.

La visualización de la ejecución del programa y su interfaz gráfica se desarrollará a través de una página web alojada
en la máquina IaaS-ULL de la asignatura (puede utilizar también si lo desea la extensión *Live View* de VSC).

Configure en el directorio `/public` de su práctica, la página `index.html`, 
que servirá de "página índice" tanto para su aplicación como para los ejercicios de la sesión de evaluación.
Enlace también en esa página tanto la página que contiene la documentación (Typedoc) de su proyecto
como otra que mostrará el diagrama UML de las clases que intervienen en su programa.

### Interfaz gráfica y especificaciones de la aplicación 
Tenga en cuenta las siguientes especificaciones a la hora de diseñar su programa:

Aunque este documento está escrito en español, se propone que los identificadores 
que se usen en el código TypeScript utilicen la terminología en inglés para las entidades que ha de 
modelar en su programa: cartas (*cards*), mazo de cartas (*deck*), nombres de los palos (*suits*), etc.

Intente que su aplicación imite en la medida de lo posible el aspecto y funcionalidades de
[Mini Balatro](https://alu0101549491.github.io/TFG-Fabian-Gonzalez-Lence/3-MiniBalatro/)
que se tomará como referencia.

Su página debería dividirse en las 5 secciones que muestra la aplicación de referencia:
* Bloque 1: Level, Money, Round, Deck
* Bloque 2: Jokers
* Bloque 3: Objetivo de puntos
* Bloque 4: Current Hand
* Bloque 5: Previsualización de la puntuación (*Score Preview*)
* Bloque 6: Control e información del juego

Utilice todos aquellos elementos HTML que le resulten necesarios y use
Bulma para dotar de estilo a esos elementos.
Haga que el color de fondo de su página sea el color violeta característico de las “páginas ULL”, en lugar del
color azul oscuro que muestra la aplicación de referencia.
Utilice asimismo la *tipografía ULL* para su aplicación.
No utilice en su aplicación código CSS salvo el procedente de la carga de Bulma.

Su aplicación solo implementará el primer nivel (*Small Blind*) del juego.
* Se reparten 8 cartas al inicio del juego
* El jugador selecciona 1–5 cartas y elige:
  * Jugar mano (máximo 3 veces por nivel), botón `Play Hand`
  * Descartar, botón `Discard` (máximo 3 veces por nivel, las cartas se reponen del mazo)
* Si acumula más puntos que el objetivo (300) pasa el nivel
* Si agota las 3 manos sin alcanzar el objetivo, el juego finaliza

Su aplicación ha de incluir los mismos botones y textos que la aplicación de referencia, aunque no todos 
esos botones y textos estarán dotados de funcionalidad o serán actualizados:
* Bloque 1. Con cada jugada o descarte se actualizará el texto de la parte superior derecha con el número de cartas restantes en el mazo.
* Bloque 2. Se mostrarán los *slots* vacíos con una apariencia que queda a su elección.
* Bloque 3. Se actualizará la información de objetivo y puntuación alcanzada.
* Bloque 4. Se mostrarán las 8 cartas repartidas al inicio, que se resaltarán de algún modo que queda a
  su elección, al ser seleccionada por el usuario.
* Bloque 5. Mostrará la mano correspondiente a la selección del usuario así como el valor de la misma.
* Todos los botones/textos del Bloque 6 han de ser funcionales (actuarán como corresponde o mostrarán el texto
  correspondiente) salvo *Hand Info* que no tendrá efecto.

Posiblemente su aplicación necesitará métodos `hasPair()`, `hasTwopair()`, `hasThreeOfaKind()` etc. 
que indican si la mano seleccionada por el jugador cumple o no el correspondiente criterio. 
Asimismo necesitará un método que determine la clasificación 
de mayor valor para una mano y establezca el valor de la mano (“chips”) en consecuencia. 
Por ejemplo, una mano de 5 cartas podría contener un trío y un par; debería ser etiquetada como “Three of a
kind” (trío) puesto que esa es la jugada de mayor valor.

Se da libertad al alumnado para implementar como crea oportuno aquellos comportamientos que no estén
descritos en esta especificación o bien resulten difíciles de realizar como se hace en la aplicación de
refeerencia.

Tenga en cuenta que el objetivo del proyecto es practicar en una aplicación concreta los conceptos estudiados
en la asignatura y no que su aplicación replique exactamente la de referencia.

## Referencias
* [Balatro](https://en.wikipedia.org/wiki/Balatro)
* [Poker](http://en.wikipedia.org/wiki/Poker)
* [Bulma](https://bulma.io/)
* [TypeDoc](https://typedoc.org/)
* [Google TypeScript Style Guide](https://google.github.io/styleguide/tsguide.html)
* [Google JavaScript Style Guide](https://google.github.io/styleguide/jsguide.html)
* [ESLint](https://eslint.org/)
* [JSDoc](https://jsdoc.app/)
* [PAI Code Examples](https://github.com/ULL-ESIT-PAI-2024-2025/PAI-class-code-examples)
