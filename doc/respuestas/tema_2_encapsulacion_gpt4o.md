<!--
Posible prompt:
<prompt>
Tengo un cuestionario con preguntas sobre "Encapsulación". Debes tener en cuenta que los conocimientos previos que tengo (y por tanto tus respuestas deben ser adaptadas), son:
- C/C++ sin orientación a objetos.
- Temas de Java previos: Clases y Objetos.

Cada respuesta debe tener entre 2 - 4 párrafos de longitud (sin contar los trozos de código).

Por favor, escribe en impersonal las respuestas.

</prompt>
----
-->
# TEMA 2. Encapsulación

## 1. En Programación Orientada a Objetos (POO), ¿Qué buscan la **encapsulación** y **la ocultación** de información? Enumera brevemente algunas ventajas de la ocultación de información.

### En Programación Orientada a Objetos, la encapsulación y la ocultación de información buscan separar de forma clara la interfaz pública de una clase (lo que otros pueden usar) de su implementación interna (cómo funciona realmente por dentro). La idea fundamental es que el estado interno de un objeto quede protegido frente a accesos o modificaciones externas no controladas. De este modo, se obliga a que cualquier interacción con los datos se realice a través de métodos definidos por la propia clase, garantizando un uso correcto y coherente del objeto.
### La ocultación de información, como parte esencial de la encapsulación, persigue que el código externo solo conozca lo imprescindible para utilizar una clase, evitando que dependa de detalles internos que podrían cambiar con el tiempo. Esto proporciona una mayor libertad para modificar o mejorar la implementación interna sin afectar al resto del programa, siempre que la interfaz pública se mantenga estable. A diferencia de la programación en C/C++ sin POO, donde las estructuras y funciones suelen estar más expuestas, Java introduce mecanismos claros para limitar el acceso mediante modificadores como private, protected y public.
### Entre las ventajas de la ocultación de información pueden destacarse varias. En primer lugar, contribuye a mantener la integridad del estado interno, ya que los atributos no pueden modificarse de forma arbitraria desde cualquier punto del código. También ayuda a reducir la complejidad, pues quienes usan una clase no necesitan conocer ni comprender sus detalles internos. Además, facilita el mantenimiento y la evolución del software, permitiendo realizar cambios internos sin romper el código que ya depende de la clase.
### Otra ventaja importante es que mejora la fiabilidad y seguridad del programa, al permitir introducir validaciones, restricciones o controles dentro de los métodos que gestionan el acceso a los datos. Por último, favorece la creación de sistemas más modulares, donde cada componente tiene responsabilidades bien definidas y puede utilizarse como una “caja negra”, haciendo que el diseño general del software resulte más limpio y robusto.


## 2. ¿Qué se entiende por la **interfaz pública** de un objeto o clase en POO? Describe brevemente cómo se relaciona con la ocultación de información.

### La **interfaz pública** de un objeto o clase se entiende como el conjunto de métodos y atributos accesibles desde fuera de esa clase, es decir, aquello que otros componentes del programa pueden utilizar para interactuar con el objeto. Esta interfaz define qué operaciones pueden realizarse sobre la instancia y actúa como un contrato estable entre el objeto y el resto del sistema. De este modo, quienes usan la clase conocen únicamente las acciones permitidas, sin necesidad de saber cómo están implementadas internamente.

### La interfaz pública se relaciona directamente con la **ocultación de información**, ya que esta última consiste precisamente en mantener escondidos los detalles internos que no deberían ser accesibles. Al hacer que ciertos atributos y métodos sean privados o protegidos, se obliga a que toda interacción se canalice a través de la interfaz pública. Así, la clase controla de forma estricta cómo pueden modificarse o consultarse sus datos internos, lo que limita errores y refuerza la coherencia del estado del objeto.

### Además, esta separación entre interfaz y implementación permite cambiar libremente la lógica interna de la clase sin afectar al código que la utiliza, siempre que la interfaz pública permanezca intacta. Esto facilita enormemente el mantenimiento de programas más grandes, ya que los módulos quedan menos acoplados entre sí. Al igual que ocurre con la encapsulación en general, la interfaz pública contribuye a crear componentes más claros, seguros y fáciles de reutilizar.

### Por último, mantener una interfaz pública bien diseñada ayuda a reducir la complejidad cognitiva al desarrollar software. Al ocultar detalles superfluos y mostrar solo lo necesario para usar un objeto, se mejora la legibilidad del código y se evita que otros programadores dependan de aspectos internos que podrían cambiar en el futuro. Así, se fomenta un diseño más robusto y orientado a la modularidad.



## 3. Brevemente: ¿Por qué hay que ser conscientes y diseñar con cuidado la **interfaz pública** de una clase? ¿Es fácil cambiarla?

### La interfaz pública de una clase debe diseñarse con cuidado porque actúa como el punto de contacto entre esa clase y el resto del programa. Una vez que otros módulos empiezan a utilizarla, cualquier cambio en dicha interfaz puede afectar potencialmente a todo el código que depende de ella. Por este motivo, se considera una parte estable y duradera del diseño, y es recomendable que esté bien pensada antes de que la clase se utilice ampliamente en un proyecto. Una interfaz mal definida puede conducir a un alto acoplamiento, dificultando la evolución del software y aumentando la posibilidad de errores.
### No suele ser fácil cambiar la interfaz pública de una clase. En cuanto se modifica un método público —su nombre, sus parámetros o incluso su comportamiento esperado— todo el código que lo utiliza debe actualizarse en consecuencia. Esto puede provocar incompatibilidades, fallos y un mayor coste de mantenimiento. Por ello, la ocultación de información y la encapsulación resultan fundamentales: permiten cambiar la implementación interna sin tocar la interfaz pública, evitando la necesidad de modificar otras partes del programa y manteniendo la estabilidad general del sistema.


## 4. ¿Qué son las **invariantes de clase** y por qué la ocultación de información nos ayuda?

### Las **invariantes de clase** se entienden como condiciones lógicas que deben cumplirse siempre para que un objeto sea considerado válido durante toda su existencia. Dichas condiciones describen estados que no deberían romperse nunca, salvo durante la ejecución interna de algunos métodos, cuando el objeto se encuentra momentáneamente en transición. En esencia, una invariante refleja reglas que garantizan la coherencia del estado interno de la clase, como podrían ser rangos válidos, relaciones entre atributos o restricciones necesarias para el funcionamiento correcto del objeto.

