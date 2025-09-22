# Informe sobre el Fast Algorithm (Exponenciación rápida)

## Introducción

El **Fast Algorithm** (o algoritmo de exponenciación rápida) es una técnica eficiente para calcular potencias de la forma:

\[
a^n, \quad a \in \mathbb{R}, \; n \in \mathbb{N}
\]

Este algoritmo se basa en la descomposición binaria del exponente, reduciendo el número de multiplicaciones necesarias.  
En lugar de realizar \(n\) multiplicaciones, se logra una complejidad de:

\[
\mathcal{O}(\log n)
\]

---

## Definición del Algoritmo

El algoritmo recursivo puede definirse de la siguiente manera:

\[
\text{FastExp}(a, n) =
\begin{cases}
1, & \text{si } n = 0 \\
a \cdot \text{FastExp}(a, n-1), & \text{si } n \text{ es impar} \\
\left(\text{FastExp}(a, \tfrac{n}{2})\right)^2, & \text{si } n \text{ es par}
\end{cases}
\]

---

## Ejemplo de Ejecución

Queremos calcular:

\[
3^5
\]

1. Como \(n = 5\) es impar:
   \[
   3^5 = 3 \cdot \text{FastExp}(3, 4)
   \]

2. Ahora \(n = 4\) es par:
   \[
   \text{FastExp}(3, 4) = \left(\text{FastExp}(3, 2)\right)^2
   \]

3. Luego \(n = 2\) es par:
   \[
   \text{FastExp}(3, 2) = \left(\text{FastExp}(3, 1)\right)^2
   \]

4. Finalmente \(n = 1\) es impar:
   \[
   \text{FastExp}(3, 1) = 3 \cdot \text{FastExp}(3, 0)
   \]

5. Caso base:
   \[
   \text{FastExp}(3, 0) = 1
   \]

---

## Estado de la Pila de Llamados

A continuación se muestra el estado de la pila de llamados en cada paso utilizando **Mermaid**.

### Paso 1: Llamada inicial
```mermaid
stack
  direction BT
  FastExp(3,5)
```

### Paso 2: Expansión con \(n=5\) (impar)
```mermaid
stack
  direction BT
  FastExp(3,4)
  FastExp(3,5)
```

### Paso 3: Expansión con \(n=4\) (par)
```mermaid
stack
  direction BT
  FastExp(3,2)
  FastExp(3,4)
  FastExp(3,5)
```

### Paso 4: Expansión con \(n=2\) (par)
```mermaid
stack
  direction BT
  FastExp(3,1)
  FastExp(3,2)
  FastExp(3,4)
  FastExp(3,5)
```

### Paso 5: Expansión con \(n=1\) (impar)
```mermaid
stack
  direction BT
  FastExp(3,0)
  FastExp(3,1)
  FastExp(3,2)
  FastExp(3,4)
  FastExp(3,5)
```

### Paso 6: Caso base
```mermaid
stack
  direction BT
  FastExp(3,0) = 1
```

---

## Verificación Matemática

Comprobamos el resultado:

\[
\begin{align}
3^5 &= 3 \cdot (3^4) \\
&= 3 \cdot \big((3^2)^2\big) \\
&= 3 \cdot \big((9)^2\big) \\
&= 3 \cdot 81 \\
&= 243
\end{align}
\]

El algoritmo obtiene el resultado correcto, y la recursión termina en el caso base \(n=0\).

---

## Conclusión

- El **Fast Algorithm** reduce la complejidad de \(\mathcal{O}(n)\) a \(\mathcal{O}(\log n)\).
- El proceso recursivo se entiende mejor visualizando la **pila de llamados**.
- La corrección se demuestra con **notación matemática clara** y el seguimiento del caso base.

---
