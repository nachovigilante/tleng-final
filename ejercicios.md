# Ejercicios de práctica

## Ejercicio 1

Dar un algoritmo que decida si dos expresiones regulares denotan el mismo lenguaje. Justificar la correctitud. Analizar la complejidad computacional de peor caso.

### Opción 1

Sea $r_1$ y $r_2$ dos expresiones regulares. Construir un **AFND** $M_1$ que acepte $L(r_1)$ y un **AFND** $M_2$ que acepte $L(r_2)$. Luego, determinizar $M_1$ y $M_2$ para obtener $M_1'$ y $M_2'$, respectivamente. Finalmente, minimizar $M_1'$ y $M_2'$ para obtener $M_1''$ y $M_2''$, respectivamente. Si $M_1''$ y $M_2''$ son isomorfos, entonces $L(r_1) = L(r_2)$.

Esta opción es costosa computacionalmente, ya que hay que determinizar y minimizar los autómatas y chequear isomorfismo de grafos. Esto último es lo más costoso de todo.

TODO: calcular complejidad computacional de peor caso.

### Opción 2

Sea $r_1$ y $r_2$ dos expresiones regulares. Construir un **AFND** $M_1$ que acepte $L(r_1)$, y un **AFND** $M_2$ que acepte $L(r_2)$. Luego, determinizar $M_1$ y $M_2$ para obtener $M_1'$ y $M_2'$, respectivamente. Luego, obtener el complemento de $M_1'$, $M_1''$, y el complemento de $M_2'$, $M_2''$. Ahora, utilizando operaciones sobre autómatas, obtener el autómata $M_3$ que acepte $L(r_1) \triangle L(r_2)$, es decir, la diferencia simétrica de los lenguajes (ésta se puede obtener como $(L(r_1) \cup L(r_2)) \cap ((L(r_1))^c \cap (L(r_2))^c)$). Finalmente, determinizar $M_3$ para obtener $M_3'$, y chequear si $M_3'$ es vacío. Si es vacío, entonces $L(r_1) = L(r_2)$.

Para chequear si $M_3'$ es vacío, se puede utilizar el algoritmo de búsqueda en profundidad (DFS) para recorrer el grafo del autómata. Si se llega a un estado final, entonces el autómata no es vacío. Si se recorren todos los estados y no se llega a un estado final, entonces el autómata es vacío.

Esta opción es mejor que la anterior, ya que no hay que minimizar los autómatas ni chequear isomorfismo de grafos. Sin embargo, sigue siendo costosa computacionalmente, ya que hay que determinizar los autómatas y chequear si el autómata resultante es vacío.

TODO: calcular complejidad computacional de peor caso.

### Opción 3

Podemos utilizar el lema de pumping para decidir si dos expresiones regulares denotan el mismo lenguaje.

TODO: completar

## Ejercicio 2

Demostrar que dada una una gramática libre de contexto $G$ sin símbolos inútiles y no recursiva a derecha. Existe una constante $c$ tal que que para todo par de símbolos no terminales $A$, $B$ para toda cadena de terminales $w$ y para toda cadena de terminales y no terminales $\alpha$, si $A\ \underset{R}{\stackrel{i}{\Rightarrow}}\ \alpha Bw$, entonces $i \leq c^{|w|+2}$.

### Solución

Es literal la demo de la cota para el árbol de derivación pero con $R$ en vez de $L$.

## Ejercicio 3

Dar dos algoritmos distintos para determinar si el lenguaje aceptado por un autómata finito dado es el conjunto de todas las cadenas del alfabeto. Justificar cada uno y dar su complejidad
algorítmica.

### Opción 1

Sea $M = \langle Q, \Sigma, \delta, q_0, F \rangle$ un **AFD**. Construir un **AFD** $M' = \langle Q, \Sigma, \delta', q_0, F' \rangle$ que acepte $\Sigma^*$ y sea mínimo. Luego, minimizar $M'$ para obtener $M''$. Si $M''$ es isomorfo a $M$, entonces $L(M) = \Sigma^*$.

Esta opción es costosa computacionalmente, ya que hay que minimizar los autómatas y chequear isomorfismo de grafos. Esto último es lo más costoso de todo.

