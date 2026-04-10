# 📊 Análisis de Datos Educativos con Apache Spark

## 📌 Descripción del proyecto

Este proyecto realiza un análisis exploratorio de datos educativos en Colombia, enfocado en:

- Estadísticas del sistema educativo a nivel municipal  
- Comparación entre el departamento del Chocó y Bogotá D.C.  
- Análisis de resultados de las pruebas Saber 11  

## 📌 Objetivos del proyecto
- Objetivo General: 

  - Aumentar en un 20% el puntaje promedio de las pruebas Saber 11° de los colegios calendario A del departamento del Chocó, con base de los resultados del 2023, para el año 2027
- Objetivos Esoecificos:
  - Evidenciar las tasas de matrícula y cobertura educativa en los municipios de Bogotá D.C. y el departamento del Chocó.
  - Identificar los factores que presentan mayor incidencia en el desempeño de las pruebas Saber 11 en Chocó y Bogotá D.C., a partir de variables individuales y del territorio.
  - Comparar los factores que inciden en el desempeño en Bogotá D.C. y Chocó, con el fin de identificar si estos son consistentes entre ambos territorios.
  - Proponer un plan de acción basado en los hallazgos del análisis.

El procesamiento de los datos se realiza utilizando **Apache Spark** en un entorno de **Jupyter Notebook**, aprovechando capacidades de procesamiento distribuido.

---

## 🧠 Contenido del análisis

El cuaderno incluye las siguientes etapas:

### 🔹 Colección y preparación de datos
- Importación de librerías
- Inicialización de Spark mediante `findspark`
- Carga de datasets

### 🔹 Exploración de datos
- Conversión entre estructuras PySpark y Pandas
- Análisis de variables educativas:
  - Población entre 5 y 16 años
  - Tasas de matriculación
  - Cobertura educativa
- Visualizaciones:
  - Gráficos de barras
  - Gráficos de torta
  - Diagramas de cajas (boxplot)

### 🔹 Análisis pruebas Saber 11
- Distribución del puntaje global
- Promedios por área
- Comparación entre Bogotá y Chocó
- Visualización tipo radar  

---

## ⚙️ Requisitos del sistema

Para ejecutar correctamente el proyecto, se requiere:

### 🔸 Software necesario

- Python **3.8 o superior**
- Apache Spark **3.x**
- Java **8 o 11** (necesario para Spark)
- Jupyter Notebook o Jupyter Lab

---

## 📦 Librerías de Python

Instalar las siguientes librerías:

```bash
pip install pyspark pandas matplotlib seaborn findspark
```

---

## 🔧 Configuración de Apache Spark

1. Descargar Apache Spark desde:  
   👉 https://spark.apache.org/downloads.html  

2. Configurar variables de entorno:

### En Linux / Mac:
```bash
export SPARK_HOME=/ruta/a/spark
export PATH=$SPARK_HOME/bin:$PATH
```

### En Windows:
- Configurar `SPARK_HOME`
- Agregar `SPARK_HOME/bin` al `PATH`

---

## ▶️ Ejecución del proyecto

1. Clonar el repositorio:

```bash
git clone https://github.com/tu-usuario/tu-repo.git
cd tu-repo
```

2. Abrir el notebook:

```bash
jupyter notebook
```

3. Ejecutar el archivo `.ipynb`

---

## 📁 Estructura del proyecto

```
.
├── data/                # Archivos CSV utilizados
├── notebooks/           # Cuaderno de análisis
├── README.md
```

---

## ⚠️ Consideraciones importantes

- Las rutas de los archivos están configuradas de forma **relativa** para facilitar la portabilidad del proyecto.
- El proyecto fue originalmente ejecutado en un **cluster con Apache Spark**, por lo que el rendimiento puede variar en un entorno local.
- Se recomienda contar con suficiente memoria RAM para manejar los datasets.

---

## 💡 Nota final

Este proyecto demuestra el uso de herramientas de procesamiento de datos a gran escala para analizar problemáticas educativas en Colombia, combinando técnicas de análisis exploratorio y visualización de datos.
