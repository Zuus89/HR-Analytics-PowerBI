# 📊 HR Analytics in Power BI

Este proyecto tiene como objetivo principal desarrollar un dashboard de análisis de RR.HH. para una empresa ficticia llamada **Atlas Labs**, con foco en entender el estado actual del personal, diversidad e inclusión, desempeño individual y rotación de empleados.

---

## 🛠️ Estructura del Reporte

El reporte fue dividido en **cuatro páginas principales**:

### 1. **Overview**
- Total de empleados (`_TotalEmployees`)
- Empleados activos e inactivos
- Tasa de rotación general (`_%AttritionRate`)
- Distribución de empleados por edad (`AgeBins`) y género
- Visuales:
  - Cards de edad mínima, máxima y fecha de ingreso
  - Donut chart por estado civil
  - Gráfico combinado de empleados y salario promedio

### 2. **Diversity & Inclusion**
- Análisis por género, edad, estado civil y etnia
- Visuales:
  - TreeMap y gráficos apilados por género y edad
  - Distribución por estado civil (donut chart)
  - Visuales cruzadas por `Department`, `JobRole` y `Gender`

### 3. **Performance Tracker**
- Página dinámica para hacer seguimiento individual
- Elementos destacados:
  - Slicer con `FullName` (single select + search)
  - Cards para:
    - Fecha de ingreso (`HireDate`)
    - Última revisión (`_LastReviewDate`)
    - Próxima revisión (`_NextReviewDate`)
  - Medidas para satisfacción:
    - `_JobSatisfaction`
    - `_EnvironmentSatisfaction`
    - `_RelationshipSatisfaction`
    - `_WorkLifeBalance`
  - Gráficos por año con evolución de evaluaciones

### 4. **Attrition Insights**
- Tasa de rotación por:
  - Departamento y cargo (TreeMap)
  - Año de contratación (`_%AttritionRateDate`)
- Uso de relaciones inactivas activadas con `USERELATIONSHIP()` para trabajar con `HireDate`
- Visuales explicativas de qué cohortes tienen mayor fuga de empleados

---

## 🧠 Técnicas y conceptos utilizados

- Modelado de datos con esquema tipo **Snowflake**
- Creación de tabla de fechas (`DimDate`) con múltiples columnas derivadas (trimestres, semanas, fiscal, etc.)
- Relaciones activas/inactivas entre fechas y otras tablas
- Medidas DAX utilizando:
  - `CALCULATE()`
  - `USERELATIONSHIP()`
  - `DIVIDE()`
  - `FORMAT()` para control de fechas y texto
- Visualizaciones avanzadas:
  - Treemaps, gráficos combinados, line charts, tarjetas (cards), slicers con búsqueda
- Segmentación dinámica por empleado
- Cálculos de rotación (Attrition Rate) por cohortes y dimensiones clave

---

## 🧩 Dataset

El modelo se compone de una tabla de hechos (`Fact_PerformanceRating`) y varias tablas de dimensiones:
- `Dim_Employee`
- `Dim_EducationLevel`
- `Dim_RatingLevel`
- `Dim_SatisfiedLevel`
- `DimDate` (calculada)
