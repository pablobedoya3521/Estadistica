# Guía Completa de Matplotlib para Visualización Estadística
======================================================================
# Índice
# -----
# 1. Gráficos Básicos
# 2. Personalización de Gráficos
# 3. Subplots (Múltiples Gráficos)
# 4. Tipos de Gráficos Especializados
# 5. Visualización de Distribuciones
# 6. Personalización Avanzada
# 7. Combinación con Pandas

*1. Gráficos Básicos*

**Importación de Matplotlib**

    import matplotlib.pyplot as plt
    import numpy as np

**Gráfico de líneas simple**

    # Datos
    x = np.arange(0, 10, 0.1)
    y = np.sin(x)

    # Crear gráfico
    plt.plot(x, y)
    plt.title('Función Seno')
    plt.xlabel('x')
    plt.ylabel('sen(x)')
    plt.show()

**Gráfico de dispersión (scatter)**

    # Datos aleatorios
    x = np.random.rand(50)
    y = np.random.rand(50)

    # Crear gráfico de dispersión
    plt.scatter(x, y)
    plt.title('Gráfico de Dispersión')
    plt.xlabel('Variable X')
    plt.ylabel('Variable Y')
    plt.show()

**Gráfico de barras**

    # Datos
    categorias = ['A', 'B', 'C', 'D', 'E']
    valores = [23, 45, 56, 78, 32]

    # Crear gráfico de barras
    plt.bar(categorias, valores)
    plt.title('Gráfico de Barras')
    plt.xlabel('Categoría')
    plt.ylabel('Valor')
    plt.show()

**Histograma**

    # Datos aleatorios con distribución normal
    datos = np.random.randn(1000)

    # Crear histograma
    plt.hist(datos, bins=30)
    plt.title('Histograma')
    plt.xlabel('Valor')
    plt.ylabel('Frecuencia')
    plt.show()

*2. Personalización de Gráficos*

**Cambiar colores y estilos de línea**

    x = np.linspace(0, 10, 100)

    # Diferentes estilos de línea
    plt.plot(x, np.sin(x), 'r-', label='sen(x)')  # rojo, línea continua
    plt.plot(x, np.cos(x), 'b--', label='cos(x)')  # azul, línea discontinua
    plt.plot(x, np.tan(x), 'g-.', label='tan(x)')  # verde, línea punto-raya

    plt.legend()
    plt.title('Funciones Trigonométricas')
    plt.ylim(-2, 2)  # Limitar eje y
    plt.grid(True)   # Agregar cuadrícula
    plt.show()

**Personalizar marcadores**

    x = np.linspace(0, 5, 10)
    y = x ** 2

    # Marcadores diferentes
    plt.plot(x, y, 'ro-', markersize=10, linewidth=2)  # círculos rojos
    plt.title('Función Cuadrática')
    plt.show()

**Personalizar ejes**

    plt.figure(figsize=(10, 6))  # Tamaño de la figura en pulgadas
    plt.plot(x, y)
    plt.title('Gráfico con Ejes Personalizados', fontsize=16)
    plt.xlabel('Eje X', fontsize=14)
    plt.ylabel('Eje Y', fontsize=14)
    plt.xticks(fontsize=12)
    plt.yticks(fontsize=12)
    plt.grid(True, linestyle='--', alpha=0.7)
    plt.show()

**Añadir texto y anotaciones**

    x = np.linspace(0, 5, 100)
    y = np.sin(2 * np.pi * x)

    plt.plot(x, y)
    plt.title('Función Seno')

    # Añadir texto en un punto específico
    plt.text(2.5, 0.8, 'Valor máximo', fontsize=12)

    # Añadir una flecha señalando un punto
    plt.annotate('Punto de inflexión', 
                xy=(1.25, 0),        # Punta de la flecha
                xytext=(2, -0.5),    # Posición del texto
                arrowprops=dict(facecolor='black', shrink=0.05))
    plt.show()

*3. Subplots (Múltiples Gráficos)*

**Crear múltiples gráficos en una cuadrícula**

    # Crear una figura con 2 filas y 2 columnas
    plt.figure(figsize=(10, 8))

    # Subplot 1: Gráfico de líneas
    plt.subplot(2, 2, 1)  # (filas, columnas, índice)
    plt.plot(np.random.rand(10))
    plt.title('Gráfico de Líneas')

    # Subplot 2: Gráfico de barras
    plt.subplot(2, 2, 2)
    plt.bar(['A', 'B', 'C', 'D'], [10, 20, 15, 30])
    plt.title('Gráfico de Barras')

    # Subplot 3: Gráfico de dispersión
    plt.subplot(2, 2, 3)
    plt.scatter(np.random.rand(10), np.random.rand(10))
    plt.title('Gráfico de Dispersión')

    # Subplot 4: Histograma
    plt.subplot(2, 2, 4)
    plt.hist(np.random.randn(100), bins=20)
    plt.title('Histograma')

    plt.tight_layout()  # Ajustar automáticamente los subplots
    plt.show()

