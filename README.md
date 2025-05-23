# Métodos numéricos para la solución de sistemas de ecuaciones lineales

Este documento presenta una recopilación de apuntes teóricos sobre los métodos numéricos más utilizados para resolver sistemas de ecuaciones lineales, fundamentales en ingeniería, física, economía, entre otras disciplinas donde se modelan fenómenos mediante ecuaciones algebraicas.

## Eliminación Gaussiana

### Definición
Es un método directo que convierte un sistema de ecuaciones lineales en una forma escalonada mediante operaciones fila. Posteriormente, se aplica sustitución regresiva para encontrar las soluciones.

### Aplicaciones
- Análisis estructural.
- Resolución de circuitos eléctricos.
- Resolución de sistemas con coeficientes constantes.

### Ventajas
- Proceso sistemático y determinista.
- Puede implementarse fácilmente en algoritmos.

### Desventajas
- Sensible a divisiones por cero.
- No es eficiente para matrices muy grandes o dispersas.

## Método de Gauss-Jordan

### Definición
Extiende la eliminación Gaussiana hasta lograr la forma escalonada reducida, donde la matriz queda diagonalizada y permite obtener directamente las soluciones del sistema.

### Aplicaciones
- Cálculo de matrices inversas.
- Resolución de sistemas sin necesidad de sustitución regresiva.

### Ventajas
- Permite comprobar si un sistema tiene solución única, ninguna o infinitas.
- Automatiza completamente la resolución del sistema.

### Desventajas
- Mayor número de operaciones que Gauss.
- Menor eficiencia computacional.

## Método de Jacobi

### Definición
Es un método iterativo que parte de una estimación inicial de las soluciones y aplica una fórmula de actualización en cada iteración. Requiere que el sistema sea diagonalmente dominante para garantizar convergencia.

### Aplicaciones
- Simulación de procesos físicos.
- Métodos numéricos en dinámica de fluidos.
- Grandes sistemas esparcidos.

### Ventajas
- Fácil de paralelizar.
- Independencia entre las actualizaciones de las variables.

### Desventajas
- Convergencia lenta.
- Sensible a errores acumulados.

## Método de Gauss-Seidel

### Definición
También es un método iterativo, pero a diferencia de Jacobi, actualiza cada variable usando inmediatamente los nuevos valores calculados en la misma iteración.

### Aplicaciones
- Solución de ecuaciones en simulaciones numéricas.
- Métodos de elementos finitos y diferencias finitas.

### Ventajas
- Convergencia más rápida que Jacobi.
- Útil para matrices dispersas.

### Desventajas
- Menor paralelismo.
- También requiere condiciones de convergencia (como diagonal dominante).

## Recomendaciones generales

- Verificar si el sistema es consistente antes de aplicar cualquier método.
- Utilizar métodos iterativos para sistemas grandes o dispersos.
- Utilizar métodos directos si se requiere precisión exacta en pocos pasos.

## Bibliografía

- Chapra, S. C., & Canale, R. P. (2007). *Métodos numéricos para ingenieros*. McGraw-Hill.
- Burden, R. L., & Faires, J. D. (2011). *Análisis numérico*. Cengage Learning.