### La ocultación de información ayuda a mantener estas invariantes porque evita que el código externo pueda modificar directamente los atributos internos. Al obligar a que cualquier cambio pase por métodos controlados, la clase puede asegurarse de que se verifican todas las condiciones necesarias antes de aceptar una modificación. De este modo, se reduce en gran medida el riesgo de que un objeto entre en un estado inconsistente, ya que solo la propia clase decide cómo y cuándo se alteran los datos que forman parte de su invariante.

### Además, este mecanismo facilita el mantenimiento del código, puesto que las comprobaciones de validez se concentran en puntos bien definidos en lugar de distribuirse por todo el programa. Así se consigue un diseño más robusto, donde los errores relacionados con estados inválidos son menos frecuentes y más fáciles de detectar. Al mismo tiempo, la implementación interna puede evolucionar sin comprometer la validez del objeto, siempre que la invariante se respete sistemáticamente.

### Finalmente, la presencia de invariantes claras y bien protegidas mejora la capacidad de razonar sobre el comportamiento de una clase. Cuando se sabe que ciertos estados están garantizados, resulta más sencillo entender, documentar y utilizar los objetos sin necesidad de revisar constantemente detalles internos. La ocultación de información, por lo tanto, no solo protege la integridad de los datos, sino que también contribuye de manera significativa a la claridad y fiabilidad del diseño orientado a objetos.



## 5. Pon un ejemplo de una clase `Punto` en `Java`, con dos coordenadas, `x` e `y`, de tipo `double`, con un método `calcularDistanciaAOrigen`, y que haga uso de la ocultación de información. ¿Cuál es la interfaz pública de la clase `Punto`? ¿Qué significa `public` y `private`?

### A continuación se muestra un ejemplo sencillo de una clase `Punto` en Java que encapsula dos coordenadas `x` e `y` de tipo `double`, expone un método `calcularDistanciaAOrigen()` y aplica ocultación de información mediante modificadores de acceso:

```java
public class Punto {
    // Atributos ocultos (estado interno)
    private double x;
    private double y;

    // Constructor (parte de la interfaz pública)
    public Punto(double x, double y) {
        this.x = x;
        this.y = y;
    }

    // Métodos de acceso controlado (parte de la interfaz pública)
    public double getX() {
        return x;
    }

    public double getY() {
        return y;
    }

    // Operación observable (parte de la interfaz pública)
    public double calcularDistanciaAOrigen() {
        return Math.sqrt(x * x + y * y);
    }

    // (Opcional) métodos setters con validación si se desea permitir cambios controlados
    // public void setX(double x) { this.x = x; }
    // public void setY(double y) { this.y = y; }
}
```

### La **interfaz pública** de la clase `Punto` está formada por todos los miembros accesibles desde fuera de la clase: el **constructor** `public Punto(double x, double y)`, los **métodos de lectura** `public double getX()` y `public double getY()`, y el **método de comportamiento** `public double calcularDistanciaAOrigen()`. Estos elementos constituyen el “contrato” para crear y usar instancias de `Punto` sin exponer ni depender de cómo se almacenan internamente las coordenadas. Los campos `x` e `y` no forman parte de la interfaz pública porque son `private` y, por tanto, están ocultos.

### En cuanto a los modificadores, **`public`** significa que el miembro (clase, constructor o método) es accesible desde cualquier otro código que tenga visibilidad del tipo. Por su parte, **`private`** restringe el acceso exclusivamente al interior de la propia clase, evitando que código externo lea o modifique directamente el estado. Esta separación favorece la **ocultación de información**: el estado se protege y cualquier interacción debe pasar por métodos públicos, donde pueden añadirse validaciones o invariantes, manteniendo la coherencia del objeto y permitiendo cambiar la implementación interna sin romper a los clientes.



## 6. En Java, ¿A quiénes se pueden aplicar los modificadores `public` o `private`?

### En Java, **`public`** puede aplicarse a **tipos de nivel superior** (clases, interfaces, *records* y *enums*) y también a **miembros** de una clase (constructores, métodos, campos) y a **tipos anidados** (clases, interfaces, *enums* y *records* definidos dentro de otra clase o interfaz). Marcar un tipo de nivel superior como `public` permite que sea accesible desde cualquier paquete, siempre que el archivo y el paquete sean visibles en el *classpath*.

### Por su parte, **`private`** **no** puede aplicarse a tipos de nivel superior. Solo puede usarse en **miembros** (campos, métodos y constructores) y en **tipos anidados** (clases, interfaces, *enums*, *records* definidos dentro de otro tipo). Esto restringe el acceso exclusivamente al interior de la clase contenedora. No se aplica a **variables locales ni parámetros**, ya que estos no admiten modificadores de acceso. En el caso de los **constructores** de `enum`, el acceso es implícitamente `private`, de modo que declararlo `private` es posible pero redundante.



## 7. En POO, la visibilidad puede ser pública o privada, pero ¿existen más tipos de visibilidad? ¿Qué ocurre en Java? ¿Y en otros lenguajes?

### En POO suelen manejarse varios **niveles de visibilidad** además de la pública y la privada. Aunque los nombres concretos dependen del lenguaje, en general se distingue entre visibilidad **pública** (acceso desde cualquier parte), **privada** (acceso solo desde la propia clase) y distintos niveles **intermedios** que permiten un acceso más controlado. Estos niveles adicionales permiten modular mejor el software y limitar el acoplamiento entre componentes, evitando que partes externas dependan de detalles internos no pensados para ser usados directamente.

### En Java existen **cuatro tipos de visibilidad**: `public`, `private`, `protected` y la visibilidad **por defecto** (llamada *default* o *package‑private*), que se aplica cuando no se especifica ningún modificador. La visibilidad `protected` permite el acceso desde la propia clase, desde clases del mismo paquete y desde subclases incluso en paquetes diferentes. La visibilidad *package‑private*, en cambio, permite el acceso únicamente a clases del mismo paquete, siendo útil para agrupar componentes relacionados sin exponerlos al exterior. Gracias a esta variedad de niveles, Java ofrece un control bastante fino sobre qué partes del código quedan expuestas.

