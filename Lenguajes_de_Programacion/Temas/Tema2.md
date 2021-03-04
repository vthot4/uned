# Principios de diseño de los lenguajes

**Contenido:**

- Descripción de los lenguajes de programación (sección 1.3)
- Diseño de los lenguajes de programación (sección 1.4)

## 2.1. Descripción de los lenguajes de programación

- Los lenguajes de programación deben describirse de manera formal, completa y precisa.
- Los elementos fundamentales para la definición de un lenguaje de programación son los siguientes:
  
  - El **léxico** o conjunto de las "palabras"  o unidades léxicas que son las cadenas de caracteres significativas del lenguaje, también denominadas tokens.
  
    También son unidades léxicas los **identificadores**, los símbolos especiales de **operadores**, como "+" o "<=" y los símbolos de puntuación como el punto y como o el punto. (";" ó ".")
  
  - La **Sintaxis** o estructura es la descripción de los diferentes componentes del lenguaje y de sus combinaciones posibles. Para ello se utilizan las **gramáticas libres de contexto**, un estándar aceptado universalmente.
  
  - **La semántica** expresa los efectos de la ejecución en un contexto determinado.
  
    Entre los sistemas de notación para definiciones semánticas formales se encuentran: 
  
    - La **semántica operacional**. El significado de una construcción es una descripción de su ejecución en una máquina hipotética.
  
    - La **denotacional**. Asigna objetos matemáticamente a cada componente del lenguaje para que modele su significado.
  
    - **Axiomática**. Modela el significado con un conjunto de axiomas que describen a sus componentes junto con algún tipo de inferencia del significado.
  
      

### 2.1.1. Traducción de los programas para su ejecución.

- Para la ejecución de los programas escritos en un lenguaje de programación, es necesario disponer de un traductor, un programa que acepta como entrada los programas del lenguaje y los ejecuta o transforma en una forma adecuada para su ejecución. En el primer caso al traductor se le denomina **intérprete** y en el segundo **compilador.**
- En el caso del intérprete la ejecución de un programa se realiza en un paso: con los datos necesarios y el programa como entrada, el intérprete produce la ejecución del programa sobre esos datos. La compilación, por su parte, es un proceso de dos pasos: el programa original o código fuente de la entrada se convierte en un nuevo programa o **código objeto**, que es el que puede ser ejecutado sobre los datos que se desee.
- El lenguaje del código objeto debe ser a su vez traducido por un **ensamblador** en un nuevo código objeto, que será linkado con otros códigos objeto, cargado en las localizaciones de memoria adecuadas y finalmente ejecutado. Otro caso posible es aquel en el que un **pseudo-intérprete** no produce un programa objetivo, sino que traduce el programa fuente a un lenguaje intermedio que posteriormente es interpretado.

- En ocasiones un lenguaje está definido por el comportamiento de un intérprete o compilador en particular, denominado **traductor definicional**, aunque sea una mala práctica.

- Las fases que tanto un intérprete como un compilador deben llevar a cabo son:

  - Un **analizador léxico** debe identificar los tokens del programa.
  - Un **analizador sintáctico** o gramatical identifica las estructuras correctas que definen las secuencias de tokens.
  - Un **analizador semántico** asigna el significado de forma suficiente para su ejecución o la obtención del programa objetivo.

  Estas fases exigen el mantenimiento de un entorno o **ambiente de ejecución**, que  administra el espacio de memoria para los datos del programa y registra el avance de la ejecución.

- Cualquier lenguaje de programación puede disponer de un intérprete y/o un compilador. Los intérpretes son menos eficientes que los compiladores ya que estos permiten la **optimización del código** en análisis previos de la ejecución del programa.

- Las propiedades del lenguaje que pueden ser determinadas antes de su ejecución o **propiedades estáticas** y las que no, llamadas **propiedades dinámicas**. Las propiedades estáticas típicas son las relacionadas con el léxico y la sintaxis de un lenguaje de programación. 

  En un lenguaje que sólo tenga asignación estática, es decir una posición de memoria fija para las variables durante toda la ejecución, puede utilizar un **ambiente totalmente estático** y en caso contrario usar un **ambiente totalmente dinámico**. Sin embargo  hay posiciones intermedias, como es el caso de un **ambiente basado en pilas** que tiene aspectos estáticos y dinámicos.

  Las propiedades del lenguaje que pueden ser determinadas antes de su ejecución o **propiedades estáticas** y las que no, llamadas **propiedades dinámicas**. Las propiedades estáticas típicas son las relacionadas con el léxico y la sintaxis de un lenguaje de programación. 

