# Teorema Maestro

El **Teorema Maestro** es una herramienta matemática que permite calcular de forma directa la complejidad temporal de algoritmos recursivos, especialmente aquellos basados en el paradigma de [Dividir y conquistar](https://github.com/JDavid-Moreno/Dividir-y-conquistar.git). Su propósito es resolver ecuaciones de recurrencia que siguen el siguiente patrón:

$$
T(n) = a T \left( \frac{n}{b} \right) + f(n)
$$

Este teorema evalúa la complejidad final analizando y comparando el costo de las llamadas recursivas frente al trabajo realizado fuera de ellas. En consecuencia, permite determinar directamente la notación Big O.

---

## Fórmula y significado de sus componentes

$$
T(n) = a T \left( \frac{n}{b} \right) + f(n)
$$

### Componente $a$
Representa la **cantidad de subproblemas** que se generan en cada nivel de recursión (es decir, el número de llamadas recursivas). Por ejemplo, en el algoritmo [Merge Sort](https://github.com/JDavid-Moreno/Algoritmos-de-ordenamiento/blob/main/Algoritmos/Merge/MergeSort.py), la lista se divide en dos partes iguales y se vuelve a llamar el método recursivo para cada una de ellas; por lo tanto, su cantidad de subproblemas es $a = 2$.

### Componente $b$
Representa el **factor de división** del problema; en otras palabras, es el factor por el cual se reduce el tamaño del argumento en cada nivel. Por ejemplo, si el problema se divide a la mitad, entonces $b = 2$; si se divide en tres partes, $b = 3$, y así sucesivamente. Para garantizar la reducción del problema, se necesita que $b > 1$.

### Componente $f(n)$
Representa el **costo del trabajo realizado fuera de las llamadas recursivas**. Esto incluye el tiempo invertido en las fases de división del problema y combinación de resultados, como la ejecución de ciclos, condicionales y operaciones elementales.

---

## Cómo calcular la complejidad a partir de la ecuación

Para determinar la complejidad mediante este método, partimos de la ecuación base:

$$
T(n) = a T \left(\frac{n}{b} \right) + f(n)
$$

Primero se deben identificar los valores numéricos de $a$ y $b$. El término $f(n)$, que representa el trabajo extra, se expresa generalmente como $O(n^c)$, donde $c$ es el exponente que analizáremos. De este modo, la estructura de la fórmula quedará de la siguiente manera:

$$
T(n) = {\color{red}a} T \left( \frac{n}{{\color{red}b}} \right) + O(n{\color{red}c})
$$

Una vez definidos estos parámetros, se comparan los valores para determinar cuál de los tres casos del teorema se aplica:

![Formas](./Recursos/TeoremaMaestro-formas.jpeg)

En la imagen anterior se observan los tres escenarios posibles para deducir la complejidad. El análisis se reduce a comparar matemáticamente el valor de $\log_b(a)$ con el exponente $c$:

1. Si $\log_b(a) > c$, el costo está dominado por las llamadas recursivas.
2. Si $\log_b(a) = c$, existe un equilibrio entre el trabajo recursivo y el trabajo local.
3. Si $\log_b(a) < c$, el costo está dominado por el trabajo fuera de la recursión.

### Ejemplo con Merge Sort

Sabemos de antemano que la complejidad de Merge Sort es $O(n \log n)$. A continuación, validaremos este resultado aplicando el Teorema Maestro.

**NOTA:** Para este ejemplo, utilizaremos la ecuación de recurrencia ya establecida para Merge Sort. El proceso detallado para construir esta ecuación a partir del código se explicará más adelante.

![Formas](./Recursos/TeoremaMaestroMerge.jpeg)

Como se puede observar, el cálculo nos conduce exactamente a la complejidad real de Merge Sort ($O(n \log n)$). Esto demuestra la efectividad del método, el cual puede aplicarse a cualquier algoritmo recursivo cuya estructura se ajuste a la del teorema.

---

## Cómo construir la ecuación de recurrencia

Es importante aclarar que no todos los algoritmos recursivos pueden ser evaluados con esta herramienta. El Teorema Maestro está restringido estrictamente a los modelos que cumplen con la estructura matemática presentada. 

A continuación, analizaremos una serie de ejemplos de algoritmos válidos, demostrando paso a paso cómo modelar su comportamiento para obtener su respectiva ecuación de recurrencia y resolverla.

Ejemplos: