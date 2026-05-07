<!--
Posible prompt:
<prompt>
Tengo un cuestionario con preguntas sobre "Aspectos funcionales". Debes tener en cuenta que los conocimientos previos que tengo (y por tanto tus respuestas deben ser adaptadas), son:
- C/C++ sin orientación a objetos.
- Temas de Java previos: clases y objetos, encapsulación, excepciones, composición, herencia, polimorfismo y genericidad.

Cada respuesta debe tener entre 2 - 4 párrafos de longitud (sin contar los trozos de código).

Por favor, escribe en impersonal las respuestas.

</prompt>
----
-->

# TEMA 7. Aspectos funcionales

## 1. ¿Qué es un puntero a una función? Pon un ejemplo de código en C, donde se define una función y que reciba una cadena de caracteres como parámetro y devuelva la cadena en mayúsculas. Crea un puntero en una variable local a dicha función llamado `aMayusculas` e invócala con el puntero.


Un **puntero a función** en C es una variable que almacena la dirección de una función, permitiendo llamar a la función a través del puntero. Esto permite pasar funciones como parámetros, almacenarlas en estructuras, o seleccionar dinámicamente qué función ejecutar.

**Ejemplo en C:**

```c
#include <stdio.h>
#include <ctype.h>
char* convertirMayusculas(char* cadena) {
	for (int i = 0; cadena[i] != '\0'; i++) {
		cadena[i] = toupper(cadena[i]);
	}
	return cadena;
}

int main() {
	char texto[] = "hola mundo";
	char* (*aMayusculas)(char*) = convertirMayusculas;
	printf("%s\n", aMayusculas(texto));
	return 0;
}
```
>**Nota:** En este ejemplo, `aMayusculas` es un puntero a la función `convertirMayusculas`, y se utiliza para invocar la función sobre la cadena.


## 2. ¿Qué es una **función lambda** en un lenguaje de programación? Pon un ejemplo similar al anterior en Javascript y otro en Java con funciones lambda. Usa una variable local `aMayusculas` para apuntar a la función lambda. Por simplicidad, en Java, emplea `Function<String, String>` para el tipo de la referencia a la función lambda.


Función lambda
: Es una función anónima, es decir, una función que no tiene nombre y que puede ser definida en línea. 

+ Permite tratar a las funciones como valores, facilitando la programación funcional y el paso de funciones como argumentos.

---

**Ejemplo en JavaScript:**

```javascript
const aMayusculas = (cadena) => cadena.toUpperCase();
console.log(aMayusculas("hola mundo")); // "HOLA MUNDO"
```

**Ejemplo en Java:**

```java
import java.util.function.Function;
Function<String, String> aMayusculas = s -> s.toUpperCase();
System.out.println(aMayusculas.apply("hola mundo")); // "HOLA MUNDO"
```

>**Nota:** En ambos casos, `aMayusculas` es una variable local que apunta a una función lambda que transforma una cadena a mayúsculas.
---
>**Nota de Clase:** `Function<String, String>`
1er String -> recibe
2ndo String -> devuelve



## 3. ¿Qué es el **paradigma funcional**? ¿Por qué a algunos lenguajes orientados a objetos como Java 8, se les llama multi-paradigma? ¿Qué quiere decir que las funciones son "ciudadanos de primera clase"?


El **paradigma funcional** es un estilo de programación donde las funciones son el elemento principal, y se favorece la inmutabilidad, la ausencia de efectos secundarios y el uso de funciones como valores.

Lenguajes como Java 8 se consideran **multi-paradigma** porque permiten programar tanto en estilo orientado a objetos como en estilo funcional, gracias a la introducción de funciones lambda y APIs funcionales.

Se dice que las funciones son **ciudadanos de primera clase** cuando pueden ser asignadas a variables, pasadas como argumentos y devueltas como resultado de otras funciones, igual que cualquier otro dato.


## 4. Explica la sintaxis básica de una función lambda en Java.


La sintaxis básica de una función lambda en Java es:

```java
(parámetros) -> expresión_o_bloque
```

