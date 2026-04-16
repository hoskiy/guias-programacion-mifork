<!--
Posible prompt:
<prompt>
Tengo un cuestionario con preguntas sobre "Composición". Debes tener en cuenta que los conocimientos previos que tengo (y por tanto tus respuestas deben ser adaptadas), son:
- C/C++ sin orientación a objetos.
- Temas de Java previos: Clases y Objetos, Encapsulación y Excepciones.

Cada respuesta debe tener entre 2 - 4 párrafos de longitud (sin contar los trozos de código).

Por favor, escribe en impersonal las respuestas.

</prompt>
----
-->
# Tema 4.1. Composición


## 1. En C, podemos crear estructuras mayores **componiendo** unas con otras, que suelen describirse como "A tiene-un/tiene-varios B". Pon un ejemplo, empleando `struct`, de una línea de puntos, donde puntos tienen dos coordenadas (`x` e `y`), y la línea esta hecha de dos puntos. Incluye una función para calcular la distancia entre puntos y otra para hallar la longitud de una línea.

#### Estructurado
```c
// C
struct Punto{
    double x;
    double y;
}
struct Linea{
    struct Punto p1;
    struct Punto p2;
}
```
```c
// C
double distancia(struct Punto p1, struct Punto p2){
    ...
}
double longitud(struct Linea l){
    return distancia(l.p1, l.p2);
}
```


## 2. Ahora transforma ese ejemplo a orientación a objetos con Java, para tener un primer ejemplo de **composición** en orientación a objetos. Crea una clase `Punto`, y una clase `Linea`. La clase `Punto` debe tener un método para calcular distancia a otro `Punto` y `Linea` debe tener un método para calcular su longitud. Gracias a la ocultación de información, supera a C, garantizando que los puntos sean inmutables, al igual que la línea, que una vez creada, no queremos que se modifique de qué a qué puntos va dicha línea.  

#### Orientacion a Objetos
```java
// Java
class Punto{
    private double x;
    private double y;
    public Punto(double x, double y){
        ...
    }
    // encapsulado dentro de Punto metemos la funcion distancia
    public distancia(Punto p2){
        return Math.sqrt(this.x - p2.x ...);
    }
    // getters de x e y
    ...
}
```
```java
// Java
class Linea{
    private Punto p1;
    private Punto p2;
    public Linea(Punto p1, Punto p2){
        ...
    }
    // getters de p1 y p2
    ...
    public longitud(){
        return this.p1.distancia(this.p2);
    }
}
```


## 3. ¿Qué significa la **multiplicidad** en la composición? En el ejemplo anterior, ¿cuál es la multiplicidad entre `Linea` y `Punto`? Indícalo expresando la multiplicidad en ambas direcciones, de `Linea` a `Punto` y de `Punto` a `Linea`.

#### Multiplicidad de A y B
**Ejemplo --> entre linea y punto**

Notacion UML
+ 1 linea se relaciona como mínimo con 2 Puntos y como máximo con 2 Puntos
+ 1 Punto se relaciona como mínimo con 0 Lineas y como máximo con muchas Lineas



## 4. ¿Qué significa composición **fuerte** y composición **débil**? ¿Qué consecuencia implica en relación al ciclo de vida de los objetos? Indica a cuál solemos referirnos como **"asociación o agregación"** y a cuál como **"composición"** propiamente.

#### Composición fuerte
+ El contenedor (ej: `Linea`) es el que crea los objetos que contiene (ej: `Punto`) y estos no viven más allá del contenedor
+ El ciclo de vida del contenido está vinculado al contenedor
---
#### Composición débil
+ El contenedor y contenido tienen ciclos de vida independientes (ej: Los objetos `Punto` pueden vivir sin estar en objetos `Linea`)

El caso del primer ejemplo es de **composición débil**

---
#### UML
+ Composición persistente --> fuerte
+ Asociación o agregación --> débil

## 5. Cuando una clase usa a otra al recibirla o devolverla como parámetro en algún método, al hacer `new` dentro de un método, o al usarlas como variables locales, ¿hablamos de composición o de **"dependencia"**?