### En otros lenguajes orientados a objetos aparecen variaciones, a veces más flexibles. Por ejemplo, en **C++** existen `public`, `private` y `protected`, pero además se permite cambiar la visibilidad heredada mediante *specifiers* y se dispone de la noción de **friend**, que otorga acceso especial a determinadas funciones o clases sin hacer públicos los miembros. Por otro lado, lenguajes como **Python** no tienen visibilidad estricta: usan convenciones como el prefijo `_` para indicar que algo es “interno”, aunque técnicamente sigue siendo accesible, y `__` para activar mecanismos de *name mangling*, que dificultan pero no impiden el acceso.

### En general, aunque la idea de controlar la visibilidad existe en prácticamente todos los lenguajes orientados a objetos, la manera de aplicarla y la rigidez del sistema varían bastante. Algunos lenguajes prefieren reglas estrictas para reforzar la encapsulación, mientras que otros se basan en convenciones o enfoques más flexibles. El objetivo común, sin embargo, sigue siendo mantener la coherencia interna de los objetos y evitar dependencias indeseadas entre partes del programa.


## 8. Responde: Los miembros de instancia privados de un objeto están ocultos para (a) otras clases o (b) otras instancias, aunque sean de la misma clase. Pon un ejemplo añadiendo un método `calcularDistanciaAPunto(Punto otro)` y explica la respuesta.

### Los **miembros de instancia privados** están ocultos para **otras clases** (a) —no pueden accederse desde fuera de la clase que los declara—, pero **no** están ocultos entre **instancias de la misma clase** (b) cuando el acceso se realiza **desde dentro** del propio código de la clase. En Java, la privacidad es **a nivel de clase, no de objeto**: cualquier método de la clase puede acceder a los campos `private` de **esta instancia** y de **otra instancia del mismo tipo** que reciba como parámetro. En cambio, desde fuera de la clase, incluso teniendo otra instancia del mismo tipo, no se puede leer ni escribir esos campos privados directamente.

### Ejemplo con el método `calcularDistanciaAPunto(Punto otro)`, donde se accede a `otro.x` y `otro.y` pese a ser `private`, porque el acceso ocurre **dentro de la propia clase** `Punto`:

```java
public class Punto {
    private double x;
    private double y;

    public Punto(double x, double y) {
        this.x = x;
        this.y = y;
    }

    public double calcularDistanciaAOrigen() {
        return Math.sqrt(x * x + y * y);
    }

    public double calcularDistanciaAPunto(Punto otro) {
        double dx = this.x - otro.x; // Válido: acceso a campos private de otra instancia dentro de la misma clase
        double dy = this.y - otro.y; // Válido por el mismo motivo
        return Math.sqrt(dx * dx + dy * dy);
    }
}
```

### En consecuencia, la afirmación correcta es: los miembros privados están ocultos para **otras clases** (a), pero **no** para **otras instancias de la misma clase** (b) cuando el acceso ocurre dentro del código de la clase. Si se intentara acceder a `otro.x` desde **otra clase** distinta a `Punto`, el compilador lo prohibiría. Este comportamiento permite implementar métodos que comparan, copian o combinan objetos del mismo tipo preservando la encapsulación hacia el exterior, mientras se mantiene la flexibilidad necesaria para operar entre instancias homogéneas.



## 9. ¿Qué son los métodos "getter" y "setter" en los lenguajes orientados a objetos?

### Los métodos **getter** y **setter** son operaciones públicas que permiten acceder y modificar, respectivamente, los atributos privados de un objeto en los lenguajes orientados a objetos. Se utilizan como una vía controlada para leer o cambiar el estado interno de una instancia sin exponer directamente sus campos. Gracias a ellos, el diseño mantiene la encapsulación y la ocultación de información, ya que el acceso a los datos no se realiza de forma directa, sino a través de una interfaz claramente definida por la propia clase.

### Un método **getter** devuelve el valor de un atributo privado. Su función principal es permitir consultar información del objeto sin comprometer la integridad de su estado. Por el contrario, un método **setter** establece o actualiza el valor de un atributo privado. En este caso, el método puede incluir validaciones, restricciones o comprobaciones necesarias para preservar las invariantes de la clase y evitar estados inconsistentes. Así, aunque el usuario de la clase pueda modificar ciertos valores, lo hace siempre bajo un control estricto.

### El uso de getters y setters aporta flexibilidad al diseño. Si en algún momento cambia la forma en que se representa internamente un atributo, basta con ajustar estos métodos sin modificar el resto del programa que utiliza la clase. Esto reduce el acoplamiento y facilita el mantenimiento del software. En lenguajes como Java, su uso está muy extendido y sigue convenciones claras de nomenclatura, lo que mejora la legibilidad y coherencia del código.

### Finalmente, aunque algunos lenguajes modernos proponen alternativas más concisas o mecanismos automáticos para generar estos métodos, el concepto sigue siendo esencial en la mayoría de paradigmas orientados a objetos. Los getters y setters representan un equilibrio entre accesibilidad y protección del estado, ofreciendo una forma segura y estructurada de interactuar con los datos encapsulados dentro de un objeto.


## 10. Cuando nos referimos a que la ocultación de información mejora la "seguridad" del programa, ¿nos referimos a que no pueda ser "hackeado"?

### No, cuando en POO se dice que la ocultación de información mejora la **“seguridad”**, no se está hablando de seguridad informática en el sentido de evitar *hackeos* o ataques externos. El concepto no tiene que ver con criptografía, protección contra intrusiones o ciberseguridad, sino con algo mucho más interno al propio programa: **proteger la coherencia del estado de los objetos y evitar errores lógicos**.

### En este contexto, “seguridad” significa que el diseño del programa es más **robusto**, **confiable** y **difícil de romper accidentalmente**. Al ocultar los atributos y permitir que solo se acceda a ellos mediante métodos controlados, se impide que otras partes del código modifiquen el estado de un objeto de forma arbitraria. Esto evita errores como dejar un objeto en un estado inválido, romper una invariante o generar interacciones inesperadas entre componentes. En lenguajes como Java, la encapsulación facilita este control al permitir definir qué es público y qué permanece oculto.