**Ejemplo:**

```java
// Lambda que convierte una cadena a mayúsculas
s -> s.toUpperCase()
```

Si hay más de un parámetro, se usan paréntesis:

```java
(a, b) -> a + b
```

Si el cuerpo tiene varias sentencias, se usan llaves y return:

```java
s -> {
	String resultado = s.trim();
	return resultado.toUpperCase();
}
```


## 5. Ahora recibamos una función como parámetro a un método y la llamaremos desde dentro. Amplia los ejemplos anteriores de Java y JavaScript con un método llamado `transformar`, que reciba un `String` como parámetro y luego una función transformadora como lo es `aMayúsculas` y la invoque desde dentro.


Recibir funciones como parámetros permite mayor flexibilidad y reutilización. A continuación, se muestra cómo hacerlo en JavaScript y Java:

**JavaScript:**

```javascript
function transformar(cadena, funcion) {
	return funcion(cadena);
}
const aMayusculas = s => s.toUpperCase();
console.log(transformar("hola", aMayusculas)); // "HOLA"
```

**Java:**

```java
import java.util.function.Function;
public static String transformar(String cadena, Function<String, String> funcion) {
	return funcion.apply(cadena);
}
Function<String, String> aMayusculas = s -> s.toUpperCase();
System.out.println(transformar("hola", aMayusculas)); // "HOLA"
```


## 6. Ahora, invoca `transformar`, con una nueva función lambda directamente en la llamada a `transformar`, por ejemplo, una función lambda que invierta la cadena. Define la función de inversión justo cuando la estás pasando como parámetro.


Se puede definir una función lambda "en línea" al llamar a `transformar`, sin necesidad de crear una variable intermedia.

**JavaScript:**

```javascript
console.log(transformar("hola", s => s.split("").reverse().join(""))); // "aloh"
```

**Java:**

```java
System.out.println(transformar("hola", s -> new StringBuilder(s).reverse().toString())); // "aloh"
```

Esto demuestra cómo las funciones lambda pueden ser creadas y usadas directamente como argumentos.


## 7. ¿Qué se entiende por cierre o "closure" en el contexto de las funciones lambda? Pon un ejemplo en Java de cómo una función lambda es capaz de acceder a una variable local en el contexto donde fue definida. Modifica el ejemplo anterior, creando otra función lambda para transformar una cadena, pero que lo que haga es concatenar a la cadena de entrada otra cadena que está en una variable local definida fuera de la función lambda.


Un **closure** es una función que recuerda el entorno en el que fue creada, es decir, puede acceder a variables locales definidas fuera de su propio cuerpo, siempre que sean efectivamente finales (no modificadas después de su asignación).

**Ejemplo en Java:**

```java
String sufijo = "!!!";
Function<String, String> añadirSufijo = s -> s + sufijo;
System.out.println(añadirSufijo.apply("hola")); // "hola!!!"
```

En este ejemplo, la función lambda accede a la variable local `sufijo` definida fuera de ella, formando un closure.


## 8. Reflexiona: ¿en qué se diferencia entonces una función lambda de los punteros a funciones que hay en C?


Las funciones lambda y los punteros a función permiten tratar funciones como valores, pero existen diferencias clave:

- **Contexto:** Las lambdas pueden capturar variables del entorno (closures), mientras que los punteros a función en C solo apuntan a funciones globales o estáticas, sin capturar contexto.
- **Tipado:** En C, los punteros a función requieren especificar la firma exacta; en lenguajes modernos, las lambdas pueden inferir tipos y ser más flexibles.
- **Sintaxis y expresividad:** Las lambdas permiten definir funciones en línea y de forma más concisa, facilitando la programación funcional.


## 9. Devolvamos ahora funciones. Creemos ahora una función que sea capaz de crear funciones "descuento". Una función "descuento", decrementa un porcentaje pasado como parámetro. Por simplicidad, usa `Function<Double, Double>` para su tipo. La función `crearDescuento(porcentaje)`, recibe solo el porcentaje de descuento a aplicar y devuelve la función de descuento. Prueba a crear dos descuentos distintos y aplicarlos a una cantidad. Explica la closure en la función descuento.


