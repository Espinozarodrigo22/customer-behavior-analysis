# Análisis de Clientes — Limpieza y Preparación de Datos

## Descripción

Se realizó el proceso de exploración, limpieza, validación y preparación de un dataset empresarial de clientes con el objetivo de obtener información confiable para análisis de comportamiento, segmentación y toma de decisiones estratégicas.

El proyecto busca responder preguntas de negocio relacionadas con ingresos, gasto de clientes, marketing, retención y riesgo financiero.

Actualmente el proyecto se encuentra en fase de análisis y preparación de datos, mientras que el dashboard interactivo en Power BI se encuentra en desarrollo.

---

## Dataset

El dataset contiene aproximadamente:

* 98.500 registros
* 24 variables

Entre las variables analizadas se encuentran:

* edad del cliente
* ingreso anual
* gasto anual
* segmento de cliente
* ciudad
* número de órdenes
* ticket promedio
* puntos de lealtad
* tasa de apertura de emails

---

## Exploración inicial del dataset

Durante la exploración inicial se observó que:

* La tabla contiene 98.500 registros y 24 variables
* No se detectaron filas completamente duplicadas
* Varias columnas presentan valores repetidos esperables en variables categóricas
* Se detectaron valores nulos en algunas variables clave como:

city
annual_income
email_open_rate
credit_score

A partir de esta exploración se definieron distintas estrategias de limpieza y validación de datos.

---

## Limpieza de datos

### customer_id

#### Problema detectado

Se identificaron registros duplicados de clientes donde todas las variables coincidían excepto el gasto anual (annual_spend).

#### Decisión

En lugar de eliminar arbitrariamente los registros duplicados, se decidió:

* calcular el promedio del gasto anual para cada cliente duplicado
* reemplazar el valor original por el promedio
* conservar un único registro por cliente

#### Resultado

Se eliminó la duplicidad de clientes manteniendo un valor representativo del gasto anual.

---

### age

#### Problema detectado

Se detectaron edades irreales dentro del dataset, incluyendo:

* edades menores a 10 años
* edades superiores a 119 años

#### Decisión

Se desarrolló un proceso de imputación basado en:

* ingreso anual promedio
* grupo de edad
* género
* ciudad

Cuando el ingreso no estaba disponible, se utilizó una segunda estrategia basada en la distribución de edades dentro de grupos similares de clientes.

#### Resultado

Se corrigieron los valores atípicos manteniendo coherencia con los patrones del dataset.

---

### last_purchase_days

#### Problema detectado

Se detectaron valores negativos en la variable que representa los días transcurridos desde la última compra.

#### Decisión

Los valores negativos se transformaron utilizando su valor absoluto, ya que conceptualmente esta variable solo puede representar valores positivos.

#### Resultado

La variable quedó estandarizada para su análisis en comportamiento de compra.

---

### loyalty_points

Se detectaron clientes con valores muy bajos de puntos de fidelidad.

Sin embargo, estos casos representan aproximadamente 7,5 % del dataset, por lo que se interpretan como parte del comportamiento normal del programa de fidelización y no como errores de datos.

---

### city

Los valores faltantes en la variable city representan una proporción pequeña del dataset.

Para evitar introducir sesgos mediante imputación arbitraria, se decidió reemplazar los valores faltantes por la categoría:

no_informado

Esto permite conservar los registros sin alterar el comportamiento real de los datos.

---

### email_open_rate

Los valores faltantes se imputaron utilizando el promedio de apertura de emails dentro de grupos definidos por:

* grupo de edad
* ciudad
* segmento

Esto permite mantener coherencia con el comportamiento típico de cada grupo de clientes.

---

### annual_spend

Se detectaron valores inconsistentes como:

* valores negativos
* valores iguales a cero
* valores extremadamente altos

Para resolver este problema se reconstruyó la variable utilizando dos variables confiables del dataset:

annual_spend = total_orders * avg_ticket

Esto permite obtener una estimación consistente del gasto anual del cliente.

---

## Preguntas de negocio

El proyecto busca responder preguntas relacionadas con:

### Clientes y negocio

* ¿Qué segmento genera mayor ingreso total?
* ¿Qué variables predicen mayor gasto anual?
* ¿Existe relación entre edad y gasto?

### Marketing

* ¿Las campañas realmente aumentan las compras?
* ¿Existe relación entre campañas y gasto?

### Riesgo financiero

* ¿Los clientes con mayor ingreso gastan más?
* ¿Los retrasos de pago afectan el gasto?

### Retención

* ¿Los puntos de fidelidad influyen en las compras?

### Estrategia

* ¿Qué perfil de cliente debería recibir promociones premium?

---

## Herramientas utilizadas

* Python
* Pandas
* Jupyter Notebook
* Power BI (dashboard en desarrollo)

---

## Estado del proyecto

✔ Exploración de datos
✔ Limpieza y preparación del dataset
✔ Definición de preguntas de negocio
🔄 Desarrollo de dashboard en Power BI

---

## Autor

Rodrigo Espinoza
Analista de Datos
