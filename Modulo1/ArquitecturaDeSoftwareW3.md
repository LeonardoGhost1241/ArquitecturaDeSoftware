# Modularidad (Cohesion, acoplamiento, Connascencia)

Como  sabemos el software tiende a la entropia, por lo que:
- Debe agregarse energia de manera consciente para mantener el orden


## Modularidad
**Modulo**
Es una parte indispensable del todo que se utiliza para la construccion de estructuras mas complejas
- Es la agrupacion logica de codigo
- Agrupacion de logica de grupos de codigo
- el arquitecto debe ser consciente de la agrupacion puede identificar el acoplamiento, cohesion, etc.

#### Modularidad en lenguajes de programacion
En los lenguajes modernos, se tiene la importancia porel agrupamiento de codigo.

Por ejemplo en java:
- Packages
- Ruta fisica coincidente con paquete, para evitar duplicidad
- Niveles de acceso y encapsulacion 

Medidas de la modularidad
Medidas en:
- Cohesion
- Acoplamiento
- Co-nacimiento (connascense)


## Cohesion
"Es una medida de la fuerza de relacion entre los elementos internos de un modulo, clase o componente. Indica que tan enfocadas y unidas estas las responsibilidades dentro de una unidad de codigo, siendo preferible una **alta cohesion**(funcionalidad unica) para facilitar el mantenimiento, la reutilizacion y la comprension del sistema"

Aspectos clave de la cohesion
**Alta Cohesion(Objetivo):**Los elementos del modulo trabajan juntos para una sola tarea o proposito bien definido, reduciendo la complejidad

**Baja Cohesion(A evitar):**El modulo realiza multiples tareas no relacionadas entre si, lo que dificulta el mantenimiento

* Medida en que las partes de un modulo deben estar contenidas dentro del mismo modulo
* Cuando todas las partes se relacionan unas con otras para funcionar, deberian estar empaquetadas todas juntas
* Intenta dividir un modulo cohesivo, resultara en incrementar el acoplamiento

![alt text](image-20.png)


#### Funcional
Cada parte del módulo se relaciona una con otra, y el módulo contiene lo esencial para  ser completamente funcional.
Las partes de un módulo se agrupan porque
todas contribuyen a una única tarea bien
definida del módulo

- Es el grado de cohesion ideal
- Todos los elementos se centran en un solo proposito
- Modulo Facil de entender, reutilizable y claro


![alt text](image-21.png)


#### Secuencial
Dos módulos interactúan de tal forma que la
salida de uno se convierte en la entrada del otro

Las partes de un módulo se agrupan porque la
salida de una parte es la entrada de otra parte, como una línea de ensamblaje

- Conexion entre elementos del otro modulo
- Necesita operar uno despues del otro

![alt text](image-22.png)

#### Comunicacional
Dos módulos forman una cadena de
comunicación, donde cada uno maneja datos
para contribuir a la salida esperada.

Las partes de un módulo se agrupan porque
operan sobre los mismos datos (por ejemplo, un módulo que opera sobre el mismo registro de información).

- Las funciones se relacionan por que todas trabajan con la misma estrvcutura de datos
- No necesariamente realizan la misma tarea, pero comparten el mismo conjunto de informacion

![alt text](image-23.png)

#### procedimental
Dos módulos deben ejecutarse en un orden
particular y específico.

Las partes de un módulo se agrupan porque
siempre siguen una determinada secuencia de
ejecución.

- representan secuencia de asos
- No necesariamente operan sobre los mismos datos

Ejemplo: Una funcion que verifica los permisos del archivo y luego abre el archivo

![alt text](image-24.png)


#### Temporal
Módulos que se relacionan basados en el
momento.

Las partes de un módulo se agrupan según el
momento en el que se procesan. Las partes se
procesan en un momento determinado de la
ejecución del programa.


- Los modulos no tienen relacion directa
- Los modulos solo se relacionan debido a un evento

Ejemplos:
* Función que se llama después de detectar una excepción que cierra archivos abiertos, crea un registro de errores y notifica al usuario.

* Módulos que deben inicializarse/ejecutarse juntos al iniciar o finalizar el
sistema.


![alt text](image-25.png)


#### Logica
Los datos dentro del módulo están relacionados de manera
lógica pero no funcional.

Las partes de un módulo se agrupan porque están categorizadas lógicamente para hacer lo mismo aunque sean diferentes por naturaleza.

- Los datos dentro del modulo estan relacionados de manera logica pero no funcional. Por ejemplo:

* Un módulo que trabaja manipulando texto, el cual lo convierte a objeto, a stream, a flujos, etc. Las operaciones están relacionadas pero las funciones son distintas.

* Agrupar todas las rutinas de manejo de entrada del mouse y el teclado o agrupar todos los modelos, vistas y controladores en
carpetas separadas en un patrón MVC.


![alt text](image-26.png)

#### Coincidental
Los elementos del módulo no tienen ninguna
relación entre sí, más que su existencia en el mismo archivo de código.

Las partes de un módulo se agrupan de forma
arbitraria. La única relación entre las partes es
que se han agrupado juntas.

![alt text](image-27.png)

### Direccion de refactorizacion 
![alt text](image-28.png)

Siendo elrango coincidental el nivel mas bajo de  cohesión, el cual impacta negativamente en la mantenibilidad y comprensión del código; entonces la dirección natural de refactorización es el nivel anterior, hasta llegar al rango funcional

