# Tema 1. Paradigmas de la computación.

**Contenido:**

- Abstracción en los lenguajes de programación (sección 1.1)
- Paradigmas de computación (sección 1.2)

> Louden: "Si la forma en que nos comunicamos influye en la forma en que pensamos y viceversa, entonces la forma en que programamos influye en lo que pensamos sobre los programas y viceversa"



La evolución de los lenguajes de programación se ha organizado en cinco generaciones:

1. En la **primera generación** se incluyen los lenguajes máquina, en los que los datos y las operaciones sobre ellos se describen mediante ceros y unos.
2. La **segunda generación** es la que incluye a los lenguajes ensambladores, cuya traducción a lenguaje máquina es muy sencilla.
3. La **tercera generación** es la que incluye a los lenguajes de alto nivel como Pascal, Fortran, C o java. Se denominan de alto nivel porque están muy alejados de la máquina pero muy cercanos a los programadores.
4. La **cuarta generación** agrupa a lenguajes de propósito específico, como SQL, etc.
5. La **quinta generación** se incluyen lenguajes en los que se especifica más el problema a resolver que la solución del problema. dentro de esta generación, encontramos lenguajes como Prolog o Haskell.



## 1.1. Abstracción en los lenguajes de programación.

- La **abstracción** en los lenguajes de programación se refiere a la ***abstracción de los datos*** que resume sus propiedades y la ***abstracción del control*** que resume las propiedades de la transferencia de control, esto es, de la modificación de la estrategia de ejecución de un programa en una situación determinada.

### 1.1.1. Abstracción de Datos

- La **abstracción de datos básicas** se refieren a la representación interna de los datos de **tipo atómico** que ofrece el lenguaje, junto a sus operaciones estándar.

- Otro tipo de abstracción básica es el uso de nombres simbólicos para referenciar las localizaciones de memoria que contienen los programas. Esto se conoce como **variable**.

- Las **abstracciones de datos estructuradas** son el mecanismo de abstracción para colecciones de datos. Una estructura típica es el **array** que reúne datos como una secuencia de elementos.

  ```
  int tabla[7];
  ## En muchos lenguajes se puede crear una definición de tipo. A estos tipos se les denomina tipos estructurados.
  typedef int Mitabla[7];
  ```

- Las **abstracciones de datos unitarias** se refieren a la agrupación, como una única unidad, de datos y operaciones sobre ellos. Introducen el concepto de **encapsulado de datos** u ocultación de información, mecanismo muy útil para reunir código relacionados entre sí en localizaciones específicas dentro del programa, ya sea en forma de archivos por separado o como estructuras del lenguaje separadas dentro de un archivo. Estas abstracciones unitarias se asocian a menudo con los tipos abstractos de datos, separando las operaciones que se pueden realizar con los valores de dicho tipo de datos (**interfaz**) de su implementación interna.

  Las clases de los lenguajes orientados a objetos son un mecanismo conceptualmente mas cercano a las abstracciones unitarias, pero también a las abstracciones estructuradas, ya que ofrecen un encapsulamiento de datos y tienen algunas características de los módulos o paquetes.

  Características de la abstracción:

  - Capacidad de **reutilización** de la misma en programas diferentes a través de bibliotecas.
  - **Interoperabilidad** o facilidad de combinación de abstracciones al proporcionar convenciones estándar para sus interfaces. 



### 1.1.2. Abstracciones de Control

- Las **abstracciones básicas de control** son sentencias individuales que permiten modificar (directa o indirectamente) el control del flujo de la ejecución de un programa. Ej: sentencia de asignación o el *goto* de Fortran.

- Las **abstracciones de control estructuradas** agrupan sentencias más simples para crear una estructura con un propósito común que permite gobernar la ejecución del programa. Ej: bucles o las sentencias condicionales.

  ```haskell
  raices x
    | numSoluciones x == 0 -> []
    | numSoluciones x == 2 -> [sqrt(x), -aqrt(x)]
  ```

  Otro mecanismo es el **subprograma**. Necesita una declaración, con un nombre y un conjunto de acciones a realizar que se abstraen bajo dicho nombre. Una llamada a un subprograma es un mecanismo más complejo que las sentencias condicionales o los bucles, puesto que requiere el almacenamiento del estado del programa ene l punto de llamada en el entorno de ejecución.

  Un mecanismo de abstracción muy cercano al de subprograma es el de **función**,que es un subprograma que devuelve un resultado tras ser invocado.

  La diferencia más importante entre procedimientos y funciones es que las funciones se corresponden con la abstracción matemática de función, por lo que pueden entenderse independientemente del estado del entorno de ejecución.