- Un último aspecto a considerar con respecto a la traducción es el relacionado con la **recuperación de errores** que favorece la **fiabilidad**, una propiedad importante del traductor. Durante la traducción, el traductor se encuentra errores que debe indicar mediante mensajes de error apropiados y que, dependiendo de la complejidad inherente al error, puede resolver o al menos recuperar para poder seguir con la traducción.

  Los errores se clasifican de acuerdo con la fase de traducción en que se encuentran:

  - Los **errores léxicos** ocurren durante la fase de análisis léxico y suelen estar limitados al uso de caracteres ilegibles. 
  - Los **errores sistácticos** se refieren a tokens que faltan en expresiones o expresiones mal formadas. 
  - Los **errores semánticos** pueden ser estáticos, detectados antes de la ejecución, como tipos incompatibles o variables no declaradas, o errores dinámicos, detectados durante la ejecución como una división por cero.
  - Los **errores lógicos** producen un comportamiento erróneo o no deseable del programa.

La **pragmática** de los lenguajes de programación se ocupa de aspectos como la especificación de mecanismos para activación o deshabilitación de opciones de optimización, depuración y otras facilidades pragmáticas que suelen incluirse en los traductores.



## 2.2. Diseño de los lenguajes de programación.

- El objetivo principal de la abstracción en el diseño de los lenguajes de programación es el control de la **complejidad**. 
- Las características pragmáticas del diseño de un lenguaje de programación deben ser conocidas tanto para diseñar nuevos lenguajes como para elegir el lenguaje de programación adecuado. El programador debe conocer los principios de diseño prioritarios durante el diseño de cada lenguaje de programación para saber elegir.



### 2.2.1. La eficiencia

- El diseño debe permitir al traductor de generación de **código ejecutable** eficiente, también conocido como **optimizabilidad**.

- La eficiencia se organiza en tres principios: eficiencia de traducción, de implementación y de programación.

  - La **eficiencia de traducción** estipula que el diseño del lenguaje debe permitir el desarrollo de un traductor eficiente y de tamaño razonable. 

    Hay traductores que se diseñan para que los programadores omitan la verificación de errores con reglas muy difíciles de verificar en tiempo de traducción, lo que influye negativamente en otro principio de diseño: la fiabilidad.

  - La **eficiencia de implementación** es la eficiencia con la que se puede escribir un traductor, que a su vez depende de la complejidad del lenguaje.

  - La **eficiencia de la programación** está relacionada con la rapidez y la facilidad para escribir programas o **capacidad** expresiva del lenguaje. La capacidad expresiva de un lenguaje se refiere a la facilidad para escribir procesos complejos de forma que el programador relacione de manera sencilla su idea con el código.

    Relacionado con este concepto, se encuentra el de **Azúcar sintáctico**, termino acuñado para describir aquellas estructuras sintácticas que no añaden expresividad al lenguaje, pero que facilitan la escritura de los programas ofreciendo alternativas para que el programador pueda escoger. Un ejemplo puede ser las diferentes versiones de bucles que ofrecen los lenguajes de programación.

  - Finalmente indicar que la fiabilidad exige de tiempo adicional para pruebas, recuperación de errores o agregación de nuevas características (capacidad de mantenimiento) y depende tanto de los recursos disponibles como de su consumo.

### 2.2.2 La regularidad.

- La **regularidad** de un lenguaje de programación es un principio que se refiere al comportamiento de la características del lenguaje. Se subdivide en tres propiedades:
  - La **generalidad** se consigue cuando el uso y la disponibilidad de los constructores no están sujetas a casos especiales y cuando el lenguaje incluye solo a los constructores necesarios y el resto se obtienen por combinaciones de constructores relacionados.
  - La **ortogonalidad** (o independencia) ocurre cuando los constructores del lenguaje pueden admitir combinaciones significativas y en ellas, la interacción entre los constructores o con el contexto, no provocan restricciones ni comportamientos inesperados. Esto implica que los constrictores del lenguaje no deben comportarse de manera diferente en contextos diferentes, por lo que las restricciones que dependen del contexto no son ortogonales.
  - La **uniformidad** se refiere a que lo similar se ve similar y lo diferente, diferente, lo que implica la consistencia entre la apariencia y el comportamiento de los constructores.

