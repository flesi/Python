# Cheatsheet de NumPy

NumPy es una biblioteca fundamental para la computación científica en Python. Ofrece soporte para arrays multidimensionales y funciones matemáticas de alto rendimiento.

## Inicialización

Para usar **NumPy**, primero debes importar la librería:

```python
import numpy as np
```

np: Se usa como alias para acceder a las funciones de NumPy.

## Creación de Arrays
Los arrays de NumPy son estructuras de datos básicas que permiten almacenar colecciones de elementos homogéneos en múltiples dimensiones.

### Array unidimensional

```python
arr1 = np.array([1, 2, 3, 4, 5])
```
Resultado

| Índice | Valor|
|--------|------|
| 0      | 1    |
| 1      | 2    |
| 2      | 3    |
| 3      | 4    |
| 4      | 5    |


### Array bidimensional

```python
arr2 = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])
```
Resultado

|     | 0   | 1   | 2   |
|-----|-----|-----|-----|
| 0   | 1   | 2   | 3   |
| 1   | 4   | 5   | 6   |
| 2   | 7   | 8   | 9   |


### Creación de arrays comunes

NumPy ofrece funciones rápidas para crear arrays predefinidos o con secuencias:

```python
np.zeros((2, 3))    # Matriz de ceros
np.ones((2, 3))     # Matriz de unos
np.arange(0, 10, 2) # Array con secuencia de números del 0 al 10 con pasos de 2
np.linspace(0, 1, 5) # Array con 5 números equiespaciados entre 0 y 1
np.eye(3)           # Matriz identidad de tamaño 3x3
np.random.rand(2, 3) # Matriz de 2x3 con números aleatorios uniformes
```

Ejemplo de `arange`

```python
arr = np.arange(0, 10, 2)
```

Resultado 
| Índice | Valor|
|--------|------|
| 0      | 0    |
| 1      | 2    |
| 2      | 4    |
| 3      | 6    |
| 4      | 8    |



## Selección e Indexación

Puedes acceder a los elementos de un array de manera similar a las listas de Python, usando índices.

```python
arr = np.array([1, 2, 3, 4, 5])
arr[0]      # Devuelve el primer elemento (1)
arr[-1]     # Devuelve el último elemento (5)
arr[1:3]    # Devuelve un slice del array: [2, 3]
```

### Indexación en arrays 2D
```python
arr2 = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])
arr2[0, 2]     # Devuelve el elemento en la primera fila, tercera columna (3)
arr2[:, 1]     # Devuelve todos los elementos de la segunda columna: [2, 5, 8]
arr2[1, :]     # Devuelve todos los elementos de la segunda fila: [4, 5, 6]
```

## Modificación de Arrays

Modifica los elementos de un array usando asignaciones.

```python
arr = np.array([1, 2, 3, 4, 5])
arr[0] = 10    # Cambia el primer elemento por 10: [10, 2, 3, 4, 5]
arr2[1, 1] = 0 # Cambia el elemento (1, 1) en un array 2D por 0
```

También puedes modificar porciones del array:

```python
arr[0:3] = 100  # Cambia los primeros tres elementos a 100: [100, 100, 100, 4, 5]
```

## Operaciones Matemáticas

NumPy soporta operaciones matemáticas entre arrays y números escalares.

```python
arr = np.array([1, 2, 3, 4, 5])
arr + 10      # Suma 10 a cada elemento: [11, 12, 13, 14, 15]
arr * 2       # Multiplica cada elemento por 2: [2, 4, 6, 8, 10]
arr - 1       # Resta 1 a cada elemento: [0, 1, 2, 3, 4]
```

### Operaciones entre arrays
```python
arr1 = np.array([1, 2, 3])
arr2 = np.array([4, 5, 6])
arr1 + arr2    # Suma elemento a elemento: [5, 7, 9]
arr1 * arr2    # Multiplica elemento a elemento: [4, 10, 18]
```

### Funciones Universales (ufuncs)

NumPy tiene funciones matemáticas vectorizadas de alto rendimiento llamadas ufuncs:

```python
np.sqrt(arr)     # Raíz cuadrada de cada elemento
np.sin(arr)      # Seno de cada elemento
np.log(arr)      # Logaritmo natural de cada elemento
np.sum(arr)      # Suma total de los elementos
np.mean(arr)     # Promedio de los elementos
np.max(arr)      # Máximo valor en el array
np.min(arr)      # Mínimo valor en el array
np.std(arr)      # Desviación estándar
```

## Redimensionamiento y Transposición

Para cambiar la forma de los arrays:

```python
arr = np.array([[1, 2, 3], [4, 5, 6]])
arr.reshape(3, 2)  # Cambia a una matriz 3x2: [[1, 2], [3, 4], [5, 6]]
arr.T              # Transpone la matriz
```


## Concatenación y División de Arrays

### Concatenar arrays
```python
arr1 = np.array([1, 2, 3])
arr2 = np.array([4, 5, 6])
np.concatenate([arr1, arr2])  # Resultado: [1, 2, 3, 4, 5, 6]
```
### División de arrays
```python
arr = np.array([1, 2, 3, 4, 5, 6])
np.split(arr, 3)  # Divide en 3 arrays: [array([1, 2]), array([3, 4]), array([5, 6])]
```

## Funciones Lógicas y Comparación

NumPy permite realizar comparaciones y operaciones lógicas:


```python
arr = np.array([1, 2, 3, 4, 5])
arr > 3         # Devuelve un array booleano: [False, False, False, True, True]
arr == 2        # Devuelve: [False, True, False, False, False]
np.any(arr > 4) # Verifica si algún elemento es mayor que 4: True
np.all(arr < 6) # Verifica si todos los elementos son menores que 6: True
```

## Operaciones Avanzadas

NumPy tiene funcionalidades adicionales como ordenar o buscar elementos:


```python
arr = np.array([5, 2, 9, 1, 6])
np.sort(arr)          # Ordena los elementos: [1, 2, 5, 6, 9]
np.argsort(arr)       # Devuelve los índices que ordenarían el array: [3, 1, 0, 4, 2]
np.argmax(arr)        # Índice del valor máximo: 2
np.argmin(arr)        # Índice del valor mínimo: 3
```

### Operaciones en Ejes (Arrays 2D)

Para operaciones a lo largo de filas o columnas en matrices 2D:

```python
arr2 = np.array([[1, 2, 3], [4, 5, 6]])
np.sum(arr2, axis=0)  # Suma a lo largo de las columnas: [5, 7, 9]
np.sum(arr2, axis=1)  # Suma a lo largo de las filas: [6, 15]
```

## Guardar y Cargar Arrays
### Guardar en archivos
```python
np.save('array.npy', arr)    # Guarda el array en un archivo .npy
np.savetxt('array.txt', arr) # Guarda el array en un archivo de texto
```
### Cargar desde archivos 
```python
arr = np.load('array.npy')   # Carga el array desde un archivo .npy
arr = np.loadtxt('array.txt')# Carga el array desde un archivo de texto
```