Cuidad: si ya tiene un bune rango de cohesion, intentar dividir el modulo solo resultara en incrementar el acoplamiento

Los estudios de Constantine, Yourdon y McConnell, indican que los dos rangos de la base son inferiores, la cohesión comunicacional y secuencial son muy buenas y la cohesión funcional es superior.


### Resumen 
Funcional: Todas las partes contribuyen a una sola tarea.

Secuencial: La salida de un elemento es la entrada de otro.

Comunicacional: Los elementos operan con los mismos datos.

Procedimental: Las actividades están relacionadas por una secuencia de ejecución.

Temporal: Los elementos se agrupan porque se ejecutan al mismo tiempo.

Lógica: Los elementos están relacionados por una lógica común pero no trabajan juntos.

Coincidente (Peor): Los elementos no tienen relación significativa entre si




## Ejermplo de Refactorizacion Secuencial -> funcional

![alt text](image-29.png)

![alt text](image-30.png)

![alt text](image-31.png)

- Tendencia a incrementar el acoplamiento, esto no necesariamente  es malo, dependerá del balance que se busca para la implementación.

Graficamente la refactorizacion se vio como:

![alt text](image-32.png)
Fórmula que considera el número de atributos y métodos, así como la cantidad de métodos que acceden a cada atributo.

- Rango de resultados [0, 1]
- 0 cohesión perfecta
- 1 completa ausencia de cohesión

![alt text](image-33.png)

![alt text](image-34.png)


Analisis y recomendacion de refactorizacion 

![alt text](image-35.png)

## Acoplamiento
O dependencia, mide el grado de interdependencia entre los modulos, clases o componentes de un sistema

![alt text](image-36.png)

Niveles de acoplamiento:
- Bajo acoplamiento (Deseable): Los módulos son independientes. Los cambios en un componente no afectan a los demás, lo que facilita el mantenimiento, las pruebas y la reutilización del código

- Alto acoplamiento (Evitar): Existe una dependencia fuerte. Si modificas un módulo, es muy probable que se rompan otros puntos del sistema, creando un "efecto dominó" que dificulta la escalabilidad

Tipos de acoplamiento: 
**Aferente (Ca):**
- Se refiere al número de dependencias
entrantes a un componente o módulo.
- Si el valor aferente es muy alto
significa que el módulo es crucial para
el sistema.

![alt text](image-37.png)

**Eferente (Ce)**
- Se refiere al número de dependencias salientes desde un componente o módulo.
- Un alto valor eferente indica que el componente depende de muchos otros, lo que puede hacerlo más susceptible a cambios en esos  componentes.

![alt text](image-38.png)


Ejercicio de conteo aferente y eferente 
![alt text](image-39.png)
![alt text](image-40.png)

### Metrica: Carcater abstracto 
![alt text](image-41.png)

### Metrica: inestabilidad
![alt text](image-42.png)

### Metrica: Distancia de la secuencia principal
![alt text](image-43.png)

Distancia de la secuencia principal
![alt text](image-44.png)

### Interpretacion grafica de la distancia

![alt text](image-45.png)

![alt text](image-46.png)

Ejemplo:
![alt text](image-47.png)

![alt text](image-48.png)

## Connascense
Esta es una metrica de calidad, introducida por Meilir Page-Jones, que mide el grado de dependencia entre dos o mas componentes de software. Indica que si un componente cambia, los otros deben modificarse para que el sistema siga funcionando, clasificandose por su fuerza, tipo y proximidad

**Dos módulos tienen connascencia si un cambio en uno obliga a cambiar el otro (nacen o se modifican juntos)**

Dos componentes son co-nacidos (connacense) si un cambio en uno requerirá la modificación del otro para mantener la correctitud general del sistema 

Clasificacion de la connascencia
Connascencia Estatica (Analizable en codigo): 
- Nombre (CoN): Cambio de nombre de una entidad (ej. método, variable).
- Tipo (CoT): Cambio en el tipo de datos (ej. cambiar de int a float).
- Posición (CoP): Dependencia del orden de parámetros.
- Algoritmo (CoA): Varios módulos deben usar el mismo algoritmo


Connascencia Dinamica (Detectable en tiempo de ejecucion)
- Ejecución (CoE): Dependencia en el orden de ejecución.
- Tiempo (CoT): Dependencia de la temporización (ej. tiempo de espera).
- Valores (CoV): Varios elementos deben coincidir en un valor específico.
- Identidad (CoI): Varios componentes dependen de la misma identidad de objeto

Niveles de connascene
![alt text](image-49.png)

Dimensiones de connascense
![alt text](image-50.png)

![alt text](image-51.png)

![alt text](image-52.png)

![alt text](image-53.png)

Tipos de connascense
![alt text](image-54.png)

### Connascense of name (CoN)
![alt text](image-55.png)

![alt text](image-56.png)

Tipo de arquitectura
![alt text](image-57.png)

### Connascense of type (CoT)
![alt text](image-58.png)

### Connascense of meaning / convention (CoM, CoC)
![alt text](image-59.png)

### Connascense of Algorithm (CoA)
![alt text](image-60.png)

### Connascense of position (CoP)
![alt text](image-61.png)

### Connascense of execution (CoE)
![alt text](image-62.png)

### Connascense of timing (CoT)
![alt text](image-63.png)

### Connascense of value (CoV)
![alt text](image-64.png)

### Connascense of identity (Col)
![alt text](image-65.png)
