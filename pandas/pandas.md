# Guía Completa de Pandas para Estadística y Análisis de Datos
# ============================================================

# Índice
# -----
# 1. Creación de DataFrames y Series
# 2. Importación y Exportación de Datos
# 3. Exploración de Datos
# 4. Selección y Filtrado de Datos
# 5. Manejo de Datos Faltantes
# 6. Estadísticas Descriptivas
# 7. Agrupación y Agregación
# 8. Operaciones Avanzadas
# 9. Visualización de Datos
# 10. Análisis de Series Temporales

*1. Creación de DataFrames y Series*

**Crear una Serie**

    serie = pd.Series([10, 20, 30, 40, 50])

**Crear una Serie con índices personalizados**

    serie = pd.Series([10, 20, 30, 40, 50], index=['a', 'b', 'c', 'd', 'e'])

**Crear un DataFrame a partir de un diccionario**

    datos = {
        'nombre': ['Ana', 'Juan', 'Pedro', 'María', 'Luis'],
        'edad': [25, 30, 35, 28, 42],
        'ciudad': ['Madrid', 'Barcelona', 'Sevilla', 'Valencia', 'Bilbao']
    }
    df = pd.DataFrame(datos)

**Crear un DataFrame con valores aleatorios**

    import numpy as np
    df_aleatorio = pd.DataFrame(np.random.rand(5, 3), columns=['A', 'B', 'C'])

*2. Importación y Exportación de Datos*

**Leer un archivo CSV**

    df = pd.read_csv('datos.csv')

**Leer un archivo Excel**

    df = pd.read_excel('datos.xlsx')

**Guardar un DataFrame como CSV**

    df.to_csv('datos_nuevos.csv', index=False)

**Guardar un DataFrame como Excel**

    df.to_excel('datos_nuevos.xlsx', index=False)

*3. Exploración de Datos*

**Ver las primeras filas de un DataFrame**

    df.head()

**Ver las últimas filas de un DataFrame**

    df.tail()

**Obtener información general del DataFrame**

    df.info()

**Obtener estadísticas descriptivas**

    df.describe()

**Verificar las dimensiones del DataFrame**

    df.shape

**Ver los nombres de las columnas**

    df.columns

**Ver los tipos de datos de cada columna**

    df.dtypes

*4. Selección y Filtrado de Datos*

**Seleccionar una columna**

    edades = df['edad']

**Seleccionar múltiples columnas**

    datos_personales = df[['nombre', 'edad']]

**Seleccionar filas por posición**

    # Seleccionar las primeras 3 filas
    primeras_filas = df.iloc[0:3]

**Seleccionar filas y columnas por posición**

    # Seleccionar filas 1-3 y columnas 0-1
    subconjunto = df.iloc[1:4, 0:2]

**Seleccionar filas por índice**

    # Si tienes índices personalizados
    fila = df.loc['indice_personalizado']

**Filtrar datos con condiciones**

    # Personas mayores de 30 años
    mayores_30 = df[df['edad'] > 30]

**Filtrar con múltiples condiciones**

    # Personas mayores de 30 años de Madrid
    filtro = (df['edad'] > 30) & (df['ciudad'] == 'Madrid')
    resultado = df[filtro]

**Filtrar basado en una lista de valores**

    # Personas que viven en Madrid o Barcelona
    ciudades = ['Madrid', 'Barcelona']
    resultado = df[df['ciudad'].isin(ciudades)]

*5. Manejo de Datos Faltantes*

**Verificar valores faltantes**

    # Muestra True para valores faltantes
    df.isna()

**Sumar valores faltantes por columna**

    # Cuenta cuántos valores faltan en cada columna
    df.isna().sum()

**Eliminar filas con valores faltantes**

    df_limpio = df.dropna()

**Rellenar valores faltantes con un valor específico**

    df_relleno = df.fillna(0)

**Rellenar valores faltantes con la media**

    df['edad'] = df['edad'].fillna(df['edad'].mean())

**Rellenar valores faltantes con el valor anterior o siguiente**

    # Método 'ffill' (forward fill) usa el valor anterior
    df_ffill = df.fillna(method='ffill')

    # Método 'bfill' (backward fill) usa el valor siguiente
    df_bfill = df.fillna(method='bfill')

*6. Estadísticas Descriptivas*

**Calcular la media de una columna**

    edad_media = df['edad'].mean()

**Calcular la mediana de una columna**

    edad_mediana = df['edad'].median()