### Por otro lado, la ocultación también ayuda a garantizar que el programa evolucione sin introducir fallos. Si el estado interno de los objetos está protegido, se puede cambiar su implementación sin afectar al resto del sistema siempre que la interfaz pública siga siendo la misma. Este tipo de “seguridad” es una protección frente a cambios peligrosos dentro del propio proyecto, más que frente a amenazas externas.

### Por tanto, la relación con la seguridad informática real es indirecta o nula. La encapsulación no impide ataques, sino errores de diseño, modificaciones indeseadas y estados inconsistentes. Su objetivo principal es mantener un programa estable, claro y correctamente estructurado, no protegerlo de intrusiones. Si quieres, puedo explicarte con un ejemplo cómo un objeto puede quedar en un estado inválido si no se usa la encapsulación correctamente.


## 11. ¿Qué diferencia hay entre **miembro de instancia** y **miembro de clase**? ¿Los miembros de clase también se pueden ocultar?

### Un **miembro de instancia** es aquel que pertenece a cada objeto creado a partir de una clase. Cada instancia tiene *su propia copia* de esos atributos y métodos, de modo que modificar un miembro de instancia en un objeto no afecta a los demás. Por ejemplo, en una clase `Punto`, los campos `x` e `y` son miembros de instancia: cada punto concreto tiene sus propias coordenadas independientes. Estos miembros representan el estado individual de cada objeto y existen mientras exista la instancia correspondiente.

### Por el contrario, un **miembro de clase** es un miembro declarado con la palabra clave `static`. Este tipo de miembro no pertenece a las instancias, sino **a la clase en sí misma**, por lo que existe una única copia compartida entre todos los objetos. Esto permite almacenar información global o comportamientos que no dependen del estado particular de un objeto concreto. Un ejemplo típico sería un contador de cuántas instancias se han creado o constantes que pertenecen conceptualmente a la clase y no a cada objeto.

### En cuanto a la visibilidad, **los miembros de clase también pueden ocultarse**, igual que los miembros de instancia. El modificador `private` puede aplicarse a un campo o método `static`, de modo que solo sea accesible desde dentro de la propia clase. Esto es habitual en patrones de diseño como *singleton* o cuando se desea proteger detalles internos que no deberían ser visibles desde fuera. Del mismo modo, un miembro de clase puede ser `public`, `protected` o *package‑private*, según convenga al diseño.

### La posibilidad de ocultar miembros de clase mantiene coherente el principio general de encapsulación: tanto el estado individual (miembros de instancia) como el estado compartido (miembros de clase estáticos) pueden protegerse del acceso externo no controlado. Así se garantiza que las reglas de uso del objeto y de la propia clase se respeten, evitando manipulaciones indebidas del estado global y preservando la integridad del diseño. Si quieres, puedo darte un ejemplo en Java que compare ambos tipos de miembros dentro de la misma clase.



## 12. Brevemente: ¿Tiene sentido que los constructores sean privados?

### Sí, tiene sentido que los constructores sean privados en ciertas situaciones concretas dentro de la POO. Un constructor privado impide que el código externo pueda crear instancias libremente, algo útil cuando se necesita controlar estrictamente cuántos objetos se generan o en qué condiciones se crean. Este enfoque se utiliza cuando la clase quiere exponer un conjunto limitado de formas de obtener instancias, evitando usos indebidos o incoherentes de su interfaz pública.

### Un caso muy habitual es el **patrón Singleton**, donde se garantiza que solo exista una única instancia de la clase. Al hacer el constructor privado, se evita que el resto del programa pueda crear nuevos objetos y se obliga a usar un método estático controlado para acceder a la instancia. También tiene sentido en clases donde la creación debe pasar por métodos estáticos especializados, conocidos como **métodos factoría**, que permiten decidir internamente qué tipo de objeto devolver o aplicar validaciones previas.

### Los constructores privados también se emplean para evitar la creación directa de objetos que solo deben ser generados por otras clases del mismo paquete. En estos casos suelen combinarse con la visibilidad *package‑private* o con métodos auxiliares que encapsulan la lógica de construcción. Así, se mantiene un control más claro sobre la vida de los objetos y se refuerza la encapsulación del diseño.

### En resumen, aunque no es lo más habitual, existen numerosos escenarios en los que un constructor privado tiene un propósito claro: restringir o controlar la creación de instancias para preservar la coherencia, aplicar reglas internas o implementar patrones de diseño bien establecidos.



## 13. ¿Cómo se indican los **miembros de clase** en Java? Pon un ejemplo, en la clase `Punto` definida anteriormente, para que incluya miembros de clase que permitan saber cuáles son los valores `x` e `y` máximos que se han establecido en todos los puntos que se hayan creado hasta el momento.

### En Java, los **miembros de clase** se indican con la palabra clave `static`. Un miembro `static` no pertenece a cada objeto individual, sino a la **clase en sí**: existe una única copia compartida por todas las instancias. Esto resulta útil para almacenar estado o comportamiento global al tipo, como contadores, *caches* o límites agregados.

### A modo de ejemplo, puede definirse en `Punto` un par de campos de clase `maxX` y `maxY` que registren los **valores máximos** de `x` e `y` observados en **todas** las instancias creadas hasta el momento. Esos campos se actualizan en el **constructor** (y en posibles *setters*, si existen) y se consultan a través de **métodos `static`**. De este modo, al crear o modificar puntos, el tipo `Punto` va manteniendo el máximo global sin necesidad de recorrer todas las instancias.

### Conviene notar que, si se permite modificar coordenadas tras construir el objeto (mediante *setters*), la actualización de `maxX` y `maxY` debe repetirse también en esos métodos. Adicionalmente, en entornos concurrentes sería recomendable sincronizar el acceso a estos campos para evitar condiciones de carrera, pero para un escenario introductorio basta con la versión sencilla siguiente.

