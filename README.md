# doc_db_2
Documentación de la actividad No.2 de la materia Visualización y Storytelling (MIAD)

## Base de datos original:

- **How old are you?:** Texto, 7 rangos de edades entre 18 y 65+, define la edad del encuestado.
- **What industry do you work in?:** Texto, describe la industria en la que trabaja el encuestado.
- **Job title:** Texto, indica el puesto que ocupa el encuestado.
- **If your job title needs additional context, please clarify here:** Texto, proporciona detalles adicionales sobre el trabajo del encuestado, si es necesario.
- **What is your annual salary? (You'll indicate the currency in a later question. If you are part-time or hourly, please enter an annualized equivalent -- what you would earn if you worked the job 40 hours a week, 52 weeks a year.):** Número, salario anual del encuestado, incluyendo equivalente para trabajos a tiempo parcial o por hora.
- **How much additional monetary compensation do you get, if any (for example, bonuses or overtime in an average year)? Please only include monetary compensation here, not the value of benefits:** Número, incluye bonificaciones u horas extras en un año promedio.
- **Please indicate the currency:** Texto, divisa en la que se paga el salario del encuestado.
- **If "Other," please indicate the currency here:** Texto, si la divisa no está en las opciones predeterminadas.
- **If your income needs additional context, please provide it here:** Texto, información adicional sobre los ingresos del encuestado, si es necesario.
- **What country do you work in?:** Texto, país donde trabaja el encuestado.
- **If you're in the U.S., what state do you work in?:** Texto, estado de trabajo si es en Estados Unidos.
- **What city do you work in?:** Texto, ciudad donde trabaja el encuestado.
- **How many years of professional work experience do you have overall?:** Texto, 8 rangos de años de experiencia general, define la experiencia general del encuestado.
- **How many years of professional work experience do you have in your field?:** Texto, 8 rangos de años de experiencia en el campo específico, define la experiencia en ese campo del encuestado.
- **What is your highest level of education completed?:** Texto, grado educativo más alto completado por el encuestado.
- **What is your gender?:** Texto, género con el que se identifica el encuestado.
- **What is your race? (Choose all that apply.):** Texto, raza o razas a las que pertenece el encuestado.

## Variables luego de modeladas

Las variables mantienen su tipo y contenido, salvo por tres excepciones: "What country do you work in?", "What city do you work in?", y "What industry do you work in?". En las dos primeras, se realiza una limpieza para corregir posibles errores en los nombres de países y ciudades. En la tercera, se ajustan las distintas formas de escribir las industrias para agruparlas correctamente.

Además, se crean tres nuevas columnas basadas en "What is your annual salary?" y "How much additional monetary compensation do you get, if any?". Dos de estas columnas contienen los valores en pesos colombianos (COP) convertidos, y la tercera representa el salario total anual, incluyendo compensaciones adicionales.

## Paso a paso actualización de datos y aplicación de modelado diseñado

Se construye un código en Python que realiza las siguientes acciones:

1. Lee un archivo de Excel llamado "salary_survey_2021.xlsx" ubicado en la carpeta '../data/raw/'.
2. Aplica una serie de transformaciones al conjunto de datos leído, como limpiar los nombres de las columnas, seleccionar un subconjunto de columnas específicas y renombrarlas para mayor claridad.
3. Realiza operaciones de limpieza y transformación en las columnas 'country', 'city', 'annual_salary', 'monetary_compensation' para estandarizar los valores y calcular equivalentes monetarios en una moneda específica (COP).
4. Calcula el salario anual y la compensación monetaria adicional en pesos colombianos (COP) utilizando tasas de conversión específicas para cada divisa.
5. Calcula el ingreso total anual en pesos colombianos sumando el salario anual y la compensación monetaria adicional.
6. Agrupa las industrias con un bajo número de ocurrencias bajo la categoría "(Otros)".
7. Filtra los datos para eliminar las filas donde la divisa no está especificada como "Other" y donde el salario anual sea igual a cero.

En resumen, este código carga datos de un archivo Excel, realiza varias transformaciones y limpiezas en los datos, calcula equivalentes monetarios en pesos colombianos, y finalmente filtra y procesa los datos para su posterior análisis en Tableau.
