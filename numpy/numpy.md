# Guía Completa de NumPy para Estadística y Probabilidad
# ======================================================================

# Índice
# -----
# 1. Creación de Arreglos
# 2. Matrices Especiales
# 3. Generación de Números Aleatorios
# 4. Operaciones Básicas
# 5. Indexación y Selección
# 6. Manipulación de Formas
# 7. Álgebra Lineal
# 8. Estadísticas Descriptivas
# 9. Operaciones Matriciales Avanzadas
# 10. Operaciones Lógicas y Filtrado

*1. Creación de Arreglos*

**Crear un arreglo de 10 ceros**
    
    `arreglo_ceros = np.zeros(10)`

**Crear un arreglo de 10 unos**
    `arreglo_unos = np.ones(10)`

***secuencias numericas***

**Crear un arreglo con valores de 1 a 50**
    `arreglo = np.arange(1, 51)`

**Crear un arreglo con valores de 1 a 10**
    `arreglo_1_10 = np.arange(1, 11)`

**Crear un arreglo con valores de 10 a 20**
    `arreglo_10_20 = np.arange(10, 21)`

**Crear un arreglo con 15 valores equidistantes entre 2 y 10**
    `arreglo_linspace = np.linspace(2, 10, 15)`

*2. Matrices Especiales*

***matriz identidad***

**Crear una matriz identidad de 4x4**
    `matriz_identidad_4x4 = np.eye(4)`

**Crear una matriz identidad de 6x6**
    `matriz_identidad_6x6 = np.eye(6)`


*3. Generación de Números Aleatorios*

***enteros aleatorios***

**Generar 10 números enteros aleatorios entre 1 y 100**
    `enteros_aleatorios = np.random.randint(1, 101, 10)`

***Números aleatorios con distribución uniforme***

**Generar 20 números aleatorios entre 0 y 1 con distribución uniforme**
    `uniformes = np.random.uniform(0, 1, 20)`

**Generar un arreglo de 100 valores aleatorios entre 0 y 1**
    `aleatorios_0_1 = np.random.rand(100)`

***Matrices aleatorias***

**Generar una matriz 5x5 con valores aleatorios entre 0 y 1**
    `matriz_aleatoria = np.random.rand(5, 5)`

**Generar una matriz 3x3 con enteros aleatorios del 1 al 50**
    `matriz_enteros = np.random.randint(1, 51, (3, 3))`


*4. Operaciones basicas*

***Suma, promedio y valores extremos***

**Crear un arreglo**
    `arr = np.array([10, 20, 30, 40, 50])`

**Calcular la suma de los elementos**
    `suma = np.sum(arr)`

**Calcular el promedio de los elementos**
    `promedio = np.mean(arr)`

**Encontrar el valor máximo**
    `maximo = np.max(arr)`

**Encontrar el valor mínimo**
    `minimo = np.min(arr)`

***Operaciones vectoriales***

**Convertir temperaturas de Celsius a Fahrenheit**
    `temperaturas_celsius = np.array([23, 25, 21, 19, 30, 28, 27])`
    `temperaturas_fahrenheit = (temperaturas_celsius * 9/5) + 32`

***Producto punto***

**Generar dos arreglos aleatorios de tamaño 5**
    `arr1 = np.random.rand(5)`
    `arr2 = np.random.rand(5)`

**Calcular el producto punto**
    `producto_punto = np.dot(arr1, arr2)`

*5. Indexación y Selección*

***Selección de elementos***
    `arreglo = np.arange(10, 21)`

**Seleccionar elementos del índice 3 al 6**
    `elementos = arreglo[3:7]`

**Seleccionar los primeros 5 elementos**
    `primeros_cinco = arreglo[:5]`

**Seleccionar los últimos 4 elementos**
    `ultimos_cuatro = arreglo[7:]`


***Selección de columnas y filas en matrices***
    `matriz = np.random.rand(5, 5)`

**Seleccionar la tercera columna**
    `tercera_columna = matriz[:, 2]`