#### Ejemplos de "dependencia", NO de composición
Punto depende de String y StringBuilder
```java
class Punto{
    ...
    public String toString(){
        StringBuilder sb = new StringBuilder();
    }
}
```
```java
class OperadorFichero{
    public static String leeFichero(Path p){
        ...
    }
}
```


## 6. En el ejemplo anterior de línea y punto, programa la relación entre `Linea` y `Punto` de dos formas. Una **como composición fuerte**, donde el ciclo de vida de los puntos está ligado al de Linea y otra **como composición débil**, donde no.

#### Composición fuerte
```java
class Linea{
    private Punto p1;
    private Punto p2;
    public Linea(double x1, double y1, double x2, double y2){
        this.p1 = new Punto(x1, y1);
        this.p2 = new Punto(x2, y2);
    }
}
```
---
#### Composicion débil
Ejemplo en pregunta 2

## 7. En Java, en la composición fuerte, ¿cuándo el contenedor destruye los objetos? No se observa que `Linea` destruya los `Punto` explícitamente, ¿Por qué?

En Java, la vida de `Punto` termina cuando es inaccesible, y en el ejemplo ocurre cuándo linea deja de serlo a su vez.

Por tanto, cuándo linea "es basura", tambien lo serán sus puntos y serán eliminados de memoria por el recolector de basura


## 8. Pon un ejemplo de composicion débil entre un departamento que tiene varios profesores. Implementa dos composiciones a la vez: entre el departamento y todos sus profesores y entre el departamento y su director, que es un profesor del departamento. Siempre debe haber un director en el departamento desde el inicio. Lanza excepciones si se viola la invariante. Emplea arrays primitivos de Java, estilo `Profesor[]`, con máximo 50, pero no rompas la encapsulación, no desveles que estás empleando un array, permite añadir un `Profesor` al final de la lista, y eliminar un profesor dada su posición. Da acceso a los profesores con un método para saber cuántos hay y otro para obtener un profesor por posición. El director se puede cambiar por otro profesor del departamento. Sin embargo, ten en cuenta esta invariante de clase: el director debe formar siempre parte de la lista de profesores, es decir, ten cuidado al cambiar el director o al eliminar un profesor.

```java
public class Profesor{
    private String nombre;
    public Profesor(String nombre){
        this.nombre = nombre;
    }
}
```
```java
public class Departamento{
    // Composición débil 1:
    // 1 Departamento como minimo 0 y como maximo muchos Profesor
    // 1 Profesor como minimo 0 y como maximo muchos Departamentos
    private Profesor[] profesores = new Profesor[50];
    private int numProfesor = 0;

    // Composicion debil 2:
    // 1 Departamento como minimo 1 y como maximo 1 Profesor
    // 1 Profesor puede ser director como minimo de 0 y como maximo de muchos Departamento
    private Profesor director;

    public Departamento(Profesor director){
        // 0-Si director es null, lanzamos IllegalArgumentException (IAE)
        // 1-Añadimos el director al conjunto de profesores
        // 2-Establecemos ese profesor como director
    }
    public int getNumProfesores(){
        return this.numProfesores;
    }
    public Profesor getProfesor(int pos){
        // 0-Validamos pos, y si no valida lanzar IAE
        return this.profesores[pos];
    }
    public void addProfesor(Profesor p){
        // 0-Si ya no hay sitio, lanzamos ArrayIndexOutOfBoundsException (AIOBE)
    }
    public void eliminarProfesor(int pos){
        // 0-Si pos no esta en el rango correcto (0-numProfesores), lanzar IAE
        // 1-Si el profesor en pos ES EL DIRECTOR, lanzar IAE
    }
    public void cambiarDirector(Profesor nuevoDirector){
        // 0-Si nuevo director es null, lanzamos IAE
        // Si nuevo director no lo encuentro(bucle de busqueda), lanzo IAE
        // diciendo que hay que meterlo en el departamento primero
    }
    public Profesor getDirector(){
        return this.director;
    }
}
```
---
#### A tener en cuenta
+ Hay 2 composiciones débiles
+ No se expone el array al exterior (imposible garantizar invariante de clase)
+ En los métodos que gestionan el departamento se controla que no se viole la invariante de clase