**Subplots con diferentes tamaños**

    # Crear una figura con subplots de diferentes tamaños
    fig = plt.figure(figsize=(10, 8))

    # Definir la disposición: (alto, ancho, índice)
    ax1 = plt.subplot2grid((3, 3), (0, 0), colspan=2)  # Fila 0, Col 0, abarca 2 columnas
    ax2 = plt.subplot2grid((3, 3), (0, 2), rowspan=2)  # Fila 0, Col 2, abarca 2 filas
    ax3 = plt.subplot2grid((3, 3), (1, 0), colspan=2)  # Fila 1, Col 0, abarca 2 columnas
    ax4 = plt.subplot2grid((3, 3), (2, 0), colspan=3)  # Fila 2, Col 0, abarca 3 columnas

    # Añadir gráficos a cada subplot
    ax1.plot(np.random.rand(10))
    ax2.scatter(np.random.rand(10), np.random.rand(10))
    ax3.bar(['A', 'B', 'C', 'D'], [10, 20, 15, 30])
    ax4.hist(np.random.randn(100), bins=20)

    plt.tight_layout()
    plt.show()

**Métodos alternativos para crear subplots**

    # Método con objetos de ejes
    fig, axs = plt.subplots(2, 2, figsize=(10, 8))

    # Acceso por índice
    axs[0, 0].plot(np.random.rand(10))
    axs[0, 0].set_title('Gráfico de Líneas')

    axs[0, 1].bar(['A', 'B', 'C', 'D'], [10, 20, 15, 30])
    axs[0, 1].set_title('Gráfico de Barras')

    axs[1, 0].scatter(np.random.rand(10), np.random.rand(10))
    axs[1, 0].set_title('Gráfico de Dispersión')

    axs[1, 1].hist(np.random.randn(100), bins=20)
    axs[1, 1].set_title('Histograma')

    plt.tight_layout()
    plt.show()

*4. Tipos de Gráficos Especializados*

**Gráfico de pastel (pie chart)**

    # Datos
    categorias = ['A', 'B', 'C', 'D', 'E']
    valores = [15, 30, 25, 10, 20]

    # Resaltar una sección específica
    explode = [0, 0.1, 0, 0, 0]  # Destacar la segunda rebanada

    plt.figure(figsize=(8, 8))
    plt.pie(valores, labels=categorias, explode=explode, autopct='%1.1f%%', 
            shadow=True, startangle=90)
    plt.axis('equal')  # Para que el círculo sea proporcional
    plt.title('Gráfico de Pastel')
    plt.show()

**Gráfico de caja (boxplot)**

    # Generar datos aleatorios
    data = [np.random.normal(0, std, 100) for std in range(1, 4)]

    plt.figure(figsize=(8, 6))
    plt.boxplot(data, notch=True, patch_artist=True)
    plt.xticks([1, 2, 3], ['Grupo 1', 'Grupo 2', 'Grupo 3'])
    plt.ylabel('Valor')
    plt.title('Gráfico de Caja')
    plt.show()

**Gráfico de violín**

    import matplotlib.pyplot as plt

    # Datos aleatorios
    data = [np.random.normal(0, std, 100) for std in range(1, 4)]

    plt.figure(figsize=(8, 6))
    plt.violinplot(data, showmeans=True, showmedians=True)
    plt.xticks([1, 2, 3], ['Grupo 1', 'Grupo 2', 'Grupo 3'])
    plt.ylabel('Valor')
    plt.title('Gráfico de Violín')
    plt.show()

**Gráfico de área**

    # Datos
    x = np.arange(0, 10, 0.1)
    y1 = np.sin(x)
    y2 = np.cos(x)

    plt.figure(figsize=(10, 6))
    plt.fill_between(x, 0, y1, alpha=0.5, label='sen(x)')
    plt.fill_between(x, 0, y2, alpha=0.5, label='cos(x)')
    plt.title('Gráfico de Área')
    plt.legend()
    plt.grid(True)
    plt.show()

*5. Visualización de Distribuciones*

**Histograma con curva normal superpuesta**

    # Generar datos aleatorios con distribución normal
    datos = np.random.randn(1000)

    plt.figure(figsize=(10, 6))

    # Histograma
    n, bins, patches = plt.hist(datos, bins=30, density=True, alpha=0.7)

    # Superposición de la curva de densidad normal
    mu, sigma = np.mean(datos), np.std(datos)
    y = ((1 / (np.sqrt(2 * np.pi) * sigma)) *
        np.exp(-0.5 * (1 / sigma * (bins - mu))**2))
    plt.plot(bins, y, 'r--', linewidth=2)

    plt.title('Histograma con Curva Normal Superpuesta')
    plt.xlabel('Valor')
    plt.ylabel('Densidad')
    plt.grid(True, alpha=0.3)
    plt.show()

**Gráfico de probabilidad normal (Q-Q plot)**

    from scipy import stats

    # Datos aleatorios
    datos = np.random.randn(100)

    plt.figure(figsize=(8, 8))

    # Crear gráfico Q-Q
    stats.probplot(datos, plot=plt)
    plt.title('Gráfico Q-Q')
    plt.grid(True)
    plt.show()

