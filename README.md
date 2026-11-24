Vista previa de solo lectura de README(proyecto_7).md
README(proyecto_7)
Análisis de Comportamiento de Usuarios de Telecomunicaciones
🎯 Objetivo del proyecto
Analizar el comportamiento de uso (llamadas, mensajes y minutos de llamada) de una base de usuarios de un servicio de telecomunicaciones en Latinoamérica, con el fin de:
Limpiar y consolidar la información proveniente de distintas fuentes de datos.
Identificar patrones de uso, valores atípicos y su relación con el tipo de plan contratado (Básico vs. Premium).
Segmentar a los usuarios por edad y nivel de uso.
Generar insights accionables para la toma de decisiones de negocio (marketing, retención y estrategias de upsell).
📂 Datasets utilizados
Archivo
Descripción
plans.csv
Información sobre los planes disponibles (Básico y Premium).
users_latam.csv
Datos demográficos de los usuarios: user_id, age, city, plan, reg_date, churn_date.
usage.csv
Registro de actividad por usuario: llamadas y mensajes, incluyendo type, duration, length y date.
🔍 Etapas del análisis
Carga y exploración inicial de los datos
Revisión de tipos de datos, dimensiones y estructura de cada dataset.
Limpieza de datos
2. Detección y corrección de valores centinela (999 en age) mediante recodificación a NaN e imputación por mediana.
3. Estandarización de valores faltantes representados como texto ("?", "NA") a NaN real.
4. Conversión de columnas de fecha a formato datetime y corrección de fechas inválidas (fuera de rango esperado).
5. Corrección de inconsistencias estructurales en usage.csv (valores de duration en registros de tipo text y viceversa).
Transformación y agregación
2. Creación de columnas auxiliares (is_text, is_call) para contabilizar mensajes y llamadas.
3. Agregación de usage.csv por user_id (total de mensajes, llamadas y minutos de llamada).
4. Combinación (merge) de la tabla agregada con users_latam.csv para construir el DataFrame user_profile.
Detección de valores atípicos (outliers)
2. Visualización mediante boxplots de las variables numéricas (age, cant_mensajes, cant_llamadas, cant_minutos_llamada).
3. Cálculo de límites mediante el método IQR.
4. Análisis cruzado de outliers contra la variable plan, para diferenciar entre errores de datos y comportamiento real de usuarios de alto consumo.
Segmentación de usuarios
2. Creación de la columna grupo_uso (Bajo uso / Uso medio / Alto uso) según cantidad de llamadas y mensajes.
3. Creación de la columna grupo_edad para análisis demográfico.
Visualización y análisis exploratorio
2. Histogramas de age, cant_mensajes, cant_llamadas y cant_minutos_llamada, segmentados por plan.
3. Gráficos de distribución por grupo_uso y grupo_edad.
Generación de insights y recomendaciones
Interpretación de los hallazgos y traducción a recomendaciones orientadas a negocio (marketing, retención, upsell a Premium).
▶️ Cómo ejecutar el notebook
Clona este repositorio:
Los rangos usados para grupo_uso (Bajo/Medio/Alto) y grupo_edad pueden modificarse directamente en las celdas correspondientes según el criterio de negocio que necesites aplicar.
Todas las visualizaciones están construidas con matplotlib y seaborn; si agregas nuevas variables, puedes replicar el mismo patrón de bucles for usado para generar los boxplots e histogramas de forma automática.
🛠️ Tecnologías utilizadas
Python 3.9
pandas
NumPy
Matplotlib
Seaborn
Jupyter Notebook
👤 Autor
Ulises — Proyecto desarrollado como parte de la certificación de Data Analyst en TripleTen.
