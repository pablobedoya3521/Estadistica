**Importación de Seaborn**

    import seaborn as sns
    import matplotlib.pyplot as plt
    import numpy as np
    import pandas as pd

**Cargar datasets de ejemplo**

    # Cargar datasets incorporados
    tips = sns.load_dataset("tips")
    iris = sns.load_dataset("iris")
    titanic = sns.load_dataset("titanic")
    planets = sns.load_dataset("planets")

*2. Gráficos de Distribución*

**Histograma mejorado (distplot/histplot)**

    # Crear histograma con curva KDE
    sns.histplot(data=tips, x="total_bill", kde=True)
    plt.title('Distribución de Cuentas')
    plt.xlabel('Total de la Cuenta')
    plt.ylabel('Frecuencia')
    plt.show()

**Gráfico de densidad (kdeplot)**

    # Estimación de densidad kernel (KDE)
    sns.kdeplot(data=tips, x="total_bill", shade=True)
    plt.title('Densidad de Distribución de Cuentas')
    plt.show()

**Histograma 2D (histplot)**

    # Histograma bidimensional
    sns.histplot(data=tips, x="total_bill", y="tip", bins=10, cbar=True)
    plt.title('Relación entre Cuenta Total y Propina')
    plt.show()

**Gráfico de densidad 2D (kdeplot)**

    # Densidad bidimensional
    sns.kdeplot(data=tips, x="total_bill", y="tip", fill=True, cmap="viridis")
    plt.title('Densidad Conjunta de Cuenta y Propina')
    plt.show()

**Distribución conjunta (jointplot)**

    # Distribución conjunta con histogramas marginales
    sns.jointplot(data=tips, x="total_bill", y="tip", kind="scatter")
    plt.suptitle('Relación entre Cuenta y Propina', y=1.05)
    plt.show()

**Variantes de jointplot**

    # Scatter con KDE
    sns.jointplot(data=tips, x="total_bill", y="tip", kind="kde")

    # Histograma hexagonal
    sns.jointplot(data=tips, x="total_bill", y="tip", kind="hex")

    # Con regresión
    sns.jointplot(data=tips, x="total_bill", y="tip", kind="reg")

*3. Gráficos Categóricos*

**Gráfico de cajas (boxplot)**

    # Diagrama de caja básico
    sns.boxplot(data=tips, x="day", y="total_bill")
    plt.title('Distribución de Cuentas por Día')
    plt.show()

**Gráfico de cajas con múltiples variables categóricas**

    # Diagrama de caja con agrupación por una segunda variable categórica
    sns.boxplot(data=tips, x="day", y="total_bill", hue="sex")
    plt.title('Distribución de Cuentas por Día y Género')
    plt.show()

**Diagrama de barras (barplot)**

    # Diagrama de barras con error bars (muestra la media y CI)
    sns.barplot(data=tips, x="day", y="total_bill")
    plt.title('Media de Cuentas por Día')
    plt.show()

**Diagrama de puntos (stripplot)**

    # Gráfico de puntos individuales
    sns.stripplot(data=tips, x="day", y="total_bill", jitter=True)
    plt.title('Cuentas Individuales por Día')
    plt.show()

**Combinar swarm y box plots**

    # Combinar diagrama de caja con puntos individuales
    plt.figure(figsize=(10, 6))
    sns.boxplot(data=tips, x="day", y="total_bill", color="lightgray")
    sns.swarmplot(data=tips, x="day", y="total_bill", color="black", alpha=0.5)
    plt.title('Combinación de Boxplot y Swarmplot')
    plt.show()

**Gráfico de cuenta (countplot)**

    # Contar ocurrencias de cada categoría
    sns.countplot(data=tips, x="day")
    plt.title('Número de Visitas por Día')
    plt.show()

*4. Gráficos de Relación*

**Gráfico de dispersión (scatterplot)**

    # Gráfico de dispersión básico
    sns.scatterplot(data=tips, x="total_bill", y="tip")
    plt.title('Relación entre Cuenta y Propina')
    plt.show()

**Gráfico de dispersión con variables categóricas**

    # Dispersión con color y tamaño según variables
    sns.scatterplot(data=tips, x="total_bill", y="tip", hue="time", size="size")
    plt.title('Relación entre Cuenta y Propina por Hora y Tamaño de Mesa')
    plt.show()

**Matriz de gráficos de dispersión (pairplot)**

    # Matriz de gráficos para visualizar múltiples relaciones
    sns.pairplot(data=iris)
    plt.suptitle('Relaciones entre Variables de Iris', y=1.02)
    plt.show()

*5. Visualización de Matrices*

**Mapa de calor básico (heatmap)**

    # Generar una matriz de correlación
    corr = iris.drop("species", axis=1).corr()

    # Crear un mapa de calor
    sns.heatmap(corr)
    plt.title('Matriz de Correlación')
    plt.show()

**Mapa de calor con anotaciones**

    # Mapa de calor con valores numéricos
    sns.heatmap(corr, annot=True, fmt=".2f", cmap="coolwarm")
    plt.title('Matriz de Correlación con Valores')
    plt.show()

**Clustermaps (agrupación jerárquica)**

    # Mapa de calor con clustering jerárquico
    sns.clustermap(corr, cmap="mako", standard_scale=1)
    plt.title('Agrupación Jerárquica de Correlaciones')
    plt.show()

*6. Combinación con Pandas*

**Visualizar datos de DataFrames directamente**

    # Crear un DataFrame de ejemplo
    np.random.seed(42)
    df = pd.DataFrame({
        'Grupo': ['A', 'B', 'C', 'D', 'E'] * 10,
        'Valor1': np.random.normal(0, 1, 50),
        'Valor2': np.random.normal(5, 2, 50),
        'Categoría': np.random.choice(['Tipo1', 'Tipo2', 'Tipo3'], 50)
    })

    # Visualizar con Seaborn
    sns.catplot(data=df, x="Grupo", y="Valor1", hue="Categoría", kind="box")
    plt.title('Valores por Grupo y Categoría')
    plt.show()
