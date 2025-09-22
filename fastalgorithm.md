# Argumentación de Corrección del FastAlgorithm

## Código

```scala
package taller1 
import scala.annotation.tailrec

class FastAlgorithm  {
  def multiply(a:Int, b:Int): Int = {
    @tailrec
    def multiplyAux(a:Int, b:Int, acc:Int):Int = {
      if (b == 0) acc
      else multiplyAux(a, b - 1, acc + a)
    }
    multiplyAux(a, b, 0)
  }
}
```

---

## Idea General del Algoritmo

El algoritmo `FastAlgorithm` implementa la multiplicación de dos enteros `a` y `b` mediante **sumas repetidas**.  
En lugar de usar directamente el operador `*`, el procedimiento acumula la suma de `a` tantas veces como lo indique `b`.

---

## Invariante del ciclo

Definimos la función auxiliar:

\[
multiplyAux(a, b, acc)
\]

donde:

- \(a\): primer número (constante).  
- \(b\): contador decreciente.  
- \(acc\): acumulador que guarda el resultado parcial.  

**Invariante**: En cada llamada recursiva se cumple que

\[
acc + a \cdot b = a \cdot b_{0}
\]

donde \(b_{0}\) es el valor inicial de \(b\).

---

## Caso base

Cuando \(b = 0\):

\[
multiplyAux(a, 0, acc) = acc
\]

De acuerdo con el invariante:

\[
acc + a \cdot 0 = acc = a \cdot b_{0}
\]

por lo tanto, el algoritmo retorna el valor correcto.

---

## Caso inductivo

Supongamos que el invariante se cumple para un valor \(b = k\).  
Es decir:

\[
acc + a \cdot k = a \cdot b_{0}
\]

Ahora, en la siguiente llamada recursiva:

\[
multiplyAux(a, k, acc) \;\;\longrightarrow\;\; multiplyAux(a, k-1, acc + a)
\]

Aplicamos el invariante:

\[
(acc + a) + a \cdot (k-1) = acc + a \cdot k
\]

lo cual sigue siendo igual a \(a \cdot b_{0}\).  
Por lo tanto, el invariante se mantiene.

---

## Terminación

En cada llamada recursiva, el parámetro \(b\) disminuye en 1:

\[
b \mapsto b - 1
\]

Dado que \(b\) es un entero no negativo, eventualmente se llega a \(b = 0\), donde el algoritmo retorna.  
Por tanto, el algoritmo **termina siempre**.

---

## Corrección total

Como el invariante se mantiene en cada paso y el caso base retorna el resultado correcto, podemos concluir:

\[
multiply(a, b) = a \cdot b
\]

para todo par de enteros no negativos \(a, b\).
