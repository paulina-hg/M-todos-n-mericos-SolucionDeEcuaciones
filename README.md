# Tema 3: Resolución de sistemas de ecuaciones lineales

Este tema aborda diferentes métodos numéricos para resolver sistemas de ecuaciones lineales. A continuación se presenta una descripción detallada de cada método, junto con su fórmula, seudocódigo, enlace al código en Java y un ejercicio resuelto distinto para cada uno.

---

## 1. Eliminación Gaussiana con pivoteo parcial

### Definición

Consiste en transformar la matriz aumentada del sistema en una matriz triangular superior mediante eliminación hacia adelante, con intercambio de filas (pivoteo parcial) para mejorar la estabilidad numérica. Luego se resuelve mediante sustitución regresiva.

### Fórmula

Se transforma el sistema $A \vec{x} = \vec{b}$ en una forma triangular superior aplicando operaciones elementales por filas:
$a_{ij}^{(k)} = a_{ij}^{(k-1)} - \frac{a_{ik}^{(k-1)}}{a_{kk}^{(k-1)}} a_{kj}^{(k-1)}$

### Seudocódigo

```
Para k de 0 a n-1:
    Buscar fila con mayor valor absoluto en la columna k y hacer pivoteo
    Para i de k+1 a n:
        factor = A[i][k] / A[k][k]
        Para j de k a n+1:
            A[i][j] = A[i][j] - factor * A[k][j]

Sustitución regresiva para obtener las soluciones
```
### Código
Puedes consultar el código Java aquí:  
[EliminacionGaussianaConPivote.java](https://github.com/paulina-hg/M-todos-n-mericos-SolucionDeEcuaciones/blob/main/EliminacionGaussianaConPivote.java)

### Ejercicio resuelto

Ejercicio:
Un ingeniero civil está diseñando un puente y necesita calcular las fuerzas internas en los miembros de una estructura estática. El sistema de ecuaciones que representa el equilibrio de fuerzas es el siguiente:
Sistema: 
```
2x + y - z = 8
-3x - y + 2z = -11
-2x + y + 2z = -3
```
Se desea aplicar el método de Eliminación Gaussiana con pivoteo parcial para encontrar los valores de x, y, y z que satisfacen el sistema.

Ejecución de código: 

```
Ingrese el tamaño de la matriz: 3
Ingrese la matriz aumentada:
2 1 -1 8 
-3 -1 2 -11
-2 1 2 -3 

Matriz aumentada inicial:
    2.0000    1.0000   -1.0000    8.0000
   -3.0000   -1.0000    2.0000  -11.0000
   -2.0000    1.0000    2.0000   -3.0000

Matriz después de eliminación:
   -3.0000   -1.0000    2.0000  -11.0000
    0.0000    1.6667    0.6667    4.3333
    0.0000    0.0000    0.2000   -0.2000

Soluciones:
x1 = 2.0000
x2 = 3.0000
x3 = -1.0000
```

---

## 2. Método de Gauss-Jordan

### Definición

Consiste en transformar la matriz aumentada en su forma escalonada reducida mediante operaciones elementales por filas, obteniendo directamente las soluciones sin necesidad de sustitución regresiva.

### Fórmula

$a_{ij}^{(k)} = \frac{a_{ij}^{(k-1)} - a_{ik}^{(k-1)}a_{kj}^{(k-1)} / a_{kk}^{(k-1)}}{a_{kk}^{(k-1)}}$

### Seudocódigo

```
Para cada fila i:
    Si el pivote es cero, buscar otra fila y hacer intercambio
    Dividir fila i por el pivote
    Para cada otra fila j:
        Restar un múltiplo de la fila i para anular el valor en la columna i
```

### Código
Puedes consultar el código Java aquí:  
[GaussJordan.java](https://github.com/paulina-hg/M-todos-n-mericos-SolucionDeEcuaciones/blob/main/GaussJordan.java)


### Ejercicio resuelto
Problema: Una empresa química necesita determinar las cantidades exactas de tres sustancias para una reacción equilibrada. Las ecuaciones químicas conducen al siguiente sistema:

```
2x + y = 5
4x - 6y = -2
```
Utilice el método de Gauss-Jordan para determinar los valores de a, b y c necesarios para equilibrar la reacción.
Ejecución de código: 

```
Ingrese el tamaño de la matriz: 
2
Ingrese la matriz aumentada:
2 1 5 
4 -6 -2 
Matriz inicial:
  2.0000   1.0000   5.0000
  4.0000  -6.0000  -2.0000

Matriz final (forma escalonada reducida):
  1.0000   0.0000   1.7500
 -0.0000   1.0000   1.5000

Soluciones:
x1 = 1.7500
x2 = 1.5000
```

---

## 3. Método de Gauss-Seidel

### Definición

Método iterativo que mejora la aproximación de las soluciones usando los valores más recientes. Es eficiente si el sistema es diagonalmente dominante.

### Fórmula

$x_i^{(k+1)} = \frac{1}{a_{ii}} \left( b_i - \sum_{j=1}^{i-1} a_{ij}x_j^{(k+1)} - \sum_{j=i+1}^n a_{ij}x_j^{(k)} \right)$

### Seudocódigo

```
Inicializar x = 0
Repetir hasta converger o alcanzar máximo de iteraciones:
    Para cada i:
        Calcular nueva x_i usando fórmula de Gauss-Seidel
        Actualizar la diferencia máxima
```

### Código
Puedes consultar el código Java aquí:  
[MetodoGaussSeidel.java](https://github.com/paulina-hg/M-todos-n-mericos-SolucionDeEcuaciones/blob/main/MetodoGaussSeidel.java)

### Ejercicio resuelto
Problema: Un investigador climático modela temperaturas en una región usando una red de sensores que generan el siguiente sistema lineal:

```
10x + 2y - 1z = 27
-3x - 6y + 2z = -61.5
x + y + 5z = -21.5
```

Ejecución de código: 

```
Ingrese el tamaño de la matriz: 
3
Ingrese el valor en la posición [1][1]: 
10 
Ingrese el valor en la posición [1][2]: 
2
Ingrese el valor en la posición [1][3]: 
-1
Ingrese el valor en la posición [1][4]: 
27
Ingrese el valor en la posición [2][1]: 
-3
Ingrese el valor en la posición [2][2]: 
-6
Ingrese el valor en la posición [2][3]: 
2
Ingrese el valor en la posición [2][4]: 
-61.5
Ingrese el valor en la posición [3][1]: 
1
Ingrese el valor en la posición [3][2]: 
1
Ingrese el valor en la posición [3][3]: 
5
Ingrese el valor en la posición [3][4]: 
-21.5

Matriz original:
   10.00     2.00    -1.00    27.00
   -3.00    -6.00     2.00   -61.50
    1.00     1.00     5.00   -21.50 

Matriz aumentada:
   10.00     2.00    -1.00 |    27.00
   -3.00    -6.00     2.00 |   -61.50
    1.00     1.00     5.00 |   -21.50

Soluciones (después de 9 iteraciones):
x1 =   0.5000
x2 =   8.0000
x3 =  -6.0000
```

---

## 4. Método de Jacobi

### Definición

Método iterativo que utiliza únicamente los valores de la iteración anterior. Requiere que el sistema sea diagonalmente dominante para garantizar la convergencia.

### Fórmula

$x_i^{(k+1)} = \frac{1}{a_{ii}} \left( b_i - \sum_{j \neq i} a_{ij}x_j^{(k)} \right)$

### Seudocódigo

```
Inicializar x = 0
Repetir hasta converger o alcanzar máximo de iteraciones:
    Para cada i:
        Calcular nuevo x_i usando valores anteriores
    Verificar convergencia comparando x viejo y nuevo
```

### Código
Puedes consultar el código Java aquí:  
[MetodoJacobi.java](https://github.com/paulina-hg/M-todos-n-mericos-SolucionDeEcuaciones/blob/main/MetodoJacobi.java)

### Ejercicio resuelto
Problema: En una red eléctrica, las tensiones en tres nodos están relacionadas por el siguiente sistema:

```
10x + y + z = 12
2x + 10y + z = 13
2x + 2y + 10z = 14
```

Ejecución de código: 

```
Caso 1:
Matriz original:
 10.0000  1.0000  1.0000 12.0000
  2.0000 10.0000  1.0000 13.0000
  2.0000  2.0000 10.0000 14.0000

Soluciones (después de 13 iteraciones):
x1 = 1.0000
x2 = 1.0000
x3 = 1.0000
```

---
### Bibliografía
Chapra, S. C., & Canale, R. P. (2007). Métodos numéricos para ingenieros. McGraw-Hill.