**Seleccionar columnas específicas (2 y 4) de una matriz**
    `D = np.random.rand(5, 5)`
    `columnas_seleccionadas = D[:, [1, 3]]  # Índices 1 y 3 (columnas 2 y 4)`


***Selección de submatrices***

**Crear una matriz 5x5 aleatoria**
    `matriz = np.random.rand(5, 5)`

**Extraer una submatriz 3x3 (filas 1-3, columnas 1-3)**
    `submatriz = matriz[1:4, 1:4]`

**Extraer submatrices de una matriz 5x5**
    `C = np.random.rand(5, 5)`
    `submatriz1 = C[:3, :3]  # Esquina superior izquierda`
    `submatriz2 = C[1:4, 1:4]  # Submatriz del centro`

**Extraer una submatriz 2x2 de la esquina inferior derecha de una matriz 4x4**
    `H = np.random.rand(4, 4)`
    `submatriz_esquina = H[-2:, -2:]`

***Selección de diagonales***

**Crear una matriz 4x4**
    `matriz = np.arange(16).reshape(4, 4)`

**Seleccionar los elementos en la diagonal secundaria**
    `diagonal_secundaria = matriz[np.arange(4), np.arange(4)[::-1]]`

**Método alternativo para diagonal secundaria**
    `diagonal_secundaria_alt = [matriz[i, 3-i] for i in range(4)]`


*6. Manipulación de Formas*

***Reshape***

**Convertir un arreglo de 12 elementos en una matriz 3x4**
    `arr = np.arange(12)`
    `atriz_3x4 = arr.reshape(3, 4)`

**Reorganizar una matriz 6x6 en una matriz de 3x12**
    `E = np.random.rand(6, 6)`
    `E_reshaped = E.reshape(3, 12)`


*7. Álgebra Lineal*

***Inversión de matrices***

**Calcular la inversa de una matriz 5x5**
    `A = np.random.rand(5, 5)`
    `A_inv = np.linalg.inv(A)`

***Determinante***

**Calcular el determinante de una matriz identidad 4x4**
    `I = np.eye(4)`
    `determinante_I = np.linalg.det(I)`

***Rango***

**Calcular el rango de una matriz 4x4**
    `B = np.random.rand(4, 4)`
    `rango_B = np.linalg.matrix_rank(B)`

***Transposición***

**Calcular la transpuesta de una matriz 4x4**
    `F = np.random.rand(4, 4)`
    `F_transpuesta = F.T`


*8. Estadísticas Descriptivas*

***Medidas de tendencia central***

**Crear un arreglo**
    `mi_arreglo = np.arange(1, 101)`

**Calcular la media**
    `media = np.mean(mi_arreglo)`

**Calcular la mediana**
    `mediana = np.median(mi_arreglo)`

***Medidas de dispersión***

**Calcular la desviación estándar**
    `desviacion_estandar = np.std(mi_arreglo)`

***Operaciones estadísticas en matrices***

**Crear una matriz de 5x5 con valores aleatorios**
    `matriz = np.random.rand(5, 5)`

**Encontrar la suma de cada fila (suma por columnas)**
    `suma_filas = np.sum(matriz, axis=0)`

**Encontrar la suma de cada columna (suma por filas)**
    `suma_columnas = np.sum(matriz, axis=1)`


*9. Operaciones Matriciales Avanzadas*

***Intercambio de filas o columnas***

**Intercambiar la primera y la última fila de una matriz 5x5**
    `G = np.random.rand(5, 5)`
    `G[[0, -1]] = G[[-1, 0]]`

*10. Operaciones Lógicas y Filtrado*

***Filtrado con condiciones***

**Filtrar elementos mayores que 4**
    `arreglo = np.arange(1, 11)`
    `mayores = [numero for numero in arreglo if numero > 4]`

**Alternativa usando NumPy**
    `mayores_np = arreglo[arreglo > 4]`

***Contar elementos que cumplen una condición***

**Generar un arreglo de 100 números aleatorios entre 0 y 100**
    `arreglo = np.random.randint(0, 101, 100)`

**Contar cuántos números están en el rango [30, 70]**
    `conteo = np.sum((arreglo >= 30) & (arreglo <= 70))`