```java
public class Punto {
    // Estado interno (miembros de instancia)
    private double x;
    private double y;

    // Miembros de clase (compartidos por todas las instancias)
    private static double maxX = Double.NEGATIVE_INFINITY;
    private static double maxY = Double.NEGATIVE_INFINITY;

    // Constructor
    public Punto(double x, double y) {
        this.x = x;
        this.y = y;
        actualizarMaximos(x, y);
    }

    // Getters de instancia
    public double getX() { return x; }
    public double getY() { return y; }

    // Operaciones de instancia
    public double calcularDistanciaAOrigen() {
        return Math.sqrt(x * x + y * y);
    }

    public double calcularDistanciaAPunto(Punto otro) {
        double dx = this.x - otro.x;
        double dy = this.y - otro.y;
        return Math.sqrt(dx * dx + dy * dy);
    }

    // (Opcional) Setters con actualización de máximos
    public void setX(double x) {
        this.x = x;
        actualizarMaximos(this.x, this.y);
    }

    public void setY(double y) {
        this.y = y;
        actualizarMaximos(this.x, this.y);
    }

    // Métodos de clase (static) para consultar los máximos globales
    public static double getMaxX() { return maxX; }
    public static double getMaxY() { return maxY; }

    // Método privado auxiliar para mantener los máximos
    private static void actualizarMaximos(double x, double y) {
        if (x > maxX) maxX = x;
        if (y > maxY) maxY = y;
    }
}
```

### En este diseño, `maxX` y `maxY` son **ocultados** (`private static`) y se exponen de forma controlada mediante `getMaxX()` y `getMaxY()` (la **interfaz pública** de clase). El uso de `static` en los campos y en sus getters indica claramente que se trata de información compartida por todas las instancias de `Punto`.



## 14. Como sería un método factoría dentro de la clase `Punto` para construir un `Punto` a partir de dos coordenadas, pero que las redondee al entero más cercano. Escribe sólo el código del método, no toda la clase ¿Has usado `static`? 

```java
public static Punto crearRedondeado(double x, double y) {
    long rx = Math.round(x);
    long ry = Math.round(y);
    return new Punto((double) rx, (double) ry);
}
```

### Sí, se ha usado `static` porque es un **método factoría**: crea y devuelve instancias sin requerir una instancia previa.


## 15. Cambia la implementación de `Punto`. En vez de dos `double`, emplea un array interno de dos posiciones, intentando no modificar la interfaz pública de la clase.

### A continuación se muestra una posible **reestructuración interna** de `Punto` para almacenar las coordenadas en un **array privado** de longitud 2 (`coords[0]` = `x`, `coords[1]` = `y`), **sin modificar la interfaz pública** previamente usada (constructores, getters, setters opcionales, métodos de instancia, métodos de clase y el método factoría):

```java
public class Punto {
    // Estado interno ahora encapsulado en un array
    private final double[] coords = new double[2]; // coords[0] -> x, coords[1] -> y

    // Miembros de clase (compartidos por todas las instancias)
    private static double maxX = Double.NEGATIVE_INFINITY;
    private static double maxY = Double.NEGATIVE_INFINITY;

    // Constructor (firma intacta)
    public Punto(double x, double y) {
        coords[0] = x;
        coords[1] = y;
        actualizarMaximos(coords[0], coords[1]);
    }

    // Método factoría (firma intacta)
    public static Punto crearRedondeado(double x, double y) {
        long rx = Math.round(x);
        long ry = Math.round(y);
        return new Punto((double) rx, (double) ry);
    }

    // Getters (firmas intactas)
    public double getX() { return coords[0]; }
    public double getY() { return coords[1]; }

    // (Opcional) Setters (firmas intactas), si se permiten cambios después de construir
    public void setX(double x) {
        coords[0] = x;
        actualizarMaximos(coords[0], coords[1]);
    }

    public void setY(double y) {
        coords[1] = y;
        actualizarMaximos(coords[0], coords[1]);
    }

    // Operaciones de instancia (firmas intactas)
    public double calcularDistanciaAOrigen() {
        return Math.sqrt(coords[0] * coords[0] + coords[1] * coords[1]);
    }

    public double calcularDistanciaAPunto(Punto otro) {
        double dx = this.coords[0] - otro.coords[0]; // Acceso permitido dentro de la misma clase
        double dy = this.coords[1] - otro.coords[1];
        return Math.sqrt(dx * dx + dy * dy);
    }

    // Miembros de clase para consultar los máximos globales (firmas intactas)
    public static double getMaxX() { return maxX; }
    public static double getMaxY() { return maxY; }

    // Método auxiliar de clase (detalle de implementación)
    private static void actualizarMaximos(double x, double y) {
        if (x > maxX) maxX = x;
        if (y > maxY) maxY = y;
    }
}
```

### Con este cambio, se conserva el **contrato público** (interfaz) para no afectar al código cliente: se mantienen los mismos nombres y firmas de métodos/constructores (`getX`, `getY`, `setX`, `setY`, `calcularDistanciaAOrigen`, `calcularDistanciaAPunto`, `getMaxX`, `getMaxY`, y `crearRedondeado`). La **ocultación de información** mejora al centralizar el estado en un contenedor (`double[]`) que puede evolucionar (por ejemplo, para añadir más dimensiones) sin exponer detalles al exterior; quien usa la clase no necesita saber si internamente hay dos campos `double` o un array.

### Este diseño mantiene intactas las garantías de encapsulación y permite evolucionar la representación interna sin romper dependencias. Si se prevé concurrencia, convendría proteger el acceso a `maxX`/`maxY` (por ejemplo, con sincronización o `AtomicDouble` equivalente), pero para un entorno introductorio secuencial, la versión mostrada resulta adecuada.



## 16. Si un atributo va a tener un método "getter" y "setter" públicos, ¿no es mejor declararlo público? ¿Cuál es la convención más habitual sobre los atributos, que sean públicos o privados? ¿Tiene esto algo que ver con las "invariantes de clase"?

### En programación orientada a objetos no es mejor declarar un atributo público solo porque tenga un **getter** y un **setter** públicos. Aunque desde fuera parezca que el resultado es similar, declarar un atributo como público elimina por completo la **ocultación de información**, mientras que mantenerlo privado permite conservar el control sobre el acceso. Incluso si el getter y el setter son simples, su mera existencia permite cambiar la lógica interna más adelante sin romper la interfaz pública. Por ejemplo, en el futuro puede añadirse validación al setter, cálculo diferido en el getter o incluso cambiar la representación interna del atributo sin que el código cliente tenga que modificarse.