**Gráfico de contorno**

    # Crear datos para el gráfico de contorno
    x = np.linspace(-3, 3, 100)
    y = np.linspace(-3, 3, 100)
    X, Y = np.meshgrid(x, y)
    Z = np.exp(-(X**2 + Y**2)/2)  # Función gaussiana 2D

    plt.figure(figsize=(8, 6))
    contour = plt.contour(X, Y, Z, cmap='viridis')
    plt.colorbar(contour, label='Valor')
    plt.title('Gráfico de Contorno')
    plt.xlabel('X')
    plt.ylabel('Y')
    plt.grid(True)
    plt.show()

**Mapa de calor (heatmap)**

    # Crear datos para el mapa de calor
    matriz = np.random.rand(10, 12)

    plt.figure(figsize=(10, 8))
    plt.imshow(matriz, cmap='hot', interpolation='nearest')
    plt.colorbar(label='Valor')
    plt.title('Mapa de Calor')
    plt.xlabel('Columna')
    plt.ylabel('Fila')
    plt.show()

*6. Personalización Avanzada*

**Cambiar el estilo de gráficos**

    # Ver estilos disponibles
    print(plt.style.available)

    # Usar un estilo predefinido
    plt.style.use('ggplot')

    x = np.linspace(0, 10, 100)
    plt.figure(figsize=(8, 6))
    plt.plot(x, np.sin(x))
    plt.title('Gráfico con Estilo ggplot')
    plt.show()

    # Restaurar estilo predeterminado
    plt.style.use('default')

**Figuras con múltiples ejes y escalas**

    # Crear figura con dos ejes Y
    fig, ax1 = plt.subplots(figsize=(10, 6))

    # Datos
    x = np.linspace(0, 10, 100)
    y1 = np.sin(x)
    y2 = np.exp(x) / 100

    # Primer eje Y (izquierda)
    ax1.plot(x, y1, 'b-', label='Seno')
    ax1.set_xlabel('X')
    ax1.set_ylabel('Amplitud', color='b')
    ax1.tick_params(axis='y', labelcolor='b')

    # Segundo eje Y (derecha)
    ax2 = ax1.twinx()
    ax2.plot(x, y2, 'r-', label='Exponencial')
    ax2.set_ylabel('Valor exponencial', color='r')
    ax2.tick_params(axis='y', labelcolor='r')

    # Leyendas
    ax1.legend(loc='upper left')
    ax2.legend(loc='upper right')

    plt.title('Gráfico con Múltiples Ejes Y')
    plt.grid(True, alpha=0.3)
    plt.show()

*7. Combinación con Pandas*

**Visualización directa desde DataFrames**

    import pandas as pd
    import numpy as np
    import matplotlib.pyplot as plt

    # Crear un DataFrame de ejemplo
    np.random.seed(42)
    df = pd.DataFrame({
        'Grupo': ['A', 'B', 'C', 'D', 'E'] * 10,
        'Valor1': np.random.normal(0, 1, 50),
        'Valor2': np.random.normal(5, 2, 50),
        'Valor3': np.random.normal(-3, 1.5, 50)
    })

    # Histograma con pandas
    plt.figure(figsize=(10, 6))
    df['Valor1'].plot.hist(bins=20, alpha=0.7)
    plt.title('Histograma desde DataFrame')
    plt.xlabel('Valor')
    plt.ylabel('Frecuencia')
    plt.grid(True, alpha=0.3)
    plt.show()

**Gráfico de barras con pandas**

    # Agrupar datos por 'Grupo' y calcular la media
    datos_agrupados = df.groupby('Grupo').mean().reset_index()

    # Crear gráfico de barras
    plt.figure(figsize=(10, 6))
    datos_agrupados.plot.bar(x='Grupo', y=['Valor1', 'Valor2', 'Valor3'], rot=0)
    plt.title('Valores Medios por Grupo')
    plt.xlabel('Grupo')
    plt.ylabel('Valor Medio')
    plt.grid(True, alpha=0.3)
    plt.legend(title='Variables')
    plt.show()

**Gráfico de dispersión con pandas**

    # Crear gráfico de dispersión
    plt.figure(figsize=(10, 6))
    df.plot.scatter(x='Valor1', y='Valor2', c='Valor3', cmap='viridis', 
                    s=50, alpha=0.7, edgecolors='white')
    plt.title('Gráfico de Dispersión desde DataFrame')
    plt.xlabel('Valor1')
    plt.ylabel('Valor2')
    plt.colorbar(label='Valor3')
    plt.grid(True, alpha=0.3)
    plt.show()

**Gráfico de caja con pandas**

    # Crear gráfico de caja
    plt.figure(figsize=(12, 6))
    df.boxplot(column=['Valor1', 'Valor2', 'Valor3'], by='Grupo', figsize=(12, 6))
    plt.title('Distribución de Valores por Grupo')
    plt.suptitle('')  # Suprimir el título automático
    plt.tight_layout()
    plt.show()