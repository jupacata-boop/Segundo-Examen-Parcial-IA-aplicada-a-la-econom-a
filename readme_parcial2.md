# Segundo Parcial - IA para la Economía 2025-2
**Universidad de los Andes - Facultad de Economía**

## Información del Proyecto

Este repositorio contiene el desarrollo del segundo parcial de la materia "IA para la Economía", enfocado en la aplicación de técnicas de Deep Learning y análisis exploratorio avanzado (EDA) para resolver problemas económicos utilizando el dataset Adult Income Census.

### Integrantes del Equipo
- María Alejandra Velásquez (202113333)
- Juan Pablo Camacho (202110977)

### Objetivos
- Implementar análisis exploratorio de datos robusto para problemas económicos
- Aplicar técnicas estadísticas avanzadas para evaluación de datasets
- Desarrollar habilidades en diagnóstico de calidad de datos
- Preparar fundamentos para modelos de Deep Learning

## Dataset: Adult Income Census

**Fuente**: UCI Machine Learning Repository - Adult Dataset  
**Problema**: Predicción de ingresos (<=50K vs >50K) basado en características socioeconómicas  
**División**: Train (32,561 registros) + Test (16,281 registros)  

### Variables del Dataset
- **Demográficas**: age, race, sex, native_country
- **Educativas**: education, education_num  
- **Laborales**: workclass, occupation, hours_per_week
- **Familiares**: marital_status, relationship
- **Financieras**: capital_gain, capital_loss, fnlwgt
- **Objetivo**: income (<=50K, >50K)

## Metodología de Análisis

### 1. Análisis Exploratorio Reforzado (EDA)

#### Evaluación Básica
- **Descripción general** de estructura y tipos de datos
- **Balance de clases** en conjuntos de entrenamiento y prueba
- **Distribución de variables** categóricas y numéricas

#### Calidad de Datos
- **Valores faltantes** por columna con análisis de patrones
- **Categorías raras** (frecuencia < 1%) para variables categóricas
- **Detección de duplicados** en ambos conjuntos

#### Estabilidad Train-Test
- **Population Stability Index (PSI)** para variables numéricas
- Evaluación de drift entre conjuntos de entrenamiento y prueba
- Interpretación: PSI ≈ 0 (estable), > 0.1 (alerta), > 0.25 (severo)

### 2. Análisis de Separabilidad

#### Variables Numéricas
- **Distribuciones por clase** usando kernel density estimation
- **Correlación punto-biserial** para medir relación con variable objetivo
- **Detección de outliers** usando método IQR (rango intercuartílico)

#### Variables Categóricas
- **Tasa de ingresos >50K** por categoría
- **Mutual Information** para medir dependencia con variable objetivo
- **Visualizaciones comparativas** de distribuciones

### 3. Técnicas Estadísticas Implementadas

```python
# Análisis principales
- Point-biserial correlation
- Population Stability Index (PSI)
- Mutual Information Score
- IQR-based outlier detection
- Kernel Density Estimation
```

## Tecnologías Utilizadas

```python
# Librerías de análisis
pandas                 # Manipulación de datos
numpy                  # Operaciones numéricas
scipy.stats            # Tests estadísticos

# Visualización
matplotlib.pyplot      # Gráficos básicos
seaborn               # Visualizaciones estadísticas

# Machine Learning
sklearn.metrics        # Métricas de evaluación
```

## Estructura del Repositorio

```
├── parcial_2_ia_economía.py    # Código principal del análisis
├── adult.zip                   # Dataset comprimido
├── results/                    # Resultados del análisis
│   ├── eda_visualizations/     # Gráficos generados
│   └── statistical_reports/    # Reportes estadísticos
└── README.md                   # Este archivo
```

## Instrucciones de Ejecución

### Prerrequisitos
```bash
pip install pandas numpy matplotlib seaborn scipy scikit-learn
```

### Ejecución en Google Colab
1. Subir el archivo `adult.zip` a Colab
2. Ejecutar el script `parcial_2_ia_economía.py`
3. Los resultados se mostrarán en línea con visualizaciones

### Montaje de Google Drive
```python
from google.colab import drive
drive.mount('/content/drive')
```

## Resultados Principales

### Balance de Clases
- **Train**: ~76% (<=50K), ~24% (>50K)
- **Test**: Distribución similar, indicando consistencia

### Variables Más Informativas
**Numéricas** (correlación punto-biserial):
- education_num: Mayor educación → mayores ingresos
- age: Relación positiva con ingresos
- hours_per_week: Horas trabajadas correlacionan con ingresos

**Categóricas** (Mutual Information):
- marital_status: Estado civil fuertemente predictivo
- relationship: Tipo de relación familiar relevante
- occupation: Ocupación altamente informativa

### Calidad de Datos
- **Valores faltantes**: Principalmente en workclass, occupation, native_country
- **Outliers**: Concentrados en capital_gain y capital_loss
- **Estabilidad**: PSI indica distribuciones estables entre train/test

## Aplicaciones Económicas

### Análisis de Inequidad Salarial
- Identificación de factores socioeconómicos determinantes
- Evaluación de brechas por género, raza y educación
- Análisis de segmentación del mercado laboral

### Políticas Públicas
- Targeting para programas de capacitación laboral
- Identificación de grupos vulnerables económicamente
- Evaluación de impacto de educación en ingresos

### Investigación Socioeconómica
- Patrones de movilidad social y económica
- Factores de estratificación socioeconómica
- Análisis de mercado laboral por demografías

## Insights Económicos Clave

1. **Educación como Factor Crítico**: education_num muestra correlación fuerte con ingresos
2. **Segmentación Ocupacional**: Ciertas ocupaciones concentran altos ingresos
3. **Demografía Predictiva**: Edad y estado civil son altamente informativos
4. **Capital vs Trabajo**: Variables de capital (gain/loss) muestran alta variabilidad

## Preparación para Deep Learning

Este EDA robusto establece las bases para:
- **Feature Engineering** informado por análisis estadístico
- **Arquitecturas de red** apropiadas para el problema
- **Estrategias de regularización** basadas en outliers detectados
- **Métricas de evaluación** considerando desbalance de clases

## Referencias Técnicas

- UCI Machine Learning Repository - Adult Dataset
- Population Stability Index en Risk Management
- Point-biserial correlation para variables binarias
- Mutual Information en Feature Selection

---

**Evaluación**: Parcial-Taller desarrollado en clase (Semana 8)  
**Modalidad**: 100% evaluación práctica  
**Enfoque**: Fundamentos de Deep Learning aplicado a economía

> **Cumplimiento Académico**: Este proyecto se desarrolla bajo las políticas de integridad académica de la Universidad de los Andes, con código original y referencias apropiadas a fuentes consultadas.