### La convención más habitual —y casi universal— en lenguajes como Java es que **los atributos deben ser privados** y el acceso debe realizarse mediante métodos públicos controlados. Esta regla no es solo una cuestión de estilo, sino un principio de diseño que protege el estado interno del objeto y evita que diferentes partes del programa accedan y modifiquen directamente los datos sin pasar por los mecanismos de control definidos. Además, esta convención permite sustituir getters/setters por otras operaciones más adecuadas en el futuro, sin perder compatibilidad con las interfaces públicas ya existentes.

### Esta práctica está directamente relacionada con las **invariantes de clase**, que son condiciones que deben mantenerse siempre que un objeto esté en un estado válido. Si un atributo fuese público, cualquier parte del programa podría modificarlo libremente, rompiendo las invariantes sin que la clase pueda impedirlo. En cambio, si el atributo es privado y solo puede modificarse mediante un setter, este método puede incluir comprobaciones que garanticen que la clase sigue cumpliendo sus invariantes. Así se asegura que los objetos no entren en estados inconsistentes y se mantenga la coherencia interna del diseño.

### Por tanto, incluso en el caso de atributos que se leen y escriben directamente, declararlos privados sigue siendo la mejor práctica. Esta decisión proporciona flexibilidad futura, protege la integridad del estado del objeto y mantiene la posibilidad de aplicar reglas internas sin romper el código ya existente. Es un ejemplo claro de cómo la encapsulación no se limita únicamente a ocultar datos, sino también a proporcionar mecanismos seguros y estables para interactuar con ellos.


## 17. ¿Qué significa que una clase sea **inmutable**? ¿qué es un método modificador? ¿Un método modificador es siempre un "setter"? ¿Tiene ventajas que una clase sea inmutable?

### Una **clase inmutable** es aquella cuyos objetos no pueden cambiar su estado interno una vez creados. Esto implica que todos sus atributos deben inicializarse en el constructor y, a partir de ese momento, no pueden modificarse. En lenguajes como Java, esta inmutabilidad se consigue normalmente declarando los atributos como `private` y `final`, y evitando métodos que alteren su contenido. De este modo, cada instancia representa un valor fijo y permanente, lo que facilita razonar sobre su comportamiento y evita estados inconsistentes.

### Un **método modificador** es cualquier método que *cambia el estado interno del objeto*. Esto incluye no solo los setters tradicionales, sino cualquier operación que altere un atributo, modifique colecciones internas o afecte a la información que forma parte de la representación interna de la clase. Por tanto, un método modificador **no es siempre un setter**: un método que, por ejemplo, incremente una coordenada, cambie elementos de un array interno o actualice un contador también es un modificador aunque no siga la forma típica de `setAtributo(...)`.

### Las clases inmutables presentan varias ventajas importantes. En primer lugar, facilitan el mantenimiento de las **invariantes de clase**, ya que el estado no cambia después del constructor, eliminando la posibilidad de que otros métodos o componentes rompan estas condiciones. En segundo lugar, simplifican el razonamiento sobre el programa y reducen errores, porque se sabe que un objeto no cambiará inesperadamente. Además, las clases inmutables son **intrínsecamente seguras frente a problemas de concurrencia**, ya que varios hilos pueden compartir las mismas instancias sin necesidad de sincronización adicional.

### Finalmente, las clases inmutables mejoran la reutilización y pueden servir como **objetos valor**, similares a números o cadenas en Java, que son naturalmente inmutables. Aunque implican crear nuevas instancias para representar cambios, esta característica suele ser aceptable en la mayoría de contextos y proporciona un diseño más robusto, claro y seguro. Si quieres, puedo mostrarte cómo convertir la clase `Punto` en una clase completamente inmutable.



## 18. ¿Es recomendable incluir métodos "setter" siempre y como convención?

### No, **no es recomendable incluir métodos *setter* siempre ni como una convención automática**. Los *setters* solo deben existir cuando realmente tenga sentido permitir que el estado del objeto cambie desde fuera. Incluirlos por costumbre debilita la encapsulación, expone detalles que quizá deberían permanecer ocultos y aumenta el riesgo de que otras partes del programa rompan invariantes o utilicen la clase de formas no previstas. En muchos diseños bien estructurados, buena parte de los atributos no necesitan ni deben ser modificables después de la construcción.

### La decisión de proporcionar un *setter* debe depender del **rol del atributo** dentro de la clase. Si el cambio del valor afecta a condiciones internas que deben mantenerse siempre (invariantes), permitir modificaciones libremente podría provocar estados inválidos. En esos casos, o bien no se expone ningún método modificador, o se diseña una operación específica que controle cuidadosamente la modificación, en lugar de un simple `setAtributo(...)` que solo asigne un valor. Por tanto, un *setter* no es una convención por defecto, sino una herramienta que debe justificarse.

### Además, evitar *setters* fomenta diseños más **seguros, robustos e inmutables**, algo especialmente valioso en programación concurrente o cuando se trabaja con objetos que representan valores conceptuales (como puntos, fechas o vectores). Las clases inmutables facilitan garantizar invariantes y reducen sorpresas, ya que los objetos no cambian de manera inesperada después de crearse. Esto mejora la claridad del diseño y limita el acoplamiento entre módulos.

### En resumen, los *setters* no deberían incluirse de forma sistemática. La convención habitual en Java y en la POO moderna es: **atributos privados siempre, y setters solo cuando exista una razón de diseño clara para permitir cambios**. Esta práctica respalda la encapsulación, mantiene las invariantes y contribuye a un código más mantenible y seguro. Si quieres, puedo ayudarte a decidir qué atributos deberían tener setters en un diseño concreto.



## 19. ¿La clase `String` en Java es mutable o inmutable? ¿Qué ocurre al concatenar dos cadenas? ¿Qué debemos hacer si vamos a hacer una operación que implique concatenar muchas veces para construir paso a paso una cadena muy larga?

### En Java, la clase **`String` es inmutable**, lo que significa que una vez creada una cadena, su contenido no puede modificarse. Cada operación que aparenta cambiarla —como concatenar, sustituir caracteres o convertir mayúsculas/minúsculas— en realidad crea **un nuevo objeto `String`** con el resultado. Esta inmutabilidad aporta seguridad, facilita el uso de cadenas como claves en estructuras como `HashMap` y evita problemas cuando se comparten entre distintos métodos o hilos.

