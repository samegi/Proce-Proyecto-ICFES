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
### 🔹 1. Importacion de Bibliotecas
- 1.1. Levantamiento de Variables de Entorno pip
- 1.2. Levantamiento de Sesión SPARK mediante `findspark`

### 🔹 2. Colección y descripcion de datos
Carga de los datos a utilizar en ambiente de trabajo Apache
(clúster spark) y se descripción de los datos según los siguientes
elementos:
- Tipos de datos.
- Comprensión del significado de cada atributo.

En esta sección se trabajan los datasets por separado.
- 2.1. Estadísticas en Educacion por Municipio

| Nombre de la columna | Descripción | Tipo de dato |
|---|---|---|
| AÑO | Vigencia del indicador | Texto |
| CÓDIGO_MUNICIPIO | Código DANE del municipio | Texto |
| MUNICIPIO | Nombre del municipio | Texto |
| CÓDIGO_DEPARTAMENTO | Código DANE del departamento | Texto |
| DEPARTAMENTO | Nombre del departamento | Texto |
| CÓDIGO_ETC | Código DANE de la entidad territorial certificada (ETC) | Texto |
| ETC | Nombre de la entidad territorial certificada (ETC) | Texto |
| POBLACIÓN_5_16 | Población en edad teórica de estudiar, entre 5 y 16 años, según proyecciones de población del DANE | Texto |
| TASA_MATRICULACIÓN_5_16 | Proporción de la población entre 5 y 16 años que se encuentra asistiendo al sistema educativo. * | Número |
| COBERTURA_NETA | Relación entre el número de estudiantes matriculados en transición, primaria, secundaria y media que tienen la edad teórica, entre 5 y 16 años, y el total de la población correspondiente a esa misma edad. * | Número |
| COBERTURA_NETA_TRANSICIÓN | Relación entre el número de estudiantes matriculados en transición que tienen la edad teórica para cursar este nivel, 5 años, y el total de la población correspondiente a esa misma edad. * | Número |
| COBERTURA_NETA_PRIMARIA | Relación entre el número de estudiantes matriculados en primaria que tienen la edad teórica para cursar este nivel, de 6 a 10 años, y el total de la población correspondiente a esa misma edad. * | Número |
| COBERTURA_NETA_SECUNDARIA | Relación entre el número de estudiantes matriculados en secundaria que tienen la edad teórica para cursar este nivel, de 11 a 14 años, y el total de la población correspondiente a esa misma edad. * | Número |
| COBERTURA_NETA_MEDIA | Relación entre el número de estudiantes matriculados en media que tienen la edad teórica para cursar este nivel, de 15 a 16 años, y el total de la población correspondiente a esa misma edad. * | Número |
| COBERTURA_BRUTA | Relación entre el número de estudiantes matriculados en transición, primaria, secundaria y media respecto a la población en edad teórica para cursar estos niveles, entre 5 y 16 años. En algunos casos, la demanda social es mayor a la población en edad teórica, explicada por estudiantes en extraedad, por lo que el indicador puede tomar valores superiores al 100%. | Número |

\* Cuando las proyecciones de población del DANE no capturan adecuadamente los flujos migratorios internos, el indicador puede alcanzar valores mayores al 100%.

- 2.2. Respuestas Saber 11 Bogotá y Chocó Calendario A