TODO: calcular complejidad computacional de peor caso.

### Opción 2

Sea $M = \langle Q, \Sigma, \delta, q_0, F \rangle$ un **AFD**. Construir el complemento de $M$, $M'$. Luego, si $M'$ es vacío, entonces $L(M) = \Sigma^*$.

TODO: completar

## Ejercicio 4

Dar un algoritmo que determine si un lenguaje regular dado es infinito. Justificar y dar la complejidad del algoritmo en el peor caso.

### Opción 1

Armo un **AFND-$\lambda$** $M$ que acepte el lenguaje. Luego busco un ciclo en el grafo de $M$ utilizando DFS. Si encuentro un ciclo y no todas las transiciones son $\lambda$, entonces el lenguaje es infinito. Si no encuentro un ciclo, entonces el lenguaje es finito.

TODO: calcular complejidad computacional de peor caso.

### Opción 2

Usar el lema de pumping para lenguajes regulares. No entiendo bien esto.

TODO: completar

## Ejercicio 5

1. ¿Cuántos autómatas finitos determinísticos con dos estados pueden construirse sobre el alfabeto $\{0, 1\}$?
2. ¿Cuántos autómatas finitos no determinísticos con dos estados pueden construirse sobre el alfabeto $\{0, 1\}$?
3. ¿Cuántos autómatas de pila con dos estados pueden construirse con alfabeto de entrada $A$, alfabeto de pila $Z$, y una cantidad máxima $M$ de símbolos en cada transición?

### Solución

1. - $|Q| = 2$
   - $|\Sigma| = 2$
   - $|\delta| = |Q|^{|Q|*|\Sigma|} = 2^4 = 16$
   - $|F| = 2^{|Q|} = 2^2 = 4$
   - $|q_0| = 2$
   - Entonces, $16 \cdot 4 \cdot 2 = 128$.
2. - $|Q| = 2$
   - $|\Sigma| = 2$
   - $|\delta| = 2^{|Q|^2*|\Sigma|} = 2^8 = 256$
   - $|F| = 2^{|Q|} = 2^2 = 4$
   - $|q_0| = 2$
   - Entonces, $256 \cdot 4 \cdot 2 = 2048$.
3. TODO: completar

## Ejercicio 6

1. Fijados los alfabetos $\Delta$ y $\Gamma$, ¿Cuántos autómatas de pila distintos $\langle Q, \Sigma, \Delta, \Gamma, q_0, F \rangle$ determinístiscos hay, Si $Q$ tiene 5 estados y en cada transición se escriben en la pila 0, 1 o 2 símbolos?

2. ¿Y cuántos no determinísticos?

### Solución

TODO: completar

## Ejercicio 7

Dar la definición de gramática libre de contexto recursiva a derecha. Dar un ejemplo. Dar el algoritmo de eliminación de recursión a derecha (inmediata y no inmediata), su justificación de correctitud, y su complejidad computacional.

### Definición

Sea $G = \langle N, \Sigma, P, S \rangle$ una gramática libre de contexto. Decimos que $G$ es recursiva a derecha si existe un no-terminal $A \in N$ y una cadena $w \in \Sigma^*$ tales que $A \underset{R}{\stackrel{*}{\Rightarrow}}wA$.

### Ejemplos

- $A \rightarrow aA\ |\ b$

Podemos ver que A es recursiva a derecha, ya que $A \Rightarrow aA \Rightarrow aaA \Rightarrow aaaA \Rightarrow ... \Rightarrow a^nA$. En este caso, se produce una recursión a derecha inmediata.

- $A \rightarrow aB$
- $B \rightarrow aA\ |\ b$

Podemos ver que A es recursiva a derecha, ya que $A \Rightarrow aB \Rightarrow aaA \Rightarrow aaaB \Rightarrow aaaaA \Rightarrow ... \Rightarrow a^nB$. En este caso, se produce una recursión a derecha no inmediata.

### Algoritmo de eliminación de recursión a derecha

TODO: completar

## Ejercicio 8

