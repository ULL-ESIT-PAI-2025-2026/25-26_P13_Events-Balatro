# Práctica 11. Programación gráfica orientada a eventos. Curvas de Lissajous

### Factor de ponderación: 10
### Estimación de horas de trabajo para realizar la práctica: 5

### Objetivos
Los objetivos de esta tarea son poner en práctica:
* La arquitectura Modelo-Vista-Controlador (MVC)
* El uso del framework Bulma para dotar de estilos a una aplicación web simple.
* Desarrollo de animaciones gráficas en TS/JS
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
* La documentación de la aplicación incluirá un fichero README.md con la información correspondiente al
  proyecto desarrollado
* La estructura de directorios del proyecto será conforme a los requisitos establecidos en la asignatura
* Se acredita conocimiento y puesta en práctica de principios y buenas prácticas de programación orientada a objetos
* Saber corregir bugs en sus programas utilizando un depurador 
* Deben usarse estructuras de datos adecuadas para representar los diferentes elementos que intervienen en el problema
* Ser capaz de desarrollar programas simples en TypeScript en el entorno Linux de la VM de la asignatura usando
  `ts-node`
* Conocer y ser capaz de trabajar con el Framework
  [Bulma CSS](https://bulma.io/)
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

### Las curvas de Lissajous
Las 
[curvas de Lissajous](https://es.wikipedia.org/wiki/Curva_de_Lissajous)
son las curvas que recorre un punto sometido a un doble movimiento armónico simple en dos direcciones perpendiculares. 

La forma de la curva depende exclusivamente de la relación entre las frecuencias de los dos movimientos, 
`a/b` y de su desfase *phi*. 
Si `a/b = 1`, la curva es un segmento, una elipse o una circunferencia en función del desfase. 
Si este cociente es racional, la curva será cerrada.
Aunque para algunos valores de `a` y `b`pueda parecer abierta, como `a = b = 1` y `a = 3` y `b = 9` con desfase *phi* = 0, 
en realidad la curva se recorre dos veces, en un sentido y otro. 
En cambio si el cociente es irracional, la curva será abierta y densa en el cuadrado `[0, 1] x [0, 1]`, en el sentido de que 
pasa arbitrariamente cerca de cualquier punto contenido en él.
Consulte 
[esta
referencia](https://www.epsilones.com/paginas/articulos/articulos-005-lissajous.html)
si quiere conocer la historia de estas curvas.

Utilice
[esta página](https://academo.org/demos/lissajous-curves/)
interactiva para visualizar una curva cambiando interactivamente los parámetros de la misma.

En esta práctica se propone desarrollar en TypeScript una aplicación web en formato SPA
([Single Page Application](https://en.wikipedia.org/wiki/Single-page_application))
conforme al patrón MVC que muestre curvas de Lissajous en una interfaz web.

### Indicaciones de caracter general
El programa que desarrolle ha de ser orientados a objetos y utilizar una arquitectura MVC.
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

Utilice el depurador integrado en el navegador para confirmar que el flujo
de ejecución de su programa es el correcto.

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

### SonarQube
SonarQube es una plataforma de análisis estático de código que inspecciona de forma automática el código fuente 
para detectar bugs, vulnerabilidades de seguridad y *code smells*.
Su finalidad principal es mejorar la calidad y mantenibilidad del software: se integra en el flujo de desarrollo 
(CI/CD y a menudo en los IDEs) para revisar cada cambio de código, aplicar reglas de buenas prácticas y comprobar 
si el proyecto cumple ciertos criterios de calidad (*quality gates*) antes de permitir su integración o despliegue.

Utilice las explicaciones y ejemplos presentados en el 
[trabajo expuesto en clase](https://github.com/ULL-ESIT-PAI-2025-2026/2025-2026-pai-sonarqube-2025-2026-pai-sonarqube.git)
sobre SonarQube para instalar un servidor y utilizarlo para inspeccionar su código.
Valore si poner en práctica las recomendaciones que la plataforma le indica sobre los puntos débiles que
pudiera encontrar en su aplicación.

### Interfaz gráfica y especificaciones de la aplicación 
Tenga en cuenta las siguientes especificaciones a la hora de diseñar su programa:

Intente que su aplicación imite en la medida de lo posible el aspecto de
[esta otra](https://academo.org/demos/lissajous-curves/)
que se tomará como referencia.

El diseño del código HTML de esa página brinda una oportunidad para practicar aquellos elementos HTML que le resulten
necesarios.
Consiga, p. ej. que su página tenga secciones *header* y *footer*. 
En la cabecera coloque al menos sus apellidos y nombre. 
Utilice el footer para colocar información sobre la asignatura, titulación, etc.


Consiga que, siguiendo el ejemplo de personalización de Bulma para su adaptación a la imagen corporativa de
la ULL que se expuso en clase, personalice los estilos de todas sus páginas para que tengan el aspecto de las
*páginas ULL* al menos en cuanto a colores y tipografía.

La interfaz de usuario de la
[aplicación de referencia](https://academo.org/demos/lissajous-curves/),
en el panel de controles de la parte derecha contiene diferentes elementos (checkbox, campos de texto, *sliders*).
Utilice esta práctica para trabajar con ese tipo de elementos interactivos así como sus correspondientes
*listeners*.
Incorpore a su aplicación todos los que sea capaz de desarrollar y conocer y dote de estilo a esos elementos utilizando Bulma.
No utilice en su aplicación código CSS salvo el procedente de la carga de Bulma:

```css
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bulma@1.0.4/css/bulma.min.css">
```

Haga que el canvas junto con el área de entrada de datos ocupe la mayor parte del viewport de su navegador,
y puesto que su desarrollo es una *Single Page Application* todo el contenido de la página debiera visualizarse 
sin necesidad de desplazarse (*scroll*) ni horizontal ni verticalmente.

No utilice elementos CSS no estudiados en la asignatura.
No se requiere que dedique esfuerzo a aspectos relacionados con CSS en esta práctica.
Los estilos de CSS son aspectos que se estudiarán con mayor nivel de detalle en el futuro. 

La curva comenzará a dibujarse automáticamente una vez cagada la página en el navegador, sin esperar por ninguna interacción por parte del usuario.

Para la actualización del dibujo en el navegador se propone utilizar una aproximación similar a
la que se presentaba en la animación de una bola que se presentó en una práctica anterior.

La página que Ud. diseñe ha de contener el canvas de dibujo de las curvas (área cuadriculada en
la web de referencia y una columna con los campos de texto que permitan introducir valores de los parámetros
(columna derecha en la web de referencia).
En esa columna de la derecha puede Ud. utilizar campos de texto para introducir los valores de los parámetros
de la curva. 
Investigue asimismo cómo incluir *sliders* (a través del elemento `<input>` de HTML) para
modificar los valores de los parámetros usando el ratón.

Se propone además que su página muestre
* Texto explicativo de las curvas de Lissajous
* Enlaces a páginas de referencia que se hayan utilizado para realizar este trabajo.

## Referencias
* [Understanding the MVC Pattern with TypeScript](https://medium.com/@alessandro.traversi/understanding-the-mvc-pattern-with-typescript-an-in-depth-analysis-5a5d6f2d61a4)
* [Lissajous Curves](https://academo.org/demos/lissajous-curves/) An interactive demonstration of Lissajous curves
* [TypeDoc](https://typedoc.org/)
* [Google TypeScript Style Guide](https://google.github.io/styleguide/tsguide.html)
* [Google JavaScript Style Guide](https://google.github.io/styleguide/jsguide.html)
* [ESLint](https://eslint.org/)
* [JSDoc](https://jsdoc.app/)
* [PAI Code Examples](https://github.com/ULL-ESIT-PAI-2025-2026/PAI-class-code-examples.git)