**Calcular el valor máximo y mínimo**

    edad_maxima = df['edad'].max()
    edad_minima = df['edad'].min()

**Calcular la desviación estándar**

    desviacion = df['edad'].std()

**Calcular el rango intercuartílico**

    q75, q25 = df['edad'].quantile(0.75), df['edad'].quantile(0.25)
    iqr = q75 - q25

**Obtener un resumen de varias estadísticas**

    resumen = df['edad'].describe()

**Calcular la correlación entre columnas numéricas**

    correlacion = df.corr()

**Calcular la covarianza entre columnas numéricas**

    covarianza = df.cov()

*7. Agrupación y Agregación*

**Agrupar por una columna y calcular la media**

    # Media de edad por ciudad
    media_por_ciudad = df.groupby('ciudad')['edad'].mean()

**Agrupar por una columna y aplicar múltiples funciones**

    # Estadísticas de edad por ciudad
    estadisticas = df.groupby('ciudad')['edad'].agg(['mean', 'min', 'max', 'count'])

**Agrupar por múltiples columnas**

    df_complejo = pd.DataFrame({
        'categoria': ['A', 'B', 'A', 'B', 'A', 'B'],
        'subcategoria': ['X', 'X', 'Y', 'Y', 'Z', 'Z'],
        'valor': [10, 20, 30, 40, 50, 60]
    })

    resultado = df_complejo.groupby(['categoria', 'subcategoria']).mean()

**Aplicar función personalizada a grupos**

    def rango(x):
    return x.max() - x.min()

    rango_por_ciudad = df.groupby('ciudad')['edad'].apply(rango)

**Filtrar grupos basados en una condición**

    # Ciudades donde la edad media es mayor a 30
    ciudades_filtradas = df.groupby('ciudad').filter(lambda x: x['edad'].mean() > 30)

*8. Operaciones Avanzadas*

**Aplicar una función a cada elemento**
**Pivot tables (tablas dinámicas)**
**Unir DataFrames (merge)**
**Concatenar DataFrames**
**Reindexar un DataFrame**
**Calcular diferencias entre filas consecutivas**

*9. Visualización de Datos*

**Importar biblioteca de visualización**

    import matplotlib.pyplot as plt
    %matplotlib inline  # En Jupyter Notebook

**Crear un gráfico de líneas**

    df['edad'].plot(kind='line')
    plt.title('Edades')
    plt.xlabel('Índice')
    plt.ylabel('Edad')
    plt.show()

**Crear un gráfico de barras**

    df['edad'].plot(kind='bar')
    plt.title('Edades por Persona')
    plt.show()

**Crear un histograma**

    df['edad'].plot(kind='hist', bins=10)
    plt.title('Distribución de Edades')
    plt.show()

**Crear un gráfico de dispersión**

    # Suponiendo que tienes columnas numéricas
    df.plot(kind='scatter', x='columna_numerica1', y='columna_numerica2')
    plt.title('Gráfico de Dispersión')
    plt.show()

**Crear un boxplot (diagrama de caja)**

    df.boxplot(column='edad', by='ciudad')
    plt.title('Distribución de Edades por Ciudad')
    plt.show()

**Matriz de correlación con mapa de calor**

    import seaborn as sns

    # Crear una matriz de correlación
    corr = df.corr()

    # Representar como mapa de calor
    sns.heatmap(corr, annot=True, cmap='coolwarm')
    plt.title('Matriz de Correlación')

    plt.show()

*10. Análisis de Series Temporales*

**Crear un índice de fechas**

    fechas = pd.date_range(start='2023-01-01', periods=10, freq='D')
    df_tiempo = pd.DataFrame({'valor': np.random.randn(10)}, index=fechas)

**Resamplear datos temporales**

    # Resamplear a nivel mensual
    df_mensual = df_tiempo.resample('M').mean()

**Calcular media móvil**

    # Media móvil de 3 periodos
    df_tiempo['media_movil'] = df_tiempo['valor'].rolling(window=3).mean()

**Cambiar la frecuencia de los datos**

    # Convertir datos diarios a semanales
    df_semanal = df_tiempo.asfreq('W')

**Desplazar datos en el tiempo**

    # Desplazar datos un periodo hacia adelante
    df_tiempo['valor_anterior'] = df_tiempo['valor'].shift(1)

**Calcular el cambio porcentual**

    df_tiempo['cambio_porcentual'] = df_tiempo['valor'].pct_change() * 100