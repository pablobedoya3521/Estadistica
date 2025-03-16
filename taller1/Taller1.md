import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

df = pd.read_csv('salarios_software.csv')
df.head()

salario = list(df['Salary'])
rango_salario = ["bajo" if x <= 300000 else "medio" if x <= 900000 else "alto" for x in salario]
df["rango_salario"] = rango_salario
df.head()

bajo = df[df['rango_salario']=='bajo']
medio = df[df['rango_salario']=='medio']
alto = df[df['rango_salario']=='alto']

m = 1.5
# bajo
media_bajo = bajo['Rating'].mean()
mediana_bajo = bajo['Rating'].median()
moda_bajo = max(bajo['Rating'].mode())
q1_bajo = bajo['Rating'].quantile(0.25)
q3_bajo = bajo['Rating'].quantile(0.75)
ric_bajo = q3_bajo - q1_bajo
lim_inf_bajo = q1_bajo - m * ric_bajo
lim_sup_bajo = q3_bajo + m * ric_bajo
min_bajo = bajo['Rating'].min()
max_bajo = bajo['Rating'].max()

# medio
media_medio = medio['Rating'].mean()
mediana_medio = medio['Rating'].median()
moda_medio = max(df['Rating'].mode())
q1_medio = medio['Rating'].quantile(0.25)
q3_medio = medio['Rating'].quantile(0.75)
ric_medio = q3_medio - q1_medio
lim_inf_med = q1_medio - m * ric_medio
lim_sup_med = q3_medio + m * ric_medio
min_medio = min(medio['Rating'])
max_medio = max(medio['Rating'])

# alto
media_alto = alto['Rating'].mean()
mediana_alto = alto['Rating'].median()
moda_alto = max(alto['Rating'].mode())
q1_alto = alto['Rating'].quantile(0.25)
q3_alto = alto['Rating'].quantile(0.75)
ric_alto = q3_alto - q1_alto
lim_inf_alto = q1_alto - m * ric_alto
lim_sup_alto = q3_alto + m * ric_alto
min_alto = min(alto['Rating'])
max_alto = max(alto['Rating'])

# print
plt.figure(figsize=(18, 9))
plt.subplot(2, 3, 1)
ax = sns.histplot(data = bajo, x = 'Rating', bins = 10, color = 'white')
ax.bar_label(ax.containers[0], fontsize = 10)
plt.title("Rating de las empresas de Software (Bajo)")
plt.xlabel("Rating")
plt.ylabel("Frecuencia")
plt.plot((media_bajo, media_bajo), (2000, media_bajo), color = 'red')
plt.plot((mediana_bajo, mediana_bajo), (2000, mediana_bajo), color = 'yellow')
plt.plot((moda_bajo, moda_bajo), (2000, moda_bajo), color = 'green')
plt.plot((q1_bajo, q1_bajo), (2000, q1_bajo), color = 'blue')
plt.plot((q3_bajo, q3_bajo), (2000, q3_bajo), color = 'blue')
plt.plot((lim_inf_bajo, lim_inf_bajo), (2000, lim_inf_bajo), color = 'purple')
plt.plot((lim_sup_bajo, lim_sup_bajo), (2000, lim_sup_bajo), color = 'purple')
plt.legend(["media", "mediana", "moda", "Q1", "Q3", "lim_inf", "lim_sup"])

plt.subplot(2, 3, 4)
sns.boxplot(
    data = bajo,
    x = 'Rating',
    flierprops = {"marker": "o"},
    boxprops = {"facecolor": (.3, .5, .7, .5)},
    medianprops = {"color": "r", "linewidth": 1},
    linecolor = "#137",
    linewidth = .75
    )
plt.subplot(2, 3, 2)
ax = sns.histplot(data = medio, x = 'Rating', bins = 10, color = 'white')
ax.bar_label(ax.containers[0], fontsize = 10)
plt.title("Rating de las empresas de Software (Medio)")
plt.xlabel("Rating")
plt.ylabel("Frecuencia")
plt.plot((media_medio, media_medio), (3000, media_medio), color = 'red')
plt.plot((mediana_medio, mediana_medio), (3000, mediana_medio), color = 'yellow')
plt.plot((moda_medio, moda_medio), (3000, moda_medio), color = 'green')
plt.plot((q1_medio, q1_medio), (3000, q1_medio), color = 'blue')
plt.plot((q3_medio, q3_medio), (3000, q3_medio), color = 'blue')
plt.plot((lim_inf_med, lim_inf_med), (3000, lim_inf_med), color = 'purple')
plt.plot((lim_sup_med, lim_sup_med), (3000, lim_sup_med), color = 'purple')
plt.legend(["media", "mediana", "moda", "Q1", "Q3", "lim_inf", "lim_sup"])
plt.subplot(2, 3, 5)
sns.boxplot(
    data = medio,
    x = 'Rating',
    flierprops = {"marker": "o"},
    boxprops = {"facecolor": (.3, .5, .7, .5)},
    medianprops = {"color": "r", "linewidth": 1},
    linecolor = "#137",
    linewidth = .75
    )

plt.subplot(2, 3, 3)
ax = sns.histplot(data = alto, x = 'Rating', bins = 10, color = 'white')
ax.bar_label(ax.containers[0], fontsize = 10)
plt.title("Rating de las empresas de Software (Alto)")
plt.xlabel("Rating")
plt.ylabel("Frecuencia")
plt.plot((media_alto, media_alto), (2000, media_alto), color = 'red')
plt.plot((mediana_alto, mediana_alto), (2000, mediana_alto), color = 'yellow')
plt.plot((moda_alto, moda_alto), (2000, moda_alto), color = 'green')
plt.plot((q1_alto, q1_alto), (2000, q1_alto), color = 'blue')
plt.plot((q3_alto, q3_alto), (2000, q3_alto), color = 'blue')
plt.plot((lim_inf_alto, lim_inf_alto), (2000, lim_inf_alto), color = 'purple')
plt.plot((lim_sup_alto, lim_sup_alto), (2000, lim_sup_alto), color = 'purple')
plt.legend(["media", "mediana", "moda", "Q1", "Q3", "lim_inf", "lim_sup"])

plt.subplot(2, 3, 6)
sns.boxplot(
    data = alto,
    x = 'Rating',
    flierprops = {"marker": "o"},
    boxprops = {"facecolor": (.3, .5, .7, .5)},
    medianprops = {"color": "r", "linewidth": 1},
    linecolor = "#137",
    linewidth = .75
    )

plt.show()

tabla = pd.DataFrame({
    "rango_salario": ["bajo", "medio", "alto"],
    "media": [media_bajo, media_medio, media_alto],
    "mediana": [mediana_bajo, mediana_medio, mediana_alto],
    "moda": [moda_bajo, moda_medio, moda_alto],
    "q1": [q1_bajo, q1_medio, q1_alto],
    "q3": [q3_bajo, q3_medio, q3_alto],
    "ric": [ric_bajo, ric_medio, ric_alto],
    "lim_inf": [lim_inf_bajo, lim_inf_med, lim_inf_alto],
    "lim_sup": [lim_sup_bajo, lim_sup_med, lim_sup_alto],
    "max": [max_bajo, max_medio, max_alto],
    "min": [min_bajo, min_medio, min_alto]
})

tabla.head()

Análisis
la media de los 3 rangos salariales no tiene un cambio significativo, dado que entre el mayor y el menor hay una diferencia de  0.04 .
el límite inferior del rango salarial alto es  2  puntos más alto que los demás, significando que los trabajadores que ganan un salario alto, califican de mejor manera a la empresa