Dar el algoritmo de pasar a forma normal 3-Chomsky. Justificar correctitud y dar la complejidad computacional.

$A \rightarrow a$

$A \rightarrow BC$

$A \rightarrow BCD$

donde $A, B, C, D$ son no terminales y $a$ es terminal. No se permiten producciones $A \rightarrow B$.

Entonces son 3-Chomsky

$S \rightarrow ABC$

$A \rightarrow BDE$

$A \rightarrow a$

$A \rightarrow BC$

No son 3-Chomsky

$A \rightarrow B$

$A \rightarrow ABCDE$ tampoco es 3-Chmsky

$A \rightarrow abcedef$ tampoco es 3-Chomsky

### Solución

**Entrada**: Una gramática libre de contexto $G = \langle V_N, V_T, P, S \rangle$ sin producciones de renombramiento.

**Salida**: Una gramática libre de contexto $G' = \langle V_N', V_T', P', S' \rangle$ equivalente a $G$ en forma normal 3-Chomsky.

**Algoritmo**:

Poner en $P'$:

- $S' \rightarrow S$
- Todas las producciones $A \rightarrow a$ con $A \in V_N$ y $a \in V_T$.
- Todas las producciones $A \rightarrow BC$ con $A, B, C \in V_N$.
- Todas las producciones $A \rightarrow BCD$ con $A, B, C, D \in V_N$.
- Para cada producción $A \rightarrow X_1X_2X_3$ con $X_1$, $X_2$ o $X_3$ o todas terminales, agregar una nueva producción $A' \rightarrow X_1'X_2'X_3'$.
- Para cada producción $A \rightarrow X_1...X_k$ con $k > 3$, $X \in (V_N \cup V_T)$, poner:
  - $A \rightarrow X_1'\langle X_2...X_k \rangle$
  - $\langle X_2...X_k \rangle \rightarrow X_2'\langle X_3...X_k \rangle$
  - ...
  - $\langle X_{k-2}...X_k \rangle \rightarrow X_{k-2}'X_{k-1}'X_k'$
  - Si $X_i \in V_T$, entonces agregar la producción $X_i' \rightarrow X_i$.
  - Si $X_i \in V_N$, entonces $X_i'$ es igual a $X_i$.

**Complejidad temporal**: $O(|P|)$.

**Correctitud**: TODO

## Ejercicio 9

Consideremos el transductor finito dado por una máquina de Mealy $\langle S, \Sigma, \Gamma, \delta, \gamma, S_0, S \rangle$

- $S$ es un conjunto finito de estados
- $\Sigma$ es el alfabeto de entrada
- $\Gamma$ es el alfabeto de salida
- $\delta: S \times \Sigma \rightarrow S$ es la función de transición.
- $\gamma: S \times \Sigma \rightarrow \Gamma$ mapea un estado y un símbolo de entrada a un símbolo de salida
- $S_0$ es un estado inicial
- Todos los esatdos de $S$ son finales.

Adaptar el algoritmo de minimizacion de autómatas finitos a una minimización de maquina Mealy.

**Ayuda**: Definir la relación de equivalencia considerando la función \delta extendida y la función gamma
extendida.

### Solución

Definimos la relación de indistinguibilidad $\equiv$ de la siguiente manera:

Dos estados $q, r \in Q$ son indistinguibles, cuando

$$\forall\alpha\in\Sigma^∗,\ \hat{\delta}(q, \alpha) \in F \iff \hat{\delta}(r, \alpha) \in F$$

$$\land\ \ \hat{\gamma}(q, \alpha) = \hat{\gamma}(r, \alpha)$$

TODO: completar

## Ejercicio 10

1. Demostrar que si un autómata finito es determinístico, accesible, co-accesible y co-determininstico entonces es mínimo.
   - Accesible: todos los estados son accesibles desde el estado inicial.
   - Co-accesible: todos los estados tienen un camino en el autómata hasta un estado final
   - Co-determininstico: hay un único estado final y no hay transiciones $\delta(p, a) = q$ y $\delta(r, a) = q$,
2. Demostrar que la recíproca de la afirmación en 1. no siempre es cierta.

### Solución

