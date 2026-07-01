# Análisis de sesgos en premios NBA mediante Machine Learning y visualización de datos

TFM — Máster Universitario en Análisis y Visualización de Datos Masivos/ Visual Analytics and Big Data | UNIR | 2026

Autores: Carlos Rozas Rodríguez · Jacobo Rodríguez González

## Descripción
Análisis del impacto de la fatiga del votante en la votación al MVP de la NBA 
(1980–2025) mediante modelos predictivos comparativos. Se contrastan dos escenarios: 
Uno basado exclusivamente en variables de rendimiento y otro que incorpora variables 
de fatiga del votante (fatigue_decay, fatigue_streak, is_defending_mvp).

## Estructura del repositorio

```
├── data/
│   ├── datos_1980-2025.csv		  # Extracción inicial de datos
│   ├── datos_1980-2025_procesados.csv   # Datos procesados tras la primera extracción
│   └── datos_1980-2025_procesados_fatigue.csv   # Datos procesados tras la generación de las variables de fatiga
├── notebooks/
│   ├── 01_ExtraccionDatos.ipynb		# Extracción de datos
│   ├── 02_LimpiezaDatos.ipynb  # Limpieza inicial de datos
│   ├── 03_IngenieraVariables.ipynb  # Generación de variables de fatiga
│   ├── 04_Modelado_GridSearchCV.ipynb  # Busqueda de mejores modelos
│   └── 05_SHAP.ipynb  # Análisis SHAP
├── outputs/
│   └── gridsearch_objects.pkl    # Resultados de la ejecución de GridSearcCV
└── README.md
```

El orden de ejecución de los notebooks será el siguiente:
*   01_ExtraccionDatos: Es el base, no es necesario introducir nada. Produce el csv datos_1980-2025.
*   02_LimpiezaDatos: Necesario el csv generado en el anterior notebook (datos_1980-2025). Produce el csv datos_1980-2025_procesados.
*   03_IngenieriaVariables: Necesario importar los datos procesados en el segundo notebook (datos_1980-2025_procesados). Produce el csv final, que se emplea como entrada en los siguientes notebooks, datos_1980-2025_procesados_fatigue.
*   04_Modelado_GridSearchCV: Importará el último csv generado (datos_1980-2025_procesados_fatigue). La salida generada será gridsearch_objects.pkl, que es el fichero que contiene los resultados de GridSearchCV.
*   05_Shap: Los datos de entrada serán los generados en el 3 notebook (datos_1980-2025_procesados_fatigue). No generará ningún fichero de salida.

Cada notebook, de manera interna, se ejecutará en orden, empezando por la primera celda que contiene los imports necesarios hasta el final de cada uno de ellos.
