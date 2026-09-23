%%%--------------------
# Programación funcional en lenguajes de uso común: JavaScript, Python y Java Streams

 ## Introducción

La programación funcional es un paradigma de programación que utiliza funciones como elemento principal para realizar operaciones sobre los datos. A diferencia de un enfoque estrictamente imperativo, donde se describe paso a paso cómo realizar una tarea, la programación funcional busca expresar qué transformación se desea realizar sobre los datos.

Entre sus características se encuentran el uso de funciones como valores, las funciones de orden superior, las funciones anónimas, la composición de operaciones y, cuando es posible, el uso de datos inmutables. Estas características permiten desarrollar programas mediante operaciones que pueden combinarse para procesar información de manera clara y estructurada.

Actualmente, lenguajes de uso común como JavaScript, Python y Java incorporan herramientas que permiten utilizar conceptos de programación funcional. JavaScript cuenta con métodos como `map()`, `filter()` y `reduce()`; Python proporciona herramientas como `lambda`, `map()`, `filter()` y `functools.reduce()`; mientras que Java incorpora la API de Streams, junto con expresiones lambda e interfaces funcionales.

---

# 1. Programación funcional

La programación funcional se basa en el uso de funciones para transformar y procesar información. Una función puede recibir datos como entrada y producir un resultado como salida.

Un concepto importante es el de **función de orden superior**, que consiste en una función que puede recibir otra función como argumento o devolver una función como resultado.

Por ejemplo, una operación que recibe una lista de números y una función para determinar qué hacer con cada número puede reutilizarse para diferentes tipos de operaciones.

Otro concepto importante es la **función pura**. Una función pura produce el mismo resultado cuando recibe los mismos valores de entrada y no depende de cambios externos para producir dicho resultado.

La programación funcional también busca reducir los cambios de estado y modificar lo menos posible los datos originales. Esto puede facilitar el mantenimiento y comprensión de los programas.

---

# 2. Programación funcional en JavaScript

JavaScript permite utilizar diferentes características de programación funcional. Entre las herramientas más importantes se encuentran las funciones como valores, las funciones flecha y los métodos de los arreglos.

Los métodos `map()`, `filter()` y `reduce()` son especialmente importantes para el procesamiento funcional de colecciones.

## 2.1 map()

El método `map()` crea un nuevo arreglo aplicando una función a cada elemento del arreglo original.

Ejemplo:

```javascript
const numeros = [1, 2, 3, 4, 5];

const cuadrados = numeros.map(n => n * n);

console.log(cuadrados);
```

Resultado:

```text
[1, 4, 9, 16, 25]
```

En este caso, la función `n => n * n` se aplica a cada elemento y genera un nuevo arreglo con los valores resultantes.

Una característica importante es que `map()` no necesita modificar directamente el arreglo original.

## 2.2 filter()

`filter()` permite crear un nuevo arreglo que contiene únicamente los elementos que cumplen una condición determinada.

Ejemplo:

```javascript
const numeros = [1, 2, 3, 4, 5, 6];

const pares = numeros.filter(n => n % 2 === 0);

console.log(pares);
```

Resultado:

```text
[2, 4, 6]
```

La función utilizada como condición determina qué elementos permanecen en el resultado.

## 2.3 reduce()

`reduce()` permite procesar los elementos de un arreglo para obtener un único resultado.

Por ejemplo, para sumar los elementos:

```javascript
const numeros = [1, 2, 3, 4];

const suma = numeros.reduce((total, n) => total + n, 0);

console.log(suma);
```

Resultado:

```text
10
```

En este caso, `total` funciona como acumulador y almacena progresivamente el resultado de la operación.

### Ventajas del enfoque funcional en JavaScript

El uso de estas operaciones permite expresar transformaciones de datos de manera declarativa. En lugar de utilizar un ciclo y modificar manualmente diferentes variables, se puede indicar directamente la transformación que se desea realizar.

---

# 3. Programación funcional en Python

