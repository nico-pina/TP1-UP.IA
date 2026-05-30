
# Impacto uso de IAg en estudiantes universitarios


### Objetivo del Trabajo

Este proyecto tiene como objetivo realizar un análisis exploratorio de datos
(EDA) sobre el impacto del uso de herramientas de la Inteligencia Artificial Generativa (IAg) en el desempeño académico y bienestar social y psicológicos de estudiantes de educación superior. Este EDA incluye visualizaciones y parámetros estadísticos que buscan identificar tendencias que respondan a hipótesiss y preguntas de investigación que se plantearon en torno al Uso de la IAg en el contexto educacional.


### Contexto del Dataset

El Dataset ``ai_student_impact.csv`` obtenido en este [enlace](https://www.kaggle.com/datasets/laveshjadon/ai-impact-on-students) contiene información sobre el impacto del uso de la IAg en estudiantes desde una mirada multidimensional, ya que incluye datos asociados a resultados académicos, patrones de comportamiento, políticas institucionales y factores psicológicos. El dataset no presenta valores nulos ni registros duplicados, lo que facilitó el análisis ya que no requirió limpieza previa de los datos.

### Diccionario de datos

| **Variable** | **Tipo** | **Descripción** | **Valores** |
| --- | --- | --- | --- |
| ``Student_ID`` | int64 | Identificador del estudiante | Entero, sin repetición con prefijo 10000n°. |
| ``Major_Category`` | object | Área de estudio | STEM, Humanities, Business, Arts y Medical. |
| ``Year_of_Study`` | object | Año de la carrera | Senior, Junior, Freshman, Sophomore, Graduate.|
| ``Pre_Semester_GPA`` | float64 | Promedio previo al semestre | Escala de 0 a 4 |
| ``Weekly_GenAI_Hours`` | float64 | Horas semanales de uso de IAg| Rango  0–~40 h |
| ``Primary_Use_Case`` | object | Uso principal de IA | Copywriting/Drafting , Ideation, Summarizing_Reading, Debugging/Troubleshooting, etc. |
| ``Prompt_Engineering_Skill`` | int64 | Nivel de habilidad en prompts | Beginner, Advanced, Intermediate. |
| ``Tool_Diversity`` | int64 | Cantidad de herramientas de IA usadas | Rango 1-5 |
| ``Paid_Subscription`` | bool | Tiene suscripción pagada a IA | ``True`` / ``False`` |
| ``Traditional_Study_Hours`` | float64 | Horas semanales de estudio tradicional | Rango: 0–~40h |
| ``Perceived_AI_Dependency`` | int64 | Nivel percibido de dependencia a IAg | Rango 1–10 |
| ``Institutional_Policy`` | object | Política institucional sobre el uso de IAg | Allowed_With_Citation, Strict_Ban, Actively_Encouraged. |
| ``Anxiety_Level_During_Exams`` | int64 | Nivel percibido de ansiedad durante exámenes |Rango 1–10|
| ``Post_Semester_GPA`` | float64 | Promedio posterior al semestre | Escala de 0 a 4  |
| ``Skill_Retention_Score`` | float64 | Retención percibida de habilidades tras el semestre | Rango ~10–100 |
| ``Burnout_Risk_Level`` | object | Nivel de riesgo de burnout | Low, Medium, High.|

### Metodología Aplicada

El análisis del DataSet se llevó a cabo en Python en JupyterLab usando cuatro principales bibliotecas para un EDA básico: ``pandas ``, ``numpy``,``matplotlib`` y ``seaborn``. El proceso para realizar en análisis exploratorio se detalla a continuación:

En primer lugar, se realizó la carga del Dataset ``ai_student_impact.csv`` y se hizo una revisión inicial usando funciones internas de Pandas como ``df.head()``, ``df.tail()``,``df.info()``,etc. En esta etapa se verificó que el dataset constaba con 50.000 observaciones en 16 columnas.

Luego, se realizó una revisión de la existencia de datos nulos y valores duplicados. Este análisis mostró que todas las columnas contienen valores completos y no hay datos duplicados. Esto último permitió avanzar sin necesidad de realizar procesos de imputación o purificación de los datos. 

Posteriormente, se llevó a cabo un análisis exploratorio de los datos EDA que incluyó parámetros estadísticos básicos (mediana y media) y elaboración de diversas visualizaciones, como histogramas con KDE, diagramas de dispersión,etc.  En paralelo, se realizó transformaciones en ciertos datos para obtener visualizaciones acordes al propósito de cada análisis.

Todas las etapas, desde la carga del dataset hasta la generación de gráficos,  quedaron documentadas en el notebook adjunto en el repositorio, lo que garantiza transparencia y consistencia en el desarrollo del análisis.

### Conclusiones y hallazgos relevantes

Previo al proceso de graficación, se formularon cuatro hipotesis (H1, H2, H3 y H4) y dos preguntas (P1 y P2) que nos proporcionarán un marco conceptual para el análisis de los datos del Dataset.  Estas preguntas e hipótesis permiten definir qué relaciones explorar, qué patrones buscar y qué comparaciones son metodológicamente relevantes dentro del estudio.

**HIPOTESIS**

- **H1**: El uso intensivo de IAg baja la retención de conocimiento.

Para analizar esta hipótesis se realizó un diagrama de dispersión tomando las variables ``Weekly_GenAI_Hours `` y ``Skill_Retention_Score ``. Dada la información proporcionada por la gráfica, podemos concluir que se confirma, pero parcialmente. Si bien se observa una baja en la retención del conocimiento a medida que aumenta el uso semanal de la IAg, la tendencia es leve. No se percibe una relación fuerte entre ambas variables. 

- **H2**: A menor uso semanal de la IAg, es mayor la cantidad de horas dedicadas al estudio tradicional (sin IAg)

Para analizar esta hipótesis se realizó un diagrama de dispersión tomando las variables ``Weekly_GenAI_Hours `` y ``Traditional_Study_Hours ``. El comportamiento observado va en la dirección de lo planteado, sin embargo, el efecto es débil y no se percibe una tendencia marcada entre ambas variables. La alta dispersión de los datos sugiere que el uso de IAg no es el único ni el principal factor que determina las horas dedicadas al estudio tradicional.

- **H3**: Hay un aumento en el promedio de notas a mayor uso percibido de la IAg

La barra asociada a Post_Semester_GPA (Promedio) es consistentemente mayor que Pre_Semester_GPA (Promedio) en todos los niveles de uso de IAg. Esto último indica una mejora en GPA es independiente del nivel de uso de la IAg. Por este motivo, la hipotesis es falta, esto es que el nivel de uso de la herramienta no parece ser un factor diferenciador en el rendimiento académico medido por GPA.

- **H4**: Los usuarios con suscripción de pago utilizan herramientas de IA generativa durante más horas semanales que los usuarios sin suscripción.

De acuerdo a la información de gráfico, la hipotesis se acepta, ya que se identifica que hay un aumento en las horas de uso en usuarios que pagan suscripción en camparación a aquellos que no pagan. Estos resultados podrían explicarse porque los usuarios con suscripción cuentan con un acceso más amplio ( mayor tokens) con respecto a aquellos que usan la versión gratuita. Además, los usuarios suscritos suelen incorporar la IAg de manera más estable en su flujo de trabajo cotidiano, ya sea para tareas académicas, profesionales o creativas, lo que incrementa naturalmente el tiempo de uso semanal.

**PREGUNTAS**

- **P1**: ¿La distribución de las horas de uso semanal de herramientas de inteligencia artificial presenta simetría o evidencia un sesgo hacia alguno de sus extremos?

La distribución de horas semanales en el uso de IAg presenta una distribución claramente sesgada positivamente, por lo tanto, no es simétrica. La mayor concentración de los estudiantes se ubica en valores bajos ( 0 - 6 hrs), que de acuerdo con clasificación, el uso semanal de la IAg se encuentra en ocasional y regular. Se observa además un peak aislado en el extremo derecho, correspondiente al límite máximo del dataset.

Adicionalmente, la media es mayor que la mediana, lo que es un factor característico de un sesgo hacia la derecha. 


- **P2**: ¿Cuál es el uso principal más frecuente de la IA entre estudiantes de Ciencias?

Entre los estudiantes del área científica (STEM y Medical), el uso principal más frecuente de la IAg es Debugging/Troubleshooting(depuración y resolución de problemas), con una cantidad de cerca de 8500 estudiantes, superando ampliamente a los otros usos.  Summarizing/Reading ocupa el segundo lugar con una cantidad de estudiantes cerca de los 5000, dejando muy por detrás a las categorias Direct_Answer_Generation, Ideation y Copywriting/Drafting.

Este resultado es coherente de acuerdo al perfil de estudiantes analizados, ya que el área de ciencias suelen enfrentarse a problemas técnicos de programación, cálculos estadísticos y matemáticos y en la resolución de casos de estudios. Las tareas de depuración y resolución de problemas están alineados con las problemáticas que enfrentan los estudiantes de estas categóricas.


### Limitaciones

De acuerdo a la información declarada, este dataset  se generó sintéticamente para simular el comportamiento real de los estudiantes y los resultados académicos en el contexto de la adopción de la IA generativa. Por este motivo, los patrones y tendencias identificados no necesariamente reflejan el comportamiento real de un grupo de estudiantes universitarios que usan IAg. Además, las variables ``Perceived_AI_Dependency`` y ``Anxiety_Level_During_Exams``, entre otras, son percepciones personales, por lo que induce a un sesgo subjetivo en el análisis. A pesar de lo antes declarado, el dataset nos permite realizar hallazgos de caracter exploratorios/descriptivos, útil para una primera aproximación en un EDA.



*La previsualización del notebook ha generado problema durante el día sábado 30/05 en la mañana. Por este motivo, [adjunto el notebook renderizado en nbviewer](https://nbviewer.org/github/nico-pina/TP1-UP.IA/blob/main/EDA%20Dataset%20IA_%20NP.ipynb)