### Cuando se **concatenan dos cadenas** con el operador `+`, Java crea internamente **un nuevo objeto `String`** que contiene el resultado de unir las dos cadenas originales. Esto implica que si se concatena repetidamente dentro de un bucle, se generan muchos objetos temporales, lo que puede penalizar el rendimiento y aumentar la carga del recolector de basura. Por ejemplo, hacer concatenaciones sucesivas en un `for` produce un coste proporcional al número de concatenaciones.

### Si se necesita **construir paso a paso una cadena muy larga**, la práctica recomendada es utilizar **`StringBuilder`** (o `StringBuffer` si se requiere sincronización). Estas clases son mutables y permiten añadir contenido sin crear nuevos objetos intermedios en cada operación. Tras completar las modificaciones, puede obtenerse el resultado final mediante el método `toString()`, generando así una única cadena definitiva. Este enfoque es más eficiente y es el recomendado en contextos donde se realizan muchas concatenaciones.

### En resumen, `String` es inmutable por diseño, la concatenación crea nuevas instancias y para construir cadenas extensas o generadas en bucles conviene utilizar `StringBuilder`. Si quieres, puedo darte un ejemplo de rendimiento comparando ambos enfoques.



## 20. En POO ¿Cómo se comparan objetos de una misma clase? ¿Por su contenido o por su identidad? ¿Qué es el método equals en Java? ¿Qué hace por defecto? ¿Cómo se deben comparar dos cadenas en Java? 

### En programación orientada a objetos, los objetos pueden compararse de dos formas: **por identidad** o **por contenido**. La *identidad* consiste en comprobar si dos referencias apuntan exactamente al **mismo objeto en memoria**; en Java esto se realiza con el operador `==`. En cambio, comparar **por contenido** implica verificar si dos objetos diferentes representan **el mismo valor lógico** según las reglas de su clase. Esta distinción es fundamental en la POO porque dos objetos pueden ser distintos en memoria pero equivalentes en significado.

### En Java, el método **`equals`** es el mecanismo estándar para comparar objetos **por contenido**. Este método está definido en la clase base `Object`, y su implementación por defecto simplemente compara **identidad**, es decir, `a.equals(b)` es equivalente a `a == b` si la clase no sobrescribe el método. Por ello, si una clase quiere definir su propia noción de igualdad lógica (por ejemplo, dos puntos con las mismas coordenadas), debe sobrescribir `equals` de manera coherente, normalmente junto con `hashCode`.

### En el caso particular de las cadenas, Java sobrescribe `equals` en la clase `String` para que compare **carácter a carácter**, es decir, por contenido y no por identidad. Por tanto, **dos cadenas deben compararse siempre usando `equals`** y **nunca con `==`**, salvo que se pretenda comprobar si ambas referencias apuntan al mismo objeto. El uso de `==` en cadenas es un error muy frecuente en principiantes, ya que puede devolver `false` aunque las cadenas tengan exactamente el mismo texto.

### Por último, esta separación entre identidad y contenido refleja una característica esencial de la POO: diferentes instancias pueden representar el mismo valor lógico incluso si no comparten identidad. Java ofrece mecanismos claros para manejar cada caso: `==` para identidad y `equals` para contenido. Entender esta diferencia es crucial para evitar fallos lógicos y diseñar clases que se comporten de forma coherente y predecible. 



## 21. ¿Qué son las clases "wrapper" en un lenguaje de programación orientado a objetos? ¿Cómo se hace? ¿Es un proceso automático? ¿Qué ventajas tienen? ¿Todos los lenguajes orientados a objetos tienen tipos primitivos y necesitan wrappers? 

### En programación orientada a objetos, las **clases *wrapper*** (o clases envoltorio) son clases que encapsulan un **tipo primitivo** dentro de un objeto. Su finalidad es permitir tratar valores básicos —como enteros o reales— como objetos completos, con métodos, comportamientos y la capacidad de integrarse en estructuras que requieren objetos. En Java, los *wrappers* típicos son `Integer`, `Double`, `Boolean`, etc., que envuelven a `int`, `double`, `boolean` y otros tipos primitivos. Gracias a ellos es posible almacenar valores simples en colecciones como `ArrayList` o `HashMap`, que no aceptan tipos primitivos.

### La conversión entre el tipo primitivo y su *wrapper* puede hacerse **explícitamente**, construyendo el objeto correspondiente, o **automáticamente**, gracias a un mecanismo del lenguaje llamado *autoboxing* y *unboxing*. Este proceso automático convierte un tipo primitivo en su *wrapper* (por ejemplo, de `int` a `Integer`) cuando se necesita un objeto, y a la inversa cuando se requiere un valor primitivo. Esta característica simplifica el código y evita la necesidad de crear objetos manualmente, aunque sigue siendo importante recordar que los *wrappers* son objetos inmutables y con un coste mayor que los primitivos.

### Las clases *wrapper* presentan varias ventajas: permiten integrar valores primitivos en contextos donde solo pueden usarse objetos, proporcionan métodos útiles (como parsear cadenas o realizar comprobaciones) y habilitan diseños más flexibles, como trabajar con valores nulos, algo que los tipos primitivos no permiten. Además, su presencia en Java refuerza la consistencia del lenguaje con su modelo orientado a objetos, ya que cualquier dato puede manipularse como objeto cuando sea necesario.

### No todos los lenguajes orientados a objetos necesitan *wrappers*. Lenguajes completamente orientados a objetos como **Smalltalk** o **Ruby** no tienen tipos primitivos: absolutamente todo es un objeto. Por ello, no necesitan envolver valores básicos. En cambio, lenguajes híbridos como **Java**, **C++** o **C#** sí incluyen tipos primitivos por motivos de rendimiento, y por tanto requieren clases *wrapper* para integrarlos en su modelo orientado a objetos cuando hace falta. Si quieres, puedo mostrarte ejemplos de *autoboxing* y *unboxing*, o comparar el rendimiento entre primitivos y *wrappers*.