1. TODO: completar
2. TODO: completar

## Ejercicio 11

Demostrar que dada una gramática regular a derecha se puede obtener una gramática regular a izquierda equivalente.

### Opción 1

Eliminar recursión a derecha.

### Opción 2

Armamos un **AFD** $M$ que acepte el lenguaje. Y ...

TODO: completar

## Ejercicio 12

Dado un autómata finito no determinístico $A$ pero sin transiciones lambda dar un algoritmo que construye el autómata finito no determinístico que acepta el lenguaje $L(A)L(A)^R$.

Demostrar por inducción en el largo de las cadenas que el algoritmo es correcto. Determinar la complejidad computacional del algoritmo.

### Solución

**Entrada**: Un **AFND** $M = \langle Q, \Sigma, \delta, q_0, F \rangle$ sin transiciones lambda.

**Salida**: Un **AFND** $M' = \langle Q', \Sigma, \delta', q_0', F' \rangle$ que acepta $L(M)L(M)^R$.

**Algoritmo**:

- Determinizar $M$ para obtener $M'$.
- Obtener el reverso de $M'$, $M''$.
- Concatenar $M$ y $M''$ para obtener $M'''$.
- $M'''$ acepta $L(M)L(M)^R$.

**Complejidad temporal**: TODO

**Correctitud**:

Demostramos por inducción en el largo de las cadenas de forma $ww^r$ que el algoritmo es correcto.

**Caso base**: $|w| = 0 \Rightarrow w = \lambda \Rightarrow ww^r = \lambda\lambda^r = \lambda$.

Si $w \in L(M)$, entonces $M$ acepta $\lambda$. Es decir, existe un camino entre $q_0$ y algún $q_f \in F$ que acepta $\lambda$. Entonces, luego de determinizar y obtener el reverso, $M''$ tiene un camino entre $q_f''$ y $q_0''$ que acepta $\lambda$ ($q_0'' \in F''$). Luego, como $M'''$ es la concatenación de $M$ y $M''$, entonces $M'''$ tiene un camino entre $q_0$ y $q_0''$ que acepta $\lambda$. Por lo tanto, $M'''$ acepta $\lambda$.

Si $w \notin L(M)$, entonces $M$ no acepta $\lambda$. Es decir, no existe un camino entre $q_0$ y algún $q_f \in F$ que acepta $\lambda$. Entonces, análogamente al caso anterior, $M'''$ no acepta $\lambda$.

**Paso inductivo**: $|w| = k$

Si $w \in L(M)$, entonces $M$ acepta $w$. Es decir, existe un camino entre $q_0$ y algún $q_f \in F$ que acepta $w$. Entonces, luego de determinizar y obtener el reverso, $M''$ tiene un camino entre $q_f''$ y $q_0''$ que acepta $w^r$ ($q_0'' \in F''$). Luego, como $M'''$ es la concatenación de $M$ y $M''$, entonces $M'''$ tiene un camino entre $q_0$ y $q_0''$ que acepta $w^r$. Por lo tanto, $M'''$ acepta $w^r$.

TODO: esto no es inductivo, es por casos. Hay que hacerlo inductivo.

## Ejercicio 13

Definimos un autómata de pila de doble entrada $P = \langle Q, \Sigma, \tau, \Gamma, \delta, q_0, Z_0, F \rangle$ donde $\delta : Q \times \Sigma \cup \{\lambda\} \times \tau \cup \{\lambda\} \times \Gamma \rightarrow P(Q \times \Gamma^∗)$.

La función $\delta$ es tal que las transiciones lambda ocurren en ambas cintas a la vez. Es decir, no hay transiciones que lean de una cinta y no de la otra.

Demostrar que para todo automata de pila de doble entrada que acepta por estado final siempre se puede encontrar otro equivalente que acepta por pila vacía.

### Solución

Dado un autómata de pila de doble entrada $P = \langle Q, \Sigma, \tau, \Gamma, \delta, q_0, Z_0, F \rangle$ que acepta por estado final, construimos un autómata de pila de simple entrada $P' = \langle Q, \Delta, \Gamma, \delta', q_0, Z_0, F \rangle$ que acepta por estado final, donde $\Delta = \Sigma \times \tau$. Para esto, definimos la función de transición $\delta'$ de la siguiente manera:

$$\delta'(q, (a, b), Z) = \{(q', \gamma)\ |\ (q', \gamma) \in \delta(q, a, b, Z)\}$$

$$\delta'(q, (\lambda, \lambda), Z) = \{(q', \gamma)\ |\ (q', \gamma) \in \delta(q, \lambda, \lambda, Z)\}$$

Luego, como sabemos que todo autómata de pila de simple entrada que acepta por estado final es equivalente a uno que acepta por pila vacía, entonces $P'$ es equivalente a un autómata de pila de simple entrada $P'' = \langle Q, \Delta, \Gamma, \delta'', q_0, Z_0, \emptyset \rangle$ que acepta por pila vacía. Por lo tanto, $P$ es equivalente a $P''$. Finalmente, podemos construir un autómata de pila de doble entrada $P''' = \langle Q, \Sigma, \tau, \Gamma, \delta''', q_0, Z_0, \emptyset \rangle$ que acepta por pila vacía, donde $\delta'''$ es la función de transición de $P''$ extendida a dos cintas (proceso inverso al que hicimos al principio).