- Finalmente indicar que las no uniformidades también pueden considerarse no ortogonalidades pues ocurren en contextos particulares y pueden considerarse interacciones entre constructores.

### 2.2.3. Principios adicionales.

Principios adicionales del diseño del lenguaje de programación que ayudan a definir un buen diseño o a elegir el mejor lenguaje para un escenario o tarea concreta:

1. **Simplicidad**. Es un principio que se refiere sintácticamente a que cada concepto del lenguaje se presente de una forma única y legible y semánticamente que contiene el menor número posible de conceptos y estructuras con reglas sencillas de combinación.

2. **Expresividad**. Es la facilidad con la que un lenguaje de programación permite expresar procesos y estructuras complejas. En los lenguajes declarativos tanto los datos como el programa pueden cambiar durante su ejecución, aspecto muy útil en situaciones complejas, como cuando el tamaño o los datos pueden ser desconocidos inicialmente. Los lenguajes orientados a objetos son muy expresivos.

3. **Extensibilidad**. Es la propiedad con la posibilidad de añadir nuevas características a un lenguaje, como nuevos tipos de datos o nuevas funciones a la biblioteca. 

   Otro aspecto importante es la modularidad, es decir, la capacidad de disponer de bibliotecas y agregar nuevas. La modularidad se corresponde también con la posibilidad de dividir en partes independientes que puedan enlazarse para su ejecución. Estos módulos puede ser reutilizados o cambiados sin que afecten al resto del programa (escalabilidad).

4. **Capacidad de restricción**. La capacidad de restricción se refiere a la posibilidad de que un programador utilice solo un subconjunto de constructores mínimo y por lo tanto solo necesite un conocimiento parcial del lenguaje. Esto ofrece dos ventajas: el programador no necesita aprender todo el lenguaje y, por otra parte, el traductor puede implementar sólo el subconjunto determinado porque la implementación para todo el lenguaje sea muy costosa e innecesaria.
   Otro aspecto relacionado con la capacidad de restricción es la **eficiencia**: porque un programa no utilice ciertas características del lenguaje, su ejecución no debe ser más ineficiente.
   Otra ventaja que permite la capacidad de restricción o la existencia de subconjuntos del lenguaje es el **desarrollo incremental** del mismo.

5. **Consistencia entre la notación y las convenciones**. un lenguaje debe incorporar notaciones y cualquier otra característica que ya se hayan convertido en estándares. Si estos aspectos estándar quedan perfectamente reconocibles, se facilita a los programadores experimentados el uso del lenguaje.

6. **Precisión**. es la propiedad que exige una definición precisa del lenguaje, de forma que el
   comportamiento de los programas sea predecible. La precisión del lenguaje ayuda tanto a la
   fiabilidad de los programas, como a la confianza en los traductores por que el programa se
   comporta igual en cualquier máquina (**portabilidad**).

7. **Portabilidad**. La portabilidad se consigue si la definición del lenguaje de programación es independiente de una máquina en particular.

8. **Seguridad**. Este principio pretende evitar los errores de programación y permite su descubrimiento. Por lo tanto la seguridad esta muy relacionada con la fiabilidad y la precisión. Sin embargo, la seguridad compromete a la capacidad expresiva del lenguaje y a su concisión, pues se apoya en que el programador especifique todo lo que sea posible en el código (para evitar errores).

   El equilibrio entre seguridad por una parte y expresividad y generalidad por otra, hacen difícil encontrar una solución acertada para todas las necesidades. Un caso positivo es Haskell que siendo un lenguaje funcional, permite objetos de múltiples tipos, no requiere declaraciones de variables y sin embargo dispone de verificación estática de tipos.

9. **Interoperabilidad**. Facilidad que tienen diferentes tipos de ordenadores, redes, sistemas operativos, aplicaciones o sistemas para trabajar conjuntamente de manera efectiva, sin comunicaciones previas, para intercambiar información útil y con sentido. Existen tres tipos:

   - **Interoperabilidad semántica**. Cuando los sistemas intercambian mensajes entre sí, interpretando el significado y el contexto de los datos.
   - **Interoperabilidad sintáctica**. Cuando un sistema lee datos de otro, mediante una representación compatible.
   - **Interoperabilidad estructural**. Cuando los sistemas pueden comunicarse e interactuar en ambientes heterogéneos.