| Nombre de la columna | Descripción resumida | Tipo de dato |
|---|---|---|
| periodo | Periodo de presentación del examen | Numérica |
| estu_consecutivo | ID público del inscrito | Texto |
| estu_estudiante | Tipo de inscripción: colegio o individual | Texto |
| estu_tipodocumento | Tipo de documento del estudiante | Texto |
| cole_area_ubicacion | Área de ubicación de la sede | Texto |
| cole_bilingue | Indica si el colegio es bilingüe | Texto |
| cole_calendario | Calendario académico del colegio | Texto |
| cole_caracter | Carácter del establecimiento educativo | Texto |
| cole_cod_dane_establecimiento | Código DANE del establecimiento | Numérica |
| cole_cod_dane_sede | Código DANE de la sede | Numérica |
| cole_cod_depto_ubicacion | Código DANE del departamento de la sede | Numérica |
| cole_cod_mcipio_ubicacion | Código DANE del municipio de la sede | Numérica |
| cole_codigo_icfes | Código ICFES de la sede-jornada | Numérica |
| cole_depto_ubicacion | Departamento donde está ubicada la sede | Texto |
| cole_genero | Género de la población del establecimiento | Texto |
| cole_jornada | Jornada de la sede | Texto |
| cole_mcpio_ubicacion | Municipio donde está ubicada la sede | Texto |
| cole_naturaleza | Naturaleza del establecimiento | Texto |
| cole_nombre_establecimiento | Nombre del establecimiento educativo | Texto |
| cole_nombre_sede | Nombre de la sede | Texto |
| cole_sede_principal | Indica si es la sede principal | Texto |
| desemp_c_naturales | Nivel de desempeño en ciencias naturales | Numérica |
| desemp_ingles | Nivel de desempeño en inglés | Texto |
| desemp_lectura_critica | Nivel de desempeño en lectura crítica | Numérica |
| desemp_matematicas | Nivel de desempeño en matemáticas | Numérica |
| desemp_sociales_ciudadanas | Nivel de desempeño en sociales y ciudadanas | Numérica |
| estu_agregado | Indica si el estudiante cuenta para el informe nacional | Texto |
| estu_cod_depto_presentacion | Código DANE del departamento de presentación | Numérica |
| estu_cod_mcpio_presentacion | Código DANE del municipio de presentación | Numérica |
| estu_cod_reside_depto | Código DANE del departamento de residencia | Numérica |
| estu_cod_reside_mcpio | Código DANE del municipio de residencia | Numérica |
| estu_dedicacioninternet | Tiempo diario dedicado a internet no académico | Texto |
| estu_dedicacionlecturadiaria | Tiempo diario dedicado a lectura por entretenimiento | Texto |
| estu_depto_presentacion | Departamento donde presentó el examen | Texto |
| estu_depto_reside | Departamento de residencia | Texto |
| estu_discapacidad | Condición de discapacidad del estudiante | Texto |
| estu_etnia | Grupo étnico minoritario del estudiante | Texto |
| estu_fechanacimiento | Fecha de nacimiento | Texto |
| estu_genero | Género del estudiante | Texto |
| estu_grado | Grado cursado al presentar la prueba | Numérica |
| estu_horassemanatrabaja | Horas trabajadas durante la semana anterior | Texto |
| estu_inse_individual | Índice socioeconómico individual | Numérica |
| estu_mcpio_presentacion | Municipio donde presentó el examen | Texto |
| estu_mcpio_reside | Municipio de residencia | Texto |
| estu_nacionalidad | Nacionalidad del estudiante | Texto |
| estu_nse_establecimiento | Nivel socioeconómico del establecimiento | Numérica |
| estu_nse_individual | Nivel socioeconómico individual | Texto |
| estu_pais_reside | País de residencia | Texto |
| estu_privado_libertad | Indica si está privado de la libertad | Texto |
| estu_repite | Identificador de repitencia de la prueba | Numérica |
| estu_tiporemuneracion | Indica si recibe remuneración por trabajar | Texto |
| fami_comecarnepescadohuevo | Frecuencia de consumo de carne, pescado o huevo | Texto |
| fami_comecerealfrutoslegumbre | Frecuencia de consumo de cereales, frutos secos o legumbres | Texto |
| fami_comelechederivados | Frecuencia de consumo de leche o derivados | Texto |
| fami_cuartoshogar | Número de cuartos usados para dormir en el hogar | Texto |
| fami_educacionmadre | Nivel educativo de la madre | Texto |
| fami_educacionpadre | Nivel educativo del padre | Texto |
| fami_estratovivienda | Estrato socioeconómico de la vivienda | Texto |
| fami_numlibros | Número de libros en el hogar | Texto |
| fami_personashogar | Número de personas en el hogar | Numérica |
| fami_situacioneconomica | Situación económica del hogar frente al año anterior | Texto |
| fami_tieneautomovil | Tenencia de automóvil en el hogar | Texto |
| fami_tienecomputador | Tenencia de computador en el hogar | Texto |
| fami_tieneconsolavideojuegos | Tenencia de consola de videojuegos | Texto |
| fami_tienehornomicroogas | Tenencia de horno microondas, eléctrico o a gas | Texto |
| fami_tieneinternet | Acceso a internet en el hogar | Texto |
| fami_tienelavadora | Tenencia de lavadora | Texto |
| fami_tienemotocicleta | Tenencia de motocicleta | Texto |
| fami_tieneserviciotv | Acceso a televisión cerrada | Texto |
| fami_trabajolabormadre | Ocupación o labor principal de la madre | Texto |
| fami_trabajolaborpadre | Ocupación o labor principal del padre | Texto |
| percentil_c_naturales | Percentil en ciencias naturales | Numérica |
| percentil_global | Percentil global del evaluado | Numérica |
| percentil_ingles | Percentil en inglés | Numérica |
| percentil_lectura_critica | Percentil en lectura crítica | Numérica |
| percentil_matematicas | Percentil en matemáticas | Numérica |
| percentil_sociales_ciudadanas | Percentil en sociales y ciudadanas | Numérica |
| punt_c_naturales | Puntaje en ciencias naturales | Numérica |
| punt_global | Puntaje total obtenido | Numérica |
| punt_ingles | Puntaje en inglés. El valor -1 indica que no contestó | Numérica |
| punt_lectura_critica | Puntaje en lectura crítica | Numérica |
| punt_matematicas | Puntaje en matemáticas | Numérica |
| punt_sociales_ciudadanas | Puntaje en sociales y ciudadanas | Numérica |

### 🔹 3. Exploración de datos
- Análisis de variables educativas:
  - Población entre 5 y 16 años
  - Tasas de matriculación
  - Cobertura educativa
- Visualizaciones:
  - Gráficos de barras
  - Gráficos de torta
  - Diagramas de cajas (boxplot)
- Análisis pruebas Saber 11
  - Distribución del puntaje global
  - Promedios por área
  - Comparación entre Bogotá y Chocó
  - Visualización tipo radar
### 🔹 4. Reporte de Calidad
Para cada uno de los dataset.
### 🔹 5. Filtros, limpieza y transformación
- Estadísticas en Educacion por Municipio
  - Limpieza
  -   Eliminacion de variables
  -   Tipo y coherencia de los datos
  - Transformacion
- Respuestas Saber 11 Bogotá y Chocó Calendario A
  - Filtros
  - Transformacion
  - Limpieza
### 🔹 6. Respuestas preguntas de Negocio.
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