Python también proporciona diferentes herramientas para trabajar con un estilo de programación funcional. Entre ellas se encuentran las funciones anónimas mediante `lambda`, además de `map()`, `filter()` y las funciones disponibles en el módulo `functools`.

La documentación oficial de Python incluye un apartado específico dedicado a los módulos relacionados con la programación funcional.

## 3.1 Funciones lambda

Una función `lambda` es una función anónima que puede utilizarse para realizar operaciones sencillas.

Ejemplo:

```python
cuadrado = lambda x: x * x

print(cuadrado(5))
```

Resultado:

```text
25
```

La expresión recibe un valor y devuelve su cuadrado.

## 3.2 map()

`map()` permite aplicar una función a cada elemento de un iterable.

```python
numeros = [1, 2, 3, 4, 5]

cuadrados = list(map(lambda n: n * n, numeros))

print(cuadrados)
```

Resultado:

```text
[1, 4, 9, 16, 25]
```

## 3.3 filter()

`filter()` permite seleccionar los elementos que cumplen una condición.

```python
numeros = [1, 2, 3, 4, 5, 6]

pares = list(filter(lambda n: n % 2 == 0, numeros))

print(pares)
```

Resultado:

```text
[2, 4, 6]
```

## 3.4 reduce()

Python proporciona `reduce()` mediante el módulo `functools`.

```python
from functools import reduce

numeros = [1, 2, 3, 4]

suma = reduce(lambda total, n: total + n, numeros, 0)

print(suma)
```

Resultado:

```text
10
```

En este caso, `reduce()` combina progresivamente los elementos hasta producir un único resultado.

## 3.5 Comprensiones de listas

Python también dispone de las llamadas **comprensiones de listas**, que permiten construir nuevas listas a partir de iterables de una manera compacta.

```python
numeros = [1, 2, 3, 4, 5]

cuadrados = [n * n for n in numeros]

print(cuadrados)
```

Resultado:

```text
[1, 4, 9, 16, 25]
```

Aunque las comprensiones de listas no son exclusivamente una característica de programación funcional, son una herramienta muy utilizada para realizar transformaciones sobre colecciones de datos.

---

# 4. Programación funcional en Java mediante Streams

Java incorporó en Java 8 la API de **Streams**, que permite realizar operaciones sobre secuencias de elementos utilizando un estilo declarativo.

Un Stream no es una colección de datos en sí misma. Es una forma de procesar los elementos de una fuente, como una lista, mediante una secuencia de operaciones.

Entre las operaciones más importantes se encuentran `filter()`, `map()` y `reduce()`.

## 4.1 map()

`map()` permite transformar cada elemento de un Stream.

```java
import java.util.List;

List<Integer> numeros = List.of(1, 2, 3, 4, 5);

List<Integer> cuadrados = numeros.stream()
        .map(n -> n * n)
        .toList();

System.out.println(cuadrados);
```

Resultado:

```text
[1, 4, 9, 16, 25]
```

Cada elemento de la lista original es transformado y el resultado se almacena en una nueva lista.

## 4.2 filter()

`filter()` permite seleccionar los elementos que cumplen una determinada condición.

```java
import java.util.List;

List<Integer> numeros = List.of(1, 2, 3, 4, 5, 6);

List<Integer> pares = numeros.stream()
        .filter(n -> n % 2 == 0)
        .toList();

System.out.println(pares);
```

Resultado:

```text
[2, 4, 6]
```

## 4.3 reduce()

`reduce()` permite combinar los elementos de un Stream para obtener un único resultado.

```java
import java.util.List;

List<Integer> numeros = List.of(1, 2, 3, 4);

int suma = numeros.stream()
        .reduce(0, (total, n) -> total + n);

System.out.println(suma);
```

Resultado:

```text
10
```

El primer argumento (`0`) funciona como valor inicial y la expresión `(total, n) -> total + n` define cómo se combinan los elementos.

## 4.4 Operaciones intermedias y terminales

Una característica importante de los Streams es que sus operaciones pueden dividirse en dos grupos principales.