## Ejercicio 14

Dado un automata de pila $P$ determinístico dar el autómata de pila no determinístico que acepta $L' = \{ww^R : w \in L(P)\}$ donde $w^R$ es la reversa de $w$, es decir si $w = abc$ entonces $w^R = cba$.

### Solución

Los pasos a seguir son los siguientes:

1. Obtener el reverso de $P'$, $P''$.
2. Concatenar $P$ y $P''$ para obtener $P'''$.

Luego, $P'''$ acepta $L'$.

## Ejercicio 15

Mostrar que si $L$ es un lenguaje aceptado por un autómata de pila determinístico por pila vacía entonces ninguna palabra de $L$ es prefijo propio de otra palabra de $L$. ¿Vale lo mismo en caso de que el autómata de pila sea no-determinístico?

### Solución

Sea $w \in L$. Supongamos que existe $w' \in L$ tal que $w$ es prefijo propio de $w'$. Entonces, existe un estado $p \in Q$ tal que $(q_0, w, Z_0) \stackrel{*}{\vdash} (p, \lambda, \lambda)$. Además, como $P$ es determinístico, $(p, \lambda, \lambda)$ es la única configuración posible producto de la derivación de $(q_0, w, Z_0)$.

Por lo tanto, si iniciamos con la configuración de $(q_0, w', Z_0) = (q_0, wv, Z_0)$, entonces $(q_0, wv, Z_0) \stackrel{*}{\vdash} (p, v, \lambda)$. Luego, como la pila está vacía, entonces $v = \lambda$.

TODO: completar

## Ejercicio 16

Dado $R$ un lenguaje regular, y dado $L$ un lenguaje libre de contexto deterministico, ¿Es decidible si $L=R$? Es decir, ¿hay un algoritmo capaz de decidir la igualdad? En caso de que sí, dar tal algoritmo y justificar. En caso de que no, dar la demostración de indecibilidad.

### Solución

$L=R \iff (L \cap \overline{R}) \cup (\overline{L} \cap R) = \varnothing$. Esto es decidible dado que los lenguajes libres de contexto determinísticos son cerrados bajo complemento e intersección con lenguajes regulares, los lenguajes libres de contexto están cerrados bajo unión, y la igualdad de lenguajes libres de contexto con el lenguaje vacío es decidible.

## Ejercicio 17

Dado $R$ un lenguaje regular, y dado $L$ un lenguaje libre de contexto determinístico, ¿Es decidible si R está incluido en $L$?

### Solución

$R \subseteq L \iff \overline{L} \cap R = \varnothing$. Como los lenguajes libres de contexto determinísticos son cerrados bajo complemento e intersección con lenguajes regulares, y la igualdad de lenguajes libres de contexto con el lenguaje vacío es decidible, entonces $R \subseteq L$ es decidible.

## Ejercicio 18

Dar un algoritmo que transforma una gramatica $LL(k)$ en otra $LL(k)$ de la forma $A \rightarrow a\alpha$ y $A \rightarrow \lambda$. Donde $a$ es terminal y $A$ es no terminal. Argumentar por qué todas las producciones admiten esta transformación (la gramática original no es recursiva a izquierda).

### Solución

TODO: completar

## Ejercicio 19

Considerar la gramatica $S \rightarrow SS|a$.

Contar la cantidad de árboles de derivacion más a la izquierda de $a^n$.

**AYUDA**: Ensayar con $n = 1, n = 2, n = 3, n = 4, n = 5$ hasta conseguir la forma general.

**Solucion** $X_n = \sum_{i+j=n,\ i,j \not= 0}{X_iX_j}$ con $X_1 = 1$ y $X_{n+1} = comb(2n, n)/(n + 1)$

### Solución

TODO: completar

## Ejercicio 20

Dar un algoritmo que transforme cada gramatica libre de contexto $G$ en otra $G'$ que reconoce el mismo lenguaje pero es tal que si $X_1...X_k$ es el lado derecho de una producción entonces todos los símbos $X_1, ..., X_k$ son distintos. Justificar la correctitud y dar la complejidad del algoritmo.

### Solución

TODO: completar

## Ejercicio 21

Dar un algoritmo que transforme cada gramática libre de contexto $G$ sin producciones $A \rightarrow \lambda$ en otra $G'$ que reconoce el mismo lenguaje pero es tal que ninguna producción tiene un lado derecho con dos no-terminales seguidos. Justificar la correctitud y dar la complejidad del algoritmo.

**Ayuda**: Pasar primero a forma normal de Greibach.

### Solución

TODO: completar

## Ejercicio 22

Dar un algoritmo que transforme cada gramatica libre de contexto G sin producciones $A \rightarrow \lambda$ en otra $G'$ que reconoce el mismo lenguaje pero tal que cada producción es de la forma $A \rightarrow a\alpha$, con a un símbolo terminal y $\alpha$ una cadena de no-terminales (puede ser vacía). Justificar la correctitud y dar la complejidad del algoritmo.

**Ayuda**: Definir un orden parcial $<$ entre los no terminales de $G$ donde si $A \rightarrow B\beta$ entonces $A < B$. Iterar cambiando la gramática donde cada produccion con cabeza $A$ tenga un cuerpo que
sea un terminal o con un no-terminal $B$ donde $A < B$.

**Otra Ayuda**: esta es la forma normal de Greibach.

### Solución

TODO: completar

## Ejercicio 23

Una gramática libre de contexto es lineal si todas las producciones son de la forma $A \rightarrow aBx$ y $A \rightarrow w$, con $a \in T, x, w \in T^∗$, y $A, B \in N$.

Mostrar que todo lenguaje lineal sin la palabra vacía tiene una gramática donde las producciones son de la forma $A \rightarrow aB$, $A \rightarrow Ba$ o $A \rightarrow a$

### Solución

TODO: completar

## Ejercicio 24

Dada $G = \langle V_N, V_T, P, S \rangle$ definir un orden lineal de los símbolos en N, $A_1, < A_2 < ... < A_n$ que respete el orden parcial inducido por la relación de derivación: si $A \stackrel{+}{\Rightarrow} B\alpha$ entonces $A < B$.

Dar la complejiiad del algoritmo de eliminación de la recursión a izquierda que opera sobre este nuevo orden.

### Solución

TODO: completar

## Ejercicio 25

Dar un algoritmo que dado un automata finito que reconoce un lenguaje infinito,
lo transforma en otro que reconoce el mismo lenguaje y tiene al menos el doble de estados que el mínimo. Demostrar que el algoritmo es correcto.

### Solución

TODO: completar

## Ejercicio 26

Dar un algoritmo que codeterminice un automata finito.

### Solución

TODO: completar

## Ejercicio 27

Dar un algoritmo que decide si un automata de pila determinisitico reconoce el
lenguaje $\Sigma^*$.

### Solución

Construir el complemento del autómata de pila, $P'$. Luego, ver si $L(P') = \varnothing$.
