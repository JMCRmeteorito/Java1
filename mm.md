# Argumento de Corrección del Algoritmo *FastAlgorithm*

El algoritmo presentado implementa la multiplicación de dos números enteros \(a\) y \(b\) a través de sumas sucesivas.

---

## Definición del algoritmo

El método `multiply(a, b)` utiliza una función auxiliar recursiva de la forma:

\[
\text{multiplyAux}(a, b, acc)
\]

donde:
- \(a\) es el primer operando,
- \(b\) es el segundo operando (contador decreciente),
- \(acc\) es el acumulador que guarda el resultado parcial.

La definición de la función es:

\[
\text{multiplyAux}(a, b, acc) =
\begin{cases}
acc & \text{si } b = 0 \\
\text{multiplyAux}(a, b-1, acc+a) & \text{si } b > 0
\end{cases}
\]

---

## Invariante

En cada llamada recursiva, el acumulador \(acc\) cumple con la siguiente propiedad:

\[
acc = a \cdot (b_0 - b)
\]

donde \(b_0\) es el valor inicial de \(b\).  
Esto significa que el acumulador siempre contiene la suma parcial correcta correspondiente a las iteraciones ya realizadas.

---

## Prueba de corrección

### Caso base:
Si \(b = 0\), se devuelve directamente:

\[
\text{multiplyAux}(a, 0, acc) = acc
\]

De acuerdo con el invariante:

\[
acc = a \cdot (b_0 - 0) = a \cdot b_0
\]

por lo tanto, el resultado es correcto.

---

### Caso inductivo:
Supongamos que para un cierto \(b = k\) el invariante se cumple:

\[
acc = a \cdot (b_0 - k)
\]

Ahora, al ejecutar un paso más:

\[
\text{multiplyAux}(a, k, acc) \to \text{multiplyAux}(a, k-1, acc+a)
\]

El nuevo acumulador será:

\[
acc' = acc + a = a \cdot (b_0 - k) + a = a \cdot (b_0 - (k-1))
\]

Lo cual mantiene el invariante.  
Por inducción, el invariante se cumple en todas las llamadas recursivas.

---