### Operaciones intermedias

Son operaciones que producen otro Stream y pueden encadenarse.

Algunos ejemplos son:

* `filter()`
* `map()`
* `sorted()`
* `distinct()`

### Operaciones terminales

Son operaciones que producen un resultado final o generan un efecto.

Algunos ejemplos son:

* `reduce()`
* `collect()`
* `forEach()`
* `count()`

Por ejemplo:

```java
List<Integer> numeros = List.of(1, 2, 3, 4, 5, 6);

long resultado = numeros.stream()
        .filter(n -> n % 2 == 0)
        .count();

System.out.println(resultado);
```

Resultado:

```text
3
```

En este caso, `filter()` es una operación intermedia y `count()` es una operación terminal.

---

# 5. Ventajas de la programación funcional

Entre las principales ventajas de este paradigma se encuentran:

1. **Código más declarativo:** permite expresar de manera directa qué transformación se desea realizar.

2. **Reutilización:** las funciones pueden utilizarse en diferentes partes de un programa.

3. **Composición:** varias operaciones pueden combinarse para crear procesos más complejos.

4. **Menor modificación del estado:** al evitar modificar directamente los datos originales, algunas operaciones pueden resultar más fáciles de analizar.

5. **Procesamiento de colecciones:** herramientas como `map()`, `filter()` y `reduce()` facilitan el trabajo con listas, arreglos y otras colecciones.

6. **Legibilidad:** cuando se utilizan correctamente, las operaciones funcionales pueden hacer que el código sea más compacto y expresar claramente la intención de una operación.

---

# 6. Conclusión

La programación funcional es un paradigma que permite organizar los programas alrededor de funciones y transformaciones de datos. Aunque JavaScript, Python y Java tienen diferentes características y sintaxis, los tres ofrecen herramientas para aplicar conceptos funcionales.

En JavaScript destacan los métodos `map()`, `filter()` y `reduce()` de los arreglos. Python proporciona funciones como `map()` y `filter()`, expresiones `lambda`, el módulo `functools` y otras herramientas para trabajar con iterables. Java utiliza la API de Streams, junto con expresiones lambda e interfaces funcionales, para realizar operaciones sobre secuencias de datos.

El uso de estas herramientas permite escribir operaciones sobre colecciones de forma declarativa y combinar diferentes transformaciones. Por esta razón, los conceptos de programación funcional forman parte de las herramientas disponibles en varios de los lenguajes de programación de uso común.

---

# Fuentes consultadas

**Mozilla Developer Network (MDN Web Docs).**
*Array — JavaScript.* Documentación de referencia de JavaScript.
[MDN — Array JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array?utm_source=chatgpt.com)

**Mozilla Developer Network (MDN Web Docs).**
*Array.prototype.reduce().* Documentación de referencia de JavaScript.
[MDN — Array.prototype.reduce()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce?utm_source=chatgpt.com)

**Python Software Foundation.**
*Módulos de programación funcional.* Documentación oficial de Python.
[Python — Módulos de programación funcional](https://docs.python.org/es/3/library/functional.html?utm_source=chatgpt.com)

**Python Software Foundation.**
*functools — Higher-order functions and operations on callable objects.* Documentación oficial de Python.
[Python — functools](https://docs.python.org/3/library/functools.html?utm_source=chatgpt.com)

**Python Software Foundation.**
*itertools — Functions creating iterators for efficient looping.* Documentación oficial de Python.
[Python — itertools](https://docs.python.org/3/library/itertools.html?utm_source=chatgpt.com)

**Oracle.**
*Package java.util.stream — Java SE API.* Documentación oficial de Java.
[Oracle — Java Stream API](https://docs.oracle.com/javase/8/docs/api/java/util/stream/package-summary.html?utm_source=chatgpt.com)

**Oracle.**
*Interface Stream — Java SE API.* Documentación oficial de Java.
[Oracle — Interface Stream](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/util/stream/Stream.html?utm_source=chatgpt.com)

%%%--------------------