## 22. ¿En POO qué es un **tipo de dato enumerado**? ¿En Java, un tipo de dato enumerado es una clase? ¿Qué ventajas tienen en términos de encapsulación los enumerados en Java?

### Un **tipo de dato enumerado** en POO es un tipo cuyos valores posibles forman un **conjunto finito, fijo y cerrado**. Cada uno de esos valores se denomina *miembro del enumerado* y representa una opción válida dentro del dominio del problema. Los enumerados permiten sustituir valores numéricos o cadenas sueltas por un tipo fuerte y claramente definido, lo que ayuda a evitar errores y hace que el código sea más expresivo y fácil de mantener. En lugar de permitir “cualquier valor”, un enumerado garantiza que solo pueden usarse los valores previstos por el diseño.

### En Java, un tipo de dato enumerado (**`enum`**) es, efectivamente, una **clase especial**. No es solo una lista de constantes: cada valor del `enum` es una **instancia única** de esa clase (públicamente accesible y final). Además, un `enum` puede tener atributos, métodos, constructores privados y comportamientos específicos. Esta estructura permite que los enumerados se integren completamente dentro del modelo orientado a objetos del lenguaje, ofreciendo mucho más que simples constantes simbólicas.

### En términos de encapsulación, los enumerados de Java presentan varias ventajas claras. Al ser clases, permiten **ocultar detalles internos** y exponer únicamente la interfaz pública necesaria. Los valores del `enum` no pueden modificarse ni instanciarse desde fuera, lo que garantiza que el conjunto de valores válidos sea inmutable y seguro. Esta característica protege las invariantes asociadas al tipo, ya que el usuario del `enum` no puede crear valores arbitrarios fuera del conjunto permitido, evitando estados inválidos dentro del programa.

### Además, los enumerados favorecen diseños más robustos al impedir errores típicos como usar constantes incorrectas, intercambiar valores incompatibles o confundir diferentes dominios conceptuales. Al encapsular todos los detalles y comportamientos dentro del `enum`, se consigue un tipo más seguro, expresivo y fácil de usar, manteniendo la coherencia del diseño orientado a objetos. Si quieres, puedo mostrarte un ejemplo de `enum` con métodos y atributos encapsulados para ver cómo se aplica en la práctica.


## 23. Crea un tipo enumerado en Java que se llame `Mes`, con doce posibles instancias y que además proporcione métodos para obtener cuántos días tiene ese mes, el ordinal de ese mes en el año (1-12), empleando atributos privados y constructores del tipo enumerado. Añade además cuatro métodos para devolver si ese mes tiene algunos días de invierno, primavera, verano u otoño, indicando con un booleano el hemisferio (norte o sur, parámetro `enHemisferioNorte`). Es decir: `esDePrimavera(boolean esHemisferioNorte)`, `esDeVerano(boolean esHemisferioNorte)`, `esDeOtoño(boolean esHemisferioNorte)`, `esDeInvierno(boolean esHemisferioNorte)`

### A continuación se define el `enum` `Mes` con sus doce instancias, almacenando de forma encapsulada el número de días (en año no bisiesto) y el ordinal 1–12 mediante atributos privados y constructor. Se incluyen los cuatro métodos de estación que consideran el **hemisferio** (norte/sur) según el parámetro `esHemisferioNorte`.

```java
public enum Mes {
    ENERO(31, 1),
    FEBRERO(28, 2),
    MARZO(31, 3),
    ABRIL(30, 4),
    MAYO(31, 5),
    JUNIO(30, 6),
    JULIO(31, 7),
    AGOSTO(31, 8),
    SEPTIEMBRE(30, 9),
    OCTUBRE(31, 10),
    NOVIEMBRE(30, 11),
    DICIEMBRE(31, 12);

    private final int dias;
    private final int ordinal1a12;

    private Mes(int dias, int ordinal1a12) {
        this.dias = dias;
        this.ordinal1a12 = ordinal1a12;
    }

    /** Número de días del mes en año no bisiesto. */
    public int getDias() {
        return dias;
    }

    /** Posición del mes en el año (1-12). */
    public int getOrdinal1a12() {
        return ordinal1a12;
    }

    /** ¿El mes contiene días de primavera en el hemisferio indicado? */
    public boolean esDePrimavera(boolean esHemisferioNorte) {
        return esHemisferioNorte
                ? (this == MARZO || this == ABRIL || this == MAYO)
                : (this == SEPTIEMBRE || this == OCTUBRE || this == NOVIEMBRE);
    }

    /** ¿El mes contiene días de verano en el hemisferio indicado? */
    public boolean esDeVerano(boolean esHemisferioNorte) {
        return esHemisferioNorte
                ? (this == JUNIO || this == JULIO || this == AGOSTO)
                : (this == DICIEMBRE || this == ENERO || this == FEBRERO);
    }

    /** ¿El mes contiene días de otoño en el hemisferio indicado? */
    public boolean esDeOtoño(boolean esHemisferioNorte) {
        return esHemisferioNorte
                ? (this == SEPTIEMBRE || this == OCTUBRE || this == NOVIEMBRE)
                : (this == MARZO || this == ABRIL || this == MAYO);
    }

    /** ¿El mes contiene días de invierno en el hemisferio indicado? */
    public boolean esDeInvierno(boolean esHemisferioNorte) {
        return esHemisferioNorte
                ? (this == DICIEMBRE || this == ENERO || this == FEBRERO)
                : (this == JUNIO || this == JULIO || this == AGOSTO);
    }
}
```

### Se mantiene la encapsulación: los atributos (`dias`, `ordinal1a12`) son **privados** y el constructor del `enum` es **privado** por definición, exponiéndose una interfaz pública clara mediante *getters* y métodos de consulta de estación. Para la estación se usa la correspondencia mensual estándar (p. ej., en el **hemisferio norte**: primavera=marzo–mayo, verano=junio–agosto, otoño=septiembre–noviembre, invierno=diciembre–febrero), invirtiéndose en el **hemisferio sur**. En cuanto a los días, **febrero** se modela con 28 (año no bisiesto); si se necesitara contemplar años bisiestos, convendría añadir una sobrecarga `getDias(int anio)` que aplique la regla de bisiesto sin romper la interfaz actual.

