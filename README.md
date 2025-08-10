# 📊 Análisis de Churn - TelecomX

**Predicción y Reducción de Evasión de Clientes en Telecomunicaciones**

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-1.3%2B-green.svg)](https://pandas.pydata.org/)
[![Matplotlib](https://img.shields.io/badge/Matplotlib-3.5%2B-orange.svg)](https://matplotlib.org/)
[![Seaborn](https://img.shields.io/badge/Seaborn-0.11%2B-lightblue.svg)](https://seaborn.pydata.org/)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

## 🎯 Descripción del Proyecto

Este proyecto realiza un **análisis exploratorio completo** para identificar los factores determinantes en la evasión de clientes (churn) de una empresa de telecomunicaciones. A través de técnicas de ciencia de datos, se identifican patrones críticos que permiten desarrollar estrategias efectivas de retención de clientes.

### 🔍 Objetivos Principales

- **Identificar factores críticos** que influyen en la decisión de abandonar el servicio
- **Segmentar clientes por nivel de riesgo** de churn
- **Desarrollar recomendaciones estratégicas** basadas en datos para reducir la evasión
- **Cuantificar el impacto financiero** de las mejoras propuestas

### 📈 Resultados Clave

- **Tasa de churn actual**: 26.54% (superior al promedio de la industria)
- **Factor más protector**: Antigüedad del cliente (correlación: -0.352)
- **Mayor riesgo**: Contratos mes-a-mes con 42.71% de churn
- **Oportunidad financiera**: $796K anuales en ingresos adicionales potenciales

## 📂 Estructura del Proyecto

```
telecomx/
│
├── README.md                          # Documentación principal
├── TelecomX.ipynb                    # Notebook principal con análisis completo
├── requirements.txt                   # Dependencias del proyecto

```

## 🛠️ Tecnologías Utilizadas

### Lenguajes y Frameworks
- **Python 3.8+**: Lenguaje principal
- **Jupyter Notebook**: Entorno de desarrollo

### Bibliotecas Principales
```python
# Manipulación de datos
pandas>=1.3.0
numpy>=1.21.0

# Visualización
matplotlib>=3.5.0
seaborn>=0.11.0
plotly>=5.0.0  # Para gráficos interactivos

# Análisis estadístico
scipy>=1.7.0
statsmodels>=0.13.0

# Utilidades
requests>=2.25.0  # Para descarga de datos
json>=2.0.0       # Procesamiento JSON
```

## 🚀 Instalación y Configuración

### 1. Clonar el Repositorio
```bash
git clone https://github.com/tu-usuario/telecomx-churn-analysis.git
cd telecomx-churn-analysis
```

### 2. Crear Entorno Virtual (Recomendado)
```bash
# Usando venv
python -m venv venv
source venv/bin/activate  # En Windows: venv\Scripts\activate

# O usando conda
conda create -n churn-analysis python=3.8
conda activate churn-analysis
```

### 3. Instalar Dependencias
```bash
pip install -r requirements.txt
```

### 4. Verificar Instalación
```python
python -c "import pandas, matplotlib, seaborn; print('✅ Instalación exitosa')"
```

## 📊 Uso del Proyecto

### Ejecución Completa del Análisis

1. **Abrir Jupyter Notebook**:
   ```bash
   jupyter notebook TelecomX.ipynb
   ```

2. **Ejecutar todas las celdas** o seguir el análisis paso a paso:
   - Carga y limpieza de datos
   - Análisis exploratorio
   - Visualizaciones
   - Generación del informe

### Ejecución por Módulos

#### Procesamiento de Datos
```python
from src.data_processing import load_and_clean_data

# Cargar y limpiar datos
df = load_and_clean_data('data/TelecomX_Data.json')
print(f"Dataset cargado: {df.shape[0]} registros, {df.shape[1]} variables")
```

#### Visualizaciones Clave
```python
from src.visualization import plot_churn_by_contract, correlation_heatmap

# Generar gráfico de churn por tipo de contrato
plot_churn_by_contract(df)

# Generar mapa de correlaciones
correlation_heatmap(df)
```

#### Análisis de Segmentación
```python
from src.analysis_utils import segment_customers, calculate_risk_scores

# Segmentar clientes por riesgo
segments = segment_customers(df)
risk_scores = calculate_risk_scores(df)
```

## 📋 Dataset y Variables

### Fuente de Datos
- **Origen**: Empresa de telecomunicaciones TelecomX
- **Formato**: JSON
- **Registros**: 7,043 clientes
- **Variables**: 21 características

### Variables Principales

| Variable | Tipo | Descripción |
|----------|------|-------------|
| `customer_id` | String | Identificador único del cliente |
| `Abandono` | Binary | Target: 1=Abandonó, 0=Permaneció |
| `Meses_Contrato` | Numeric | Antigüedad en meses |
| `Cargo_Mensual` | Numeric | Cargo mensual en USD |
| `Tipo_Contrato` | Categorical | Mes-a-mes, 1 año, 2 años |
| `Servicio_Internet` | Categorical | DSL, Fibra óptica, Sin internet |
| `Adulto_Mayor` | Binary | Cliente mayor de 65 años |
| `Metodo_Pago` | Categorical | Forma de pago preferida |

> 📖 **Diccionario completo**: Ver `docs/diccionario_datos.md`

## 📊 Resultados y Hallazgos

### Insights Principales

1. **🔴 Contratos Flexibles = Alto Riesgo**
   - Contratos mes-a-mes: **42.71% churn**
   - Contratos 2 años: **2.83% churn**

2. **⚠️ Paradoja de Fibra Óptica**
   - Servicio premium con **41.89% churn**
   - Indica problemas de calidad o expectativas

3. **🎯 Antigüedad es Protección**
   - Correlación más fuerte: **-0.352**
   - Cada mes adicional reduce probabilidad de churn

4. **👥 Segmentación de Riesgo**
   - **Alto riesgo**: 1,043 clientes (tasa ~65% churn)
   - **Bajo riesgo**: 1,500 clientes (tasa ~5% churn)

### Impacto Financiero Proyectado

| Métrica | Actual | Con Mejoras | Beneficio |
|---------|--------|-------------|-----------|
| **Tasa Churn** | 26.54% | 15.00% | -43.5% |
| **Clientes Retenidos** | - | +815 | +$633K/año |
| **ROI Iniciativas** | - | - | **298%** |

## 🎯 Recomendaciones Estratégicas

### Acciones Inmediatas (0-3 meses)
- [ ] **Migración contractual**: Incentivos para contratos anuales
- [ ] **Auditoría técnica**: Revisar calidad de fibra óptica
- [ ] **Programa VIP**: Atención especial a adultos mayores

### Mediano Plazo (3-12 meses)
- [ ] **Optimización de pagos**: Eliminar cheques electrónicos
- [ ] **Bundling inteligente**: Paquetes personalizados
- [ ] **Pricing dinámico**: Descuentos por antigüedad

### Largo Plazo (1-2 años)
- [ ] **Programa de lealtad**: Beneficios escalonados
- [ ] **Predicción proactiva**: ML para identificar riesgo
- [ ] **Experiencia omnicanal**: Coherencia en todos los puntos

```

## 📈 Métricas de Éxito del Proyecto

- ✅ **Análisis Completo**: 7,043 registros procesados
- ✅ **Visualizaciones**: 12+ gráficos profesionales generados
- ✅ **Insights Accionables**: 5 recomendaciones estratégicas principales
- ✅ **ROI Calculado**: $796K anuales en oportunidad identificada
- ✅ **Segmentación**: 4 grupos de riesgo definidos

## 🤝 Contribuciones

Si deseas contribuir a este proyecto:

1. **Fork** el repositorio
2. Crea una **branch** para tu feature (`git checkout -b feature/nueva-funcionalidad`)
3. **Commit** tus cambios (`git commit -am 'Agregar nueva funcionalidad'`)
4. **Push** a la branch (`git push origin feature/nueva-funcionalidad`)
5. Crea un **Pull Request**

### Áreas de Mejora Identificadas

- [ ] Implementar modelos de Machine Learning predictivos
- [ ] Crear dashboard interactivo con Plotly/Dash
- [ ] Automatizar pipeline de datos con Apache Airflow
- [ ] Integrar análisis de texto en comentarios de clientes
- [ ] Desarrollar API REST para scoring en tiempo real

---


**⭐ Si este proyecto te resulta útil, no olvides darle una estrella en GitHub**

*Última actualización: Agosto 2025*