En Java, se pueden devolver funciones usando lambdas. La función `crearDescuento` devuelve una función que aplica un descuento sobre un valor:

```java
import java.util.function.Function;
public static Function<Double, Double> crearDescuento(double porcentaje) {
	return cantidad -> cantidad * (1 - porcentaje / 100);
}
Function<Double, Double> descuento10 = crearDescuento(10);
Function<Double, Double> descuento25 = crearDescuento(25);
System.out.println(descuento10.apply(100.0)); // 90.0
System.out.println(descuento25.apply(100.0)); // 75.0
```

La función lambda devuelta recuerda el valor de `porcentaje` gracias a un closure.


## 10. En Java, que es un lenguaje con comprobación estática de tipos, donde los tipos se declaran, toda función lambda tiene un tipo, que se conoce como **interfaz funcional**. ¿Qué es una **interfaz funcional**? ¿Qué requisitos tiene?


Una **interfaz funcional** en Java es una interfaz que declara exactamente un método abstracto. Es el tipo que puede representar una función lambda.

**Requisitos:**

- Solo puede tener un método abstracto.
- Puede tener métodos `default` o `static`.
- Se puede marcar con la anotación `@FunctionalInterface` (opcional, pero recomendable).


## 11. Creemos una interfaz funcional a mano. Por ejemplo, define la interfaz funcional del ejemplo que transforma la cadena en otra. Llámale `Transformador`, que define una función que convierte una cadena de texto (`String`) en otra (`String`).


**Definición de la interfaz funcional:**

```java
@FunctionalInterface
public interface Transformador {
	public String transformar(String entrada);
}
```

Esta interfaz permite definir lambdas o referencias a métodos que transforman cadenas.


## 12. Ahora hagamos la interfaz funcional algo más genérica y empleando generics, para que permita definir un `Transformador` de un tipo en otro. Pon un ejemplo de un transformador que redondea un `Double` en un `Integer`.


**Versión genérica de la interfaz:**

```java
@FunctionalInterface
public interface Transformador<T, R> {
	R transformar(T entrada);
}
```

**Ejemplo de uso:**

```java
Transformador<Double, Integer> redondear = d -> (int) Math.round(d);
System.out.println(redondear.transformar(3.7)); // 4
```


## 13. `Transformador`, en su versión genérica, parece muy útil y reutilizable, hasta el punto de que es igual a una interfaz funcional que ya hay, que es `Function<T, R>`. Muestra las interfaces funcionales predefinidas que hay en Java.


Java proporciona varias **interfaces funcionales predefinidas** en el paquete `java.util.function`:

- `Function<T, R>`: transforma un valor de tipo T en uno de tipo R.
- `Consumer<T>`: recibe un valor de tipo T y no devuelve nada.
- `Supplier<T>`: no recibe parámetros y devuelve un valor de tipo T.
- `Predicate<T>`: recibe un valor de tipo T y devuelve un booleano.
- `UnaryOperator<T>`: como Function, pero entrada y salida son del mismo tipo.
- `BinaryOperator<T>`: como Function, pero con dos entradas del mismo tipo y una salida del mismo tipo.
>**Nota de Clase:** 
`BiFunction<E1, E2, S>`: recibe 2 parametros de tipo E1, E2 y devulve un valor de tipo S
`Runnable`: run():void

## 14. Vamos a ver ejemplos expresivos de funcional en Java. Estudiemos el `List.forEach`, como versión funcional del bucle `for`. Emplea el `forEach` para recorrer una lista de `Integer` y que muestre un mensaje si el entero es positivo.


### Respuesta

El método `forEach` permite aplicar una acción a cada elemento de una lista de forma funcional.

**Ejemplo:**

```java
import java.util.*;
List<Integer> numeros = Arrays.asList(-2, 0, 3, 7, -1);
numeros.forEach(n -> {
	if (n > 0) {
		System.out.println(n + " es positivo");
	}
});
```