## 9. En Java, existen también `List`, cambia y muestra cómo sería el código anterior empleando `List` en vez de arrays primitivos. ¿Qué parte del código original te has ahorrado? Además, fíjate en el método `getProfesor(int pos)`: si en su lugar existiera un método que devolviera todos los profesores a la vez, ¿qué problema tendría devolver directamente la lista interna? ¿Cómo lo resolverías?

#### Con List
```java
public class Profesor{
    private String nombre;
    public Profesor(String nombre){
        this.nombre = nombre;
    }
}
```
```java
public class Departamento{
    // Composición débil 1:
    // 1 Departamento como minimo 0 y como maximo muchos Profesor
    // 1 Profesor como minimo 0 y como maximo muchos Departamentos
    private List<Prodesor> profesores = new ArrayList<>();

    // Composicion debil 2:
    // 1 Departamento como minimo 1 y como maximo 1 Profesor
    // 1 Profesor puede ser director como minimo de 0 y como maximo de muchos Departamento
    private Profesor director;

    public Departamento(Profesor director){
        // 0-Si director es null, lanzamos IllegalArgumentException (IAE)
        // 1-Añadimos el director al conjunto de profesores
        // 2-Establecemos ese profesor como director
    }
    public int getNumProfesores(){
        return this.numProfesores;
    }
    public Profesor getProfesor(int pos){
        // 0-Validamos pos, y si no valida lanzar IAE
        return this.profesores[pos];
    }
    public void addProfesor(Profesor p){
        // 0-Si ya no hay sitio, lanzamos ArrayIndexOutOfBoundsException (AIOBE)
    }
    public void eliminarProfesor(int pos){
        // 0-Si pos no esta en el rango correcto (0-numProfesores), lanzar IAE
        // 1-Si el profesor en pos ES EL DIRECTOR, lanzar IAE
        // 2- Eliminar el elemento pos en el array (bucle de copia del siguiente y establecer a null la ultima)
    }
    public void cambiarDirector(Profesor nuevoDirector){
        // 0-Si nuevo director es null, lanzamos IAE
        // Si nuevo director no lo encuentro(bucle de busqueda), lanzo IAE
        // diciendo que hay que meterlo en el departamento primero
    }
    public Profesor getDirector(){
        return this.director;
    }

    // ACCESO A LA LISTA INTERNA??? (CUIDADO INVARIANTE DE CLASE)
    public List<Profesor> getProfesores(){
        // Problema --> return this.profesores;
        //copia, solucion clasica, pequeña penalizacion en rendimiento
        return new ArrayList<>(this.profesores);
        // Solucion alternativa, sin copia
        return Collections.unmodificableList(this.profesores);
    }
    // Problema --> La lista es mutable, perdemos el control sobre la invariante de clase
    // Si insisto en usar esta interfaz, pero quiero garantizar que solo se use para recorrerlos y no modificar, puedo:

    // 1- Devolver una copia de la lista
    // 2- Devolver un envoltorio no mutable
}
```
#### A tener en cuenta
+ No cambias la interfaz publica
+ Es más facil implementar algunos metodos, delegando en métodos de List
+ Si se devuelve, hay que devolver una copia, para proteger la invariante de clase



## 10. Al igual que ocurre con las excepciones en Java, que pueden encerrar causas (que son excepciones), de forma recursiva, suponen un tipo especial de composiciones, denominadas composiciones recursivas. Pon un ejemplo en Java de una `Persona`, que sea inmutable, y que tiene una madre, que es otra `Persona`. Haz un main con un ejemplo de uso con una familia de personas, desde el nieto hasta la abuela. Enumera algún otro ejemplo clásico de composiciones recursivas.

```java
class Persona{
    private Persona madre;
    public Persona(Persona madre){
        this.madre = madre;
    }
    public Persona(){
        this.madre = null;
    }

    public static void main (String args[]){
        Persona abuela = new Persona();
        Persona hija = new Persona(abuela);
        Persona nieto = new Persona(nieto);
    }
}
```

## 11. ¿Qué son las relaciones de composición "bidireccionales"? ¿Qué habría que hacer para implementar este tipo de relación en el ejemplo de `Profesor` y `Departamento`?

Las bidireccionales exigen programar cuidadosamente para mantener la consistencia

* Ejemplo: Si añado un profesor al departamento debo actualizar la referancia al `Departamento` desde `Profesor`