- Las **abstracciones de control de tipo unitario** permiten agrupar una colección de subprogramas como una unidad en sí misma e independiente del programa. 

  Esencialmente son idénticas a las abstracciones de datos unitarias. Simplemente varía el enfoque, que en esta ocasión se orienta más a las operaciones que a los datos. Mantienen las propiedades de las abstracciones de datos unitarias como la reutilización mediante la creación de bibliotecas.

-  **Mecanismos de programación en paralelo**. Abstracción de control difícil de clasificar.

  

  *(**) Abstracciones de los Lenguajes de Programación*

| Abstracción  | De Datos                 | de Control                        |
| ------------ | ------------------------ | --------------------------------- |
| Básica       | tipos atómicos variables | asignación goto                   |
| Estructurada | tipos estructurados      | bucles condicionales subprogramas |
| Unitaria     | módulos paquetes         | módulos paquetes                  |

Un lenguaje de programación sólo necesita describir computaciones, entonces sólo necesita mecanismos suficientes para describir todos los cálculos que pueden llevar a cabo una **máquina de Turing**, puesto que cualquier máquina de Turing puede ejecutar cualquier cálculo conocido en un ordenador. Un lenguaje de este tipo se conoce como lenguaje completo de Turing, debe incluir variables enteras y aritméticas, así como la ejecución de sentencias de forma secuencial, incluyendo sentencias de asignación, condicionales(if) y bucles (while).



## 1.2. Paradigmas de computación

- **Modelo de computación Von Neumann.** El programa se almacenara en la máquina antes de ejecutarse y a su vez:

  - La ejecución secuencial de instrucciones.
  - El uso de variables para la representación de las posiciones de memoria.
  - El uso de la asignación para cambiar el valor de las variables. 

  Estos lenguajes se conocen como **lenguajes imperativos**, porque sus instrucciones representan ordenes. También se les ha denominado **procedurales**. 

  **Paradigma imperativo.**

- **Paradigma funcional**, que usa la noción de función según se plantea en el **lambda cálculo**.

- **Paradigma lógico**, que se basa en la lógica simbólica.

- **Programación declarativa** se denomina al grupo formado por la programación funcional y la lógica. En este tipo, las propiedades se declaran y no se especifican las secuencias de ejecución. También se les domina **lenguajes de muy alto nivel** o de **quita generación**. 

  

### 1.2.1. Programación orientada a objetos.

- Este paradigma se basa en la idea de que un objeto se puede describir como una colección de posiciones de memoria junto con todas las operaciones que pueden cambiar los valores de dichas posiciones.
- En la mayoría de los **lenguajes orientados a objetos**, los objetos se agrupan en clases que representan a todos los que tienen las mismas propiedades. Estas clases se definen mediante declaraciones parecidas a las de los tipos estructurados. Tras la declaración de una clase, se pueden crear objetos concretos a partir de la misma, mediante la instanciación de la clase.



### 1.2.2. Programación funcional

- La computación en el paradigma funcional se fundamenta en la evaluación de funciones o en la aplicación de funciones a valores conocidos, por lo que también se denominan **lenguajes aplicativos**. El mecanismo básico es la evaluación de funciones, con las siguientes características:
  - La transferencia de valores como parámetros de las funciones que se evalúan.
  - La generación de resultados en forma de valores devueltos por las funciones.
- Este proceso no involucra de ningún modo a la asignación de una variable a una posición de memoria. tampoco las operaciones repetitivas se representan por ciclos, sino mediante las **funciones recursivas**.

```haskell
### máximo común divisor (gcd)
gcd u v
  | v == 0 -> u
  | otherwise -> gcd v (mod u v)
```



### 1.2.3. Programación lógica

- En un lenguaje de programación lógica, un programa está formado por un conjunto de sentencias que describen lo que es *verdad* o conocido con respecto a un problema, en vez de indicar la secuencia de pasos que llevan al resultado. No necesita de abstracciones de control condicionales ni de ciclos ya que el control lo aporta el modelo de inferencia lógica que subyace.

```prolog
gcd(U, 0, U)
gcd(U, V, X) :- not (V = 0),
                Y is U mod V,
                gcd(V, Y, X).
```

```prolog
gcd(18,8,X)
```

- En prolog un programa es un conjunto de sentencias, denominadas cláusulas. 
- A diferencia de las funciones en la programación funcional, Prolog requiere de variables para representar los valores de las funciones, aunque no representan tampoco posiciones de memoria.



