

# 📝 Principales Insights y Hallazgos

<details>
<summary><b>🔍 Database No Filtrada (Vista General)</b></summary>
<br>

Se analizan cuatro bloques sin aplicar ningún filtro dinámico, es decir, se analiza la base de datos al completo.

### 1. Métricas Salariales y Puestos
* **Salario Mediano General:** **$113,000/año** ($47.62/hora).
* **Roles Mejor Pagados:**
  * **Senior Data Scientist:** $156,000/año
  * **Machine Learning Engineer:** $155,000/año ($60.75/hora)
  * **Software Engineer / Senior Data Engineer:** ~$145,000 - $147,000/año
* **Roles con Mayor Volumen de Ofertas:**
  * **Data Analyst:** 112,866 ofertas
  * **Data Scientist:** 97,664 ofertas
  * **Data Engineer:** 128,994 ofertas

### 2. Stack Técnico Más Demandado
Las tecnologías más requeridas en las ofertas laborales se concentran en datos y nube:
1. **Python** y **SQL** (Líderes indiscutibles con más de 200,000 menciones cada uno)
2. **AWS** y **Azure** (Infraestructura Cloud)
3. **Tableau**, **Spark**, **R**, **Excel**, **Power BI** y **Java**

### 3. Condiciones Laborales y Beneficios
* **Opción de Teletrabajo:** Presente únicamente en el **13.15%** de las ofertas publicadas.
* **Titulación Específica:** Requerida en el **67.48%** de las posiciones.
* **Seguro Médico:** Incluido en el **12.83%** de las vacantes.

### 4. Tendencia Temporal de Contratación (2024)
* **Pico de demanda:** El primer semestre mantuvo un volumen alto y constante (promedio de 45,000 a 55,000 ofertas mensuales entre enero y julio).
* **Caída sustancial:** Se observa una desaceleración pronunciada a partir de agosto, alcanzando el punto más bajo en noviembre (14,000 ofertas), seguido de una ligera recuperación en diciembre (31,000 ofertas).
</details>


<details>
<summary><b>🔍 Sector Tech en Suiza</b></summary>
<br>

Al aislar la muestra del mercado suizo (3.689 ofertas de empleo), el panel revela patrones claros sobre la demanda de perfiles analíticos y técnicos:

1. **Stack Tecnológico Predominante:** **Python** y **SQL** se consolidan como los dos pilares absolutos e indiscutibles exigidos por los empleadores, seguidos por plataformas *Cloud* (AWS y Azure).
2. **Cultura de Trabajo y Presencialidad:** El **92.71%** de las ofertas de empleo no contemplan la opción de teletrabajo 100% remoto, evidenciando una fuerte preferencia por modelos presenciales o híbridos rigurosos en el sector corporativo y asegurador suizo.
3. **Distribución de Roles:** Alta concentración de vacantes orientadas a *Data Engineer*, *Data Scientist* y *Data Analyst*.
4. **Temporalidad y Estacionalidad del Mercado Suizo:** Se aprecia un pico claro de ofertas a principios de primavera (marzo/abril) y un repunte en verano (julio), seguido de una caída drástica hacia septiembre y noviembre. Esto refleja el ciclo presupuestario corporativo y bancario suizo: los presupuestos de contratación tecnológica se abren fuertemente tras el cierre de Q1, y se congelan bruscamente hacia el final del año fiscal.

<img width="1257" height="772" alt="dashboard_suiza" src="https://github.com/user-attachments/assets/8151d4c4-0522-4372-8c66-feb80ef6324a" />


Durante la fase de exploración visual se identificó una anomalía en las tarjetas KPI salariales del dataset filtrado (mediana salarial de **$88k/año**), cifra sensiblemente inferior a la media macroeconómica real de plazas como Zúrich o Ginebra, donde los rangos medios oscilan entre **$110k - $145k+**. El origen del error puede deberse a la presencia de registros con salarios atípicos muy bajos (e.g., $30,72K o $34,56K) procedentes del *scraping* de portales internacionales, correspondientes a contratos en prácticas o erratas en la conversión de salarios mensuales/por horas a la tasa anual.
Para la preparación de este modelo a un entorno de producción o reporting directivo, se propone que el *pipeline* en Power Query requiera de un filtrado IQR para la eliminación de *outliers* salariales inferiores a $80k, o la imputación condicional por mediana según el rol (`job_title_short`).

