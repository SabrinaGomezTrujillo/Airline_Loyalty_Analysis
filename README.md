# ✈️ Comportamiento de Clientes en un Programa de Lealtad de Aerolínea

**Autora:** Sabrina Giselle Gómez Trujillo

Análisis exploratorio y estadístico del programa de lealtad de una aerolínea canadiense. A partir de dos datasets complementarios se estudia el perfil sociodemográfico de los socios, su comportamiento de vuelo y el uso del programa de puntos, con el objetivo de identificar oportunidades de negocio y sentar las bases para modelos predictivos de CLV y churn.

---

## 📁 Estructura del repositorio

```
.
├── data/
│   ├── Customer Flight Activity.csv      # Actividad mensual de vuelo por socio
│   └── Customer Loyalty History.csv      # Perfil e historial del cliente
├── Airline_Loyalty_Analysis.ipynb        # Notebook principal
└── README.md
```

---

## 📊 Datasets

| Dataset | Registros | Variables | Contenido |
|---|---|---|---|
| `Customer Flight Activity.csv` | 405 624 | 10 | Vuelos reservados, distancia, puntos acumulados y canjeados |
| `Customer Loyalty History.csv` | 16 737 | 16 | Perfil del cliente, provincia, educación, ingresos, tipo de tarjeta |

Los datasets se unen mediante un **LEFT JOIN** sobre `Loyalty Number`, resultando en un dataset combinado de **401 688 registros** tras la limpieza.

---

## 🛠️ Herramientas y librerías

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)
![pandas](https://img.shields.io/badge/pandas-✓-150458?logo=pandas)
![NumPy](https://img.shields.io/badge/NumPy-✓-013243?logo=numpy)
![Matplotlib](https://img.shields.io/badge/Matplotlib-✓-11557c)
![Seaborn](https://img.shields.io/badge/Seaborn-✓-4c72b0)
![SciPy](https://img.shields.io/badge/SciPy-✓-8caae6?logo=scipy)
![statsmodels](https://img.shields.io/badge/statsmodels-✓-3c6478)

---

## 🗂️ Estructura del notebook

| Sección | Contenido |
|---|---|
| **0 · Setup** | Imports, configuración global y carga de datos |
| **1 · Exploración y limpieza** | EDA inicial, duplicados, nulos, imputación y unión de datasets |
| **2 · Análisis estadístico** | Descriptiva, outliers (IQR), correlaciones y variables categóricas |
| **3 · Visualización** | Seis gráficos clave con interpretación de negocio |
| **4 · Prueba de hipótesis** | ANOVA y Kruskal-Wallis: vuelos reservados por nivel educativo |
| **5 · Conclusiones** | Hallazgos principales y próximos pasos estratégicos |

---

## 🔍 Principales hallazgos

| # | Hallazgo | Implicación |
|---|---|---|
| 1 | **75% de socios nunca canjea puntos** | El programa de beneficios está infrautilizado — alta oportunidad de activación |
| 2 | **Tarjeta Aurora genera 43% más CLV** que la Star | Promover el upgrade de tarjeta es la palanca de mayor impacto en rentabilidad |
| 3 | **Estacionalidad clara**: picos en verano y diciembre | Planificar campañas de fidelización y capacidad en temporada alta |
| 4 | **12.35% de socios canceló**, con CLV ~15% inferior al promedio | Modelo de churn factible y necesario para retención temprana |
| 5 | **Ontario + BC + Quebec = 78%** de los socios | Segmentar campañas regionales; personalización especial en Quebec |
| 6 | **Cambio de política de puntos en 2018**: mayor pendiente pts/km | Incluir `Year` como variable de control en modelos de puntos |
| 7 | **Nivel educativo no predice vuelos** (ANOVA p = 0.49, Kruskal-Wallis p = 0.45) | Las campañas de reservas pueden diseñarse sin segmentar por educación |
| 8 | **Variables redundantes** identificadas: `Total Flights`, `Dollar Cost Points Redeemed` | Reducir dimensionalidad antes de modelar |

---

## 📈 Visualizaciones incluidas

1. **Estacionalidad de reservas** — comparación mensual 2017 vs 2018
2. **Distancia vs puntos acumulados** — verificación de consistencia del programa por año
3. **Distribución geográfica** — clientes únicos por provincia
4. **Salario por nivel educativo** — validación de coherencia y brecha salarial
5. **Distribución por tipo de tarjeta** — penetración de cada nivel y CLV mediano asociado
6. **Perfil demográfico** — estado civil y género de los socios

---

## 🔬 Prueba de hipótesis

**Pregunta:** ¿El número de vuelos reservados difiere según el nivel educativo del cliente?

| Prueba | Estadístico | p-valor | Conclusión |
|---|---|---|---|
| ANOVA | F = 0.8564 | 0.4893 | No significativo |
| Kruskal-Wallis | H = 3.6735 | 0.4520 | No significativo |

No existe evidencia estadística de diferencias en actividad de vuelo por nivel educativo. Las medias son prácticamente idénticas entre grupos (98.7–101.0 vuelos por cliente). Las variables con mayor poder discriminante son `Loyalty Card`, `Province` y `CLV`.

---

## 🚀 Próximos pasos

1. **Modelo de predicción de CLV** — usando `Loyalty Card`, `Province`, `Education`, `Marital Status`, `Salary` y actividad de vuelo como features.
2. **Modelo de churn** — clasificador binario con `Cancelled` como variable target.
3. **Segmentación de clientes** — clustering (K-Means o jerárquico) sobre actividad y perfil sociodemográfico.
4. **Análisis de upgrade de tarjeta** — identificar el perfil de clientes que ascendieron de nivel para replicar el patrón mediante campañas dirigidas.
5. **Experimento A/B** — campaña de activación de puntos para el 75% de socios que nunca canjea.

---

## ▶️ Cómo ejecutar el notebook

1. Clonar el repositorio y situarse en la carpeta raíz.
2. Asegurarse de tener los archivos de datos en la carpeta `data/`.
3. Instalar las dependencias:
   ```bash
   pip install pandas numpy matplotlib seaborn scipy statsmodels
   ```
4. Abrir el notebook:
   ```bash
   jupyter notebook Airline_Loyalty_Analysis.ipynb
   ```
