# Teorema Maestro

Teorema maestro es una herramienta que nos permite calcular la complejidad de algoritmos recursivos, generalmente los que son [Dividir y conquistar](https://github.com/JDavid-Moreno/Dividir-y-conquistar.git), Permite resolver recurrencias que son de la forma o siguen el patron:  

$$
T(n) = a T \left( \frac{n}{b} \right) + f(n)
$$

Comparando el costo de las llamadas recursivas con el trabajo realizado fuera de ellas para determinar la complejidad final del algoritmo, o sea el Teorema Maestro permite obtener directamente la complejidad Big O.

---

## Fórmula o ecuación y su significado

$$
T(n) = a T \left( \frac{n}{b} \right) + f(n)
$$

### a
Representa la Cantidad de subproblemas que se crean, es decir, la cantidad de llamadas recursivas, por ejemplo en [Merge Sort](https://github.com/JDavid-Moreno/Algoritmos-de-ordenamiento/blob/main/Algoritmos/Merge/MergeSort.py) lo que hacemos es dividir la lista en dos partes iguales y a cada parte nuevamente llamamos merge sort a cada una, por lo que su cantidad de subproblemas nuevos es: $a = 2 $ 

### b

Representa el factor de división del problema o mejor dicho, el factor por el que se reduce el tamaño, por ejemplo si se divide entre 2 queda $b = 2 $, si se divide entre 3 queda $b = 3 $, y asi sucesivamente.

### f(n)

Trabajo que se hace fuera de las llamadas recursivas, o sea los ciclos, verificaciones, etc.

---

## Como calcular la complejidad dado la ecuación

En caso de que se nos de ya la "formula" con los datos y queremos encontrar la solución, hay 3 casos posibles:

Dado la ecuación: 

$$
T(n) = a T \left(\frac{n}{b} \right) + f(n)
$$

tenemos que revisar los valores que nos dan para $a$ $b$ y $f(n)$, este ultimo como ya nos lo dan resuleto vendra de la forma $O(nᶜ)$ donde C sera la variable que tendremos que analizar, por lo que quedaria la formula asi

$$
T(n) = {\color{red}a} T \left( \frac{n}{{\color{red}b}} \right) + O(n{\color{red}ᶜ})
$$



---

Antes de todo, no todo algoritmo recursivo se le puede sacar por decirlo asi, el teorema maestro solo los que cumplan la estructura ya mostrada, por lo que solo nos enfocaremos en esos, ahora unos ejemplos de algunos algoritmos que se le pueden sacar teorema maestro y como calcularlo.

Ejemplos:

### Merge Sort