Esto reemplaza el clásico bucle `for` por una expresión más declarativa.

## 15. Repasando el tema de genericidad, fíjate en la firma de `forEach`, ¿por qué se usa `Consumer<? super T>` y no `Consumer<T>`? Explica qué significa **PECS**, y explícalo para el caso de mejorar el ejemplo del método `transformar` la hora de definir el tipo de la función transformadora.


### Respuesta

La firma `Consumer<? super T>` permite mayor flexibilidad, ya que acepta consumidores de T o de cualquier supertipo de T. Esto sigue el principio **PECS**:

> **PECS**: *Producer Extends, Consumer Super*

Esto significa:
- Si un parámetro produce valores, se usa `? extends T`.
- Si consume valores, se usa `? super T`.

En el caso de `transformar`, si se quisiera aceptar funciones que transforman cualquier supertipo de String, se podría usar `Function<? super String, ? extends String>` para mayor generalidad.

## 16. Referencias a métodos. Podemos obtener una referencia a métodos de objetos o clases. Pon un ejemplo en JavaScript y en Java, de una clase `Persona` con un método `saludar`. En el código principal, crea una `Persona` con un nombre, y obtén una referencia a su método `saludar` en una variable local. Invoca `saludar` con esa referencia a su método `saludar`.


### Respuesta

**JavaScript:**

```javascript
class Persona {
	constructor(nombre) {
		this.nombre = nombre;
	}
	saludar() {
		return `Hola, soy ${this.nombre}`;
	}
}
const p = new Persona("Ana");
const refSaludar = p.saludar.bind(p);
console.log(refSaludar()); // "Hola, soy Ana"
```

**Java:**

```java
class Persona {
	private String nombre;
	public Persona(String nombre) { this.nombre = nombre; }
	public String saludar() { return "Hola, soy " + nombre; }
}
Persona p = new Persona("Ana");
Supplier<String> refSaludar = p::saludar;
System.out.println(refSaludar.get()); // "Hola, soy Ana"
```


## 17. ¿Qué tipos de referencias a método se pueden hacer en Java? Pon un ejemplo de referencia a método estático, a constructor, a método de instancia de una instancia concreta y a método de instancia sobre cualquier instancia.


### Respuesta

En Java existen varios tipos de referencias a métodos:

1. **Método estático:**
	```java
	Function<String, Integer> parseador = Integer::parseInt;
	```
2. **Constructor:**
	```java
	Supplier<List<String>> creador = ArrayList::new;
	```
3. **Método de instancia de un objeto concreto:**
	```java
	String texto = "hola";
	Supplier<String> mayus = texto::toUpperCase;
	```
4. **Método de instancia sobre cualquier instancia de un tipo:**
	```java
	Function<String, Integer> longitud = String::length;
	```


## 18. Otro ejemplo expresivo. Ordena una lista de `Persona`, cada persona tiene un nombre y una edad (de tipo entero). Ordena la lista de `Persona` con `Collections.sort`, pasándole como comparador una expresión lambda que compare la edad de ambas personas y si tienen la misma edad, se ordene por orden alfabético del nombre. Crea dos versiones: Una con la función de comparación hecha manualmente, y otra empleando `Comparator`.


### Respuesta

**Definición de la clase Persona:**

```java
class Persona {
	String nombre;
	int edad;
	public Persona(String nombre, int edad) {
		this.nombre = nombre;
		this.edad = edad;
	}
}
List<Persona> personas = Arrays.asList(
	new Persona("Ana", 20),
	new Persona("Luis", 20),
	new Persona("Bea", 18)
);
```

**Versión manual:**

```java
Collections.sort(personas, (p1, p2) -> {
	if (p1.edad != p2.edad)
		return Integer.compare(p1.edad, p2.edad);
	return p1.nombre.compareTo(p2.nombre);
});
```

**Usando Comparator:**

```java
personas.sort(Comparator.comparingInt((Persona p) -> p.edad)
	.thenComparing(p -> p.nombre));
```

Ambas versiones ordenan primero por edad y, en caso de empate, por nombre alfabéticamente.
