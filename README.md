# Proyecto_Final_RappiPlus_Data_Analyst
Proyecto Final. RappiPlus: De datos a decisiones de negocio

# Proyecto 11: Dashboard de análisis comercial de la plataforma de rappi | RappiPlus: de datos a decisiones de negocio


## 📌 Descripción del proyecto
En este proyecto desarrollé un análisis integral del desempeño de **RappiPlus**, un servicio de suscripción dentro del ecosistema de Rappi diseñado para aumentar la frecuencia de compra y el valor generado por usuario. El equipo de negocio necesitaba comprender si el servicio estaba cumpliendo sus objetivos comerciales y de producto. Para ello, transformé datos de pedidos, catálogo, marketing, comportamiento de usuarios y experimentación A/B en hallazgos accionables.

El análisis se enfocó en responder las siguientes preguntas:

- ¿Podemos confiar en los datos?
- ¿El negocio está generando ganancias?
- ¿En qué parte del proceso de compra se pierden los usuarios?
- ¿Los usuarios regresan después de registrarse?
- ¿La nueva interfaz de checkout produjo un impacto real en la conversión?
- ¿Cómo se pueden comunicar estos resultados mediante un dashboard ejecutivo?


## 🎯 Objetivo del proyecto

El objetivo fue evaluar el desempeño comercial, operativo y de producto de RappiPlus para identificar oportunidades de mejora en rentabilidad, conversión, retención y experiencia de usuario.

Durante el proyecto logré:

- Preparar y validar las fuentes de datos utilizadas en el análisis.
- Detectar y corregir problemas de calidad, duplicados, valores nulos e inconsistencias.
- Calcular métricas de ingresos, costos, gasto en marketing, profit y ticket promedio.
- Identificar productos, categorías y pedidos con impacto negativo en la rentabilidad.
- Construir un funnel de conversión con SQL para identificar puntos de abandono.
- Analizar la retención de usuarios mediante cohortes semanales.
- Evaluar una modificación de interfaz mediante un experimento A/B.
- Diseñar un dashboard interactivo en Power BI para comunicar resultados a stakeholders.



## 🗺️ Flujo general del análisis

| Etapa | Pregunta de negocio | Resultado |
|---|---|---|
| 1. Calidad de datos | ¿Podemos confiar en los datos? | Datasets limpios y auditables |
| 2. Rentabilidad | ¿El negocio genera ganancias? | KPIs de revenue, costo, marketing y profit |
| 3. Funnel | ¿Dónde se pierden los usuarios? | Etapas de conversión y mayor abandono |
| 4. Cohortes | ¿Los usuarios regresan? | Retención semanal por cohorte |
| 5. Experimento A/B | ¿Los cambios funcionan? | Decisión estadística y recomendación |
| 6. Dashboard | ¿Cómo comunicar los resultados? | Dashboard ejecutivo e interactivo |


---

## 🛠️ Herramientas utilizadas

| Herramienta | Uso dentro del proyecto |
|---|---|
| Python | Limpieza, transformación, análisis exploratorio y prueba estadística |
| Pandas | Manipulación, validación y estructuración de datasets |
| NumPy | Tratamiento de datos y operaciones numéricas |
| Matplotlib y Seaborn | Visualización exploratoria de datos |
| SQL | Funnel de conversión y análisis de cohortes |
| Statsmodels | Z-test de proporciones para experimento A/B |
| Power BI | Modelado, DAX, dashboard y comunicación de insights |
| Jupyter Notebook | Documentación y ejecución reproducible del análisis |

---

# 📂 Datos utilizados

El proyecto integró datos de pedidos, catálogo de productos, inversión en marketing, eventos de usuario, actividad posterior al registro y un experimento A/B de checkout.

## 1. Pedidos — `rappiplus_orders_raw.csv`

Cada fila representa un pedido realizado dentro de la plataforma.

| Columna | Tipo | Descripción |
|---|---|---|
| `id_pedido` | Categórica | Identificador único del pedido |
| `id_usuario` | Categórica | Identificador del usuario |
| `fecha_hora_pedido` | Fecha | Fecha en que se realizó el pedido |
| `pais` | Categórica | País desde donde se realizó el pedido |
| `dispositivo` | Categórica | Dispositivo utilizado |
| `fuente_referencia` | Categórica | Canal de adquisición del usuario |
| `nombre_producto` | Categórica | Producto comprado |
| `categoria_producto` | Categórica | Categoría del producto |
| `cantidad` | Numérica | Cantidad de productos adquiridos |
| `precio_unitario` | Numérica | Precio por unidad |
| `monto_descuento` | Numérica | Descuento aplicado al pedido |
| `monto_total` | Numérica | Monto final pagado por el pedido |

## 2. Catálogo — `rappiplus_catalog.csv`

Cada fila representa un producto disponible en la plataforma.

| Columna | Tipo | Descripción |
|---|---|---|
| `nombre_producto` | Categórica | Nombre del producto |
| `categoria_producto` | Categórica | Categoría a la que pertenece |
| `costo_unitario` | Numérica | Costo por unidad para el negocio |
| `proveedor` | Categórica | Empresa proveedora |

## 3. Marketing — `rappiplus_marketing_spend.csv`

Cada fila representa una inversión de marketing realizada por país y canal.

| Columna | Tipo | Descripción |
|---|---|---|
| `fecha` | Fecha | Fecha de ejecución de la inversión |
| `pais` | Categórica | País donde se realizó la campaña |
| `id_campaña` | Categórica | Identificador de la campaña |
| `canal` | Categórica | Canal de marketing utilizado |
| `gasto` | Numérica | Monto invertido en marketing |

## 4. Eventos — tabla SQL `events`

Esta tabla registra las interacciones de los usuarios dentro de la plataforma y fue utilizada para construir el funnel de conversión.

| Columna | Tipo | Descripción |
|---|---|---|
| `id_usuario` | Categórica | Identificador único del usuario |
| `id_sesion` | Categórica | Identificador único de la sesión |
| `nombre_evento` | Categórica | Evento realizado por el usuario |
| `timestamp_evento` | Fecha | Momento en que ocurrió el evento |
| `pais` | Categórica | País del usuario |
| `dispositivo` | Categórica | Dispositivo utilizado |
| `fuente_referencia` | Categórica | Canal de adquisición |
| `categoria_producto` | Categórica | Categoría asociada al evento |

## 5. Usuarios y actividad — tablas SQL

Estas tablas fueron utilizadas para analizar el comportamiento de los usuarios después de su registro.

### Tabla `users`

| Columna | Tipo | Descripción |
|---|---|---|
| `id_usuario` | Categórica | Identificador único del usuario |
| `fecha_registro` | Fecha | Fecha de registro |
| `pais` | Categórica | País de origen |
| `dispositivo` | Categórica | Dispositivo de registro |
| `tipo_plan` | Categórica | Tipo de plan contratado |

### Tabla `user_activity`

| Columna | Tipo | Descripción |
|---|---|---|
| `id_usuario` | Categórica | Identificador único del usuario |
| `fecha_actividad` | Fecha | Fecha en que se registró actividad |
| `dias_despues_registro` | Numérica | Días transcurridos desde el registro |
| `activo` | Numérica | Estado de actividad: `1` activo, `0` inactivo |

## 6. Experimento A/B — `experiment_checkout_ui.csv`

Cada fila representa la participación de un usuario en un experimento de interfaz de checkout.

| Columna | Tipo | Descripción |
|---|---|---|
| `id_usuario` | Categórica | Identificador único del usuario |
| `variante` | Categórica | Variante asignada: control o tratamiento |
| `convirtio` | Numérica | Conversión: `1` convirtió, `0` no convirtió |
| `dispositivo` | Categórica | Dispositivo utilizado |
| `pais` | Categórica | País del usuario |
| `duracion_sesion` | Numérica | Duración de la sesión en segundos |
| `timestamp` | Fecha | Fecha de interacción |



# 🔎 Desarrollo del análisis

## 1. Preparación y calidad de datos

Inicialmente evalué la calidad de los tres datasets principales: pedidos, catálogo y marketing. La revisión incluyó tipos de datos, valores nulos, registros duplicados, variables categóricas, rangos numéricos y consistencia entre columnas relacionadas.

En el dataset original de pedidos identifiqué:

| Indicador | Resultado |
|---|---:|
| Registros iniciales de pedidos | 25.100 |
| Pedidos únicos originales | 25.000 |
| Registros duplicados detectados | 100 |
| Registros completos finales | 24.600 |
| Registros separados para auditoría | 400 |

Las principales acciones realizadas fueron:

- Conversión de las variables de fecha al formato adecuado.
- Validación de valores numéricos en cantidad, precio, descuentos y montos totales.
- Identificación de valores negativos o inválidos en variables numéricas.
- Verificación de la fórmula `cantidad × precio_unitario − monto_descuento`.
- Eliminación de registros duplicados mediante el identificador `id_pedido`.
- Estandarización de los nombres de países: Argentina, Colombia y México.
- Estandarización de la categoría Electrónica.
- Recuperación de categorías faltantes utilizando la información del catálogo cuando fue posible.
- Separación de registros incompletos para auditoría, evitando imputar valores que no podían reconstruirse de forma confiable.

Como resultado del proceso de limpieza, generé los siguientes archivos:

```
orders_clean.csv
catalog_clean.csv
marketing_clean.csv
orders_auditable_nulos.csv
marketing_auditable_nulos.csv
```


## 2. Análisis de rentabilidad

Después de limpiar los datos, relacioné la tabla de pedidos con el catálogo mediante la variable `nombre_producto`. Esto permitió agregar el costo unitario de cada producto y calcular el costo total asociado a cada pedido.

Las métricas principales utilizadas fueron:

| KPI | Fórmula |
|---|---|
| Revenue total | `SUM(monto_total)` |
| Costo de productos | `cantidad × costo_unitario` |
| Gasto total en marketing | `SUM(gasto)` |
| Profit total | `Revenue − costos de productos − gasto de marketing` |
| Ticket promedio | `Revenue total / cantidad de pedidos` |
| Promedio de productos por pedido | `PROMEDIO(cantidad)` |
| Margen de ganancia | `Profit / Revenue` |

El análisis permitió comparar ingresos, costos y ganancias por:

- Categoría de producto.
- Producto.
- País.
- Canal de adquisición.
- Dispositivo.
- Periodo de tiempo.

Uno de los hallazgos más relevantes fue que algunos pedidos de alto volumen, especialmente asociados a productos de electrónica, generaban ingresos altos pero presentaban pérdidas debido a que el costo de los productos superaba el ingreso recibido.

## 3. Funnel de conversión con SQL

Para entender el comportamiento de los usuarios dentro de la plataforma, construí un funnel de conversión a partir de los eventos registrados en la tabla `events`.

El análisis permitió:

- Identificar el número de usuarios únicos por etapa.
- Calcular la conversión entre etapas consecutivas.
- Detectar el punto con mayor abandono.
- Analizar oportunidades de mejora según país, dispositivo, canal o categoría.

El principal punto de abandono se encontró durante el proceso de checkout, específicamente en el momento en que el usuario debe registrar o confirmar su método de pago.

Este comportamiento puede estar relacionado con factores como:

- Falta de claridad en el precio final.
- Tarifas adicionales visibles al final del proceso.
- Fricción en el formulario de pago.
- Métodos de pago insuficientes.
- Dudas sobre seguridad o confianza al completar la compra.

## 4. Análisis de retención por cohortes

Para evaluar si los usuarios regresaban a la plataforma, construí cohortes semanales según la fecha de registro y medí su actividad durante las primeras cuatro semanas posteriores.

El proceso consistió en:

1. Agrupar a cada usuario en una cohorte según su semana de registro.
2. Relacionar la cohorte con la tabla de actividad de usuarios.
3. Calcular usuarios activos durante las semanas 1, 2, 3 y 4.
4. Obtener porcentajes de retención para cada cohorte.

Los resultados mostraron un patrón de retención cercano al **40%** durante las primeras semanas.

| Métrica | Interpretación |
|---|---|
| Retención aproximada | Cerca de 40% |
| Abandono aproximado | Cerca de 60% |
| Periodo analizado | Primeras cuatro semanas después del registro |
| Oportunidad principal | Mejorar la activación temprana y la recompra |

Este resultado indica que una proporción importante de usuarios no vuelve a estar activa después del registro. Por ello, se recomienda investigar qué beneficios, mensajes, descuentos o experiencias pueden incrementar la recurrencia temprana.

## 5. Evaluación del experimento A/B

Analicé un experimento A/B para determinar si una nueva interfaz de checkout aumentaba la tasa de conversión.

### Hipótesis estadísticas

- **Hipótesis nula \(H₀\):** no existe una diferencia estadísticamente significativa entre la tasa de conversión de la interfaz de control y la interfaz de tratamiento.
- **Hipótesis alternativa \(H₁\):** existe una diferencia estadísticamente significativa entre ambas tasas de conversión.

Se aplicó un **Z-test de dos proporciones** con un nivel de significancia de 5%.

### Resultados del experimento

| Métrica | Grupo control | Grupo tratamiento |
|---|---:|---:|
| Usuarios convertidos | 779 | 820 |
| Usuarios totales | 4.965 | 5.035 |
| Tasa de conversión | 15,69% | 16,29% |
| Diferencia de conversión | — | 0,60 puntos porcentuales |

| Resultado estadístico | Valor |
|---|---:|
| Estadístico Z | -0,81328 |
| Valor p | 0,41606 |
| Nivel de significancia | 0,05 |
| Decisión | No se rechaza la hipótesis nula |

Aunque la interfaz de tratamiento tuvo una tasa de conversión ligeramente mayor, la diferencia observada no fue estadísticamente significativa.

Por esta razón, no existe evidencia suficiente para afirmar que la nueva interfaz haya producido una mejora real en la conversión. La recomendación es diseñar y probar nuevas variantes antes de escalar este cambio a todos los usuarios.


# 📈 Dashboard en Power BI

Construí un dashboard interactivo en Power BI utilizando los archivos limpios generados durante la etapa de preparación de datos. El modelo incluyó relaciones entre pedidos, catálogo, marketing y una tabla calendario para habilitar análisis temporal, métricas acumuladas y comparaciones entre periodos.

## Dashboard 1: Desempeño general del negocio

Esta página permite visualizar una perspectiva ejecutiva del desempeño de RappiPlus. Incluye:

- Revenue total.
- Costo total.
- Profit total.
- Ticket promedio.
- Gasto total en marketing.
- Promedio de productos por pedido.
- Revenue, costo y margen por categoría.
- Evolución mensual del profit por país.
- Ingresos acumulados YTD.
- Filtros por mes, país, fuente de referencia y dispositivo.


## Dashboard 2: Vista detallada y drill-through

Esta página permite profundizar en el comportamiento de los productos y pedidos específicos. Incluye:

- Porcentaje de ganancias.
- Porcentaje de costos.
- Precio más bajo y precio más alto.
- Ingresos acumulados YTD.
- Comparación de revenue, cantidad y margen por producto.
- Tabla detallada de pedidos.
- Formato condicional para identificar profit negativo.
- Matriz de cohortes de ingresos.
- Drill-through desde categorías o productos hacia pedidos individuales.


# 💡 Hallazgos principales

- Los datos pudieron utilizarse para análisis después de aplicar un proceso de limpieza, estandarización y auditoría de registros incompletos.
- El negocio presenta rentabilidad general positiva, pero existen pedidos y productos que pueden generar pérdidas.
- La categoría de electrónica concentra una parte importante de la facturación.
- `Laptop-Gaming-16GB` presenta un alto impacto en los ingresos, pero algunos pedidos asociados muestran profit negativo.
- El principal abandono de usuarios ocurre durante la etapa de checkout relacionada con el método de pago.
- La retención se mantiene cerca del 40% durante las primeras cuatro semanas después del registro.
- La nueva interfaz de checkout no mostró una mejora estadísticamente significativa en la conversión.
- Los ingresos acumulados muestran crecimiento, aunque es necesario monitorear los costos y subsidios para proteger la rentabilidad a mediano plazo.



# ✅ Recomendaciones de negocio

- Revisar las reglas de precio, descuento y beneficios asociados a productos de alto costo, especialmente en electrónica.
- Implementar alertas para identificar pedidos con margen negativo antes de que afecten la rentabilidad.
- Analizar los pedidos con cantidades inusualmente altas para validar si corresponden al comportamiento esperado de un marketplace minorista.
- Investigar la fricción en checkout mediante pruebas de usabilidad, análisis de errores y encuestas a usuarios.
- Mostrar de forma más clara los costos finales, tarifas y métodos de pago antes de la última etapa de compra.
- Implementar estrategias de activación temprana para mejorar la retención durante las primeras cuatro semanas.
- Diseñar nuevas variantes de interfaz y validarlas mediante experimentos A/B antes de implementar cambios globales.
- Mantener los archivos de auditoría para conservar la trazabilidad de datos incompletos y facilitar correcciones futuras.



# 🚀 Cómo ejecutar el proyecto

## Requisitos

Instala las librerías necesarias:

```bash
pip install pandas numpy matplotlib seaborn sqlalchemy psycopg2-binary statsmodels
```

## Pasos de ejecución

1. Clona este repositorio:

```bash
git clone [URL_DEL_REPOSITORIO]
```

2. Abre el archivo Jupyter Notebook ubicado en:

```text
notebooks/S12-Estudiante_Proyecto_Final.ipynb
```

3. Ejecuta las secciones de carga, validación y limpieza de datos.

4. Verifica que se generen los archivos limpios dentro de la carpeta `data/processed/`.

5. Configura las credenciales de conexión a la base de datos para ejecutar las consultas SQL relacionadas con funnel y cohortes.

6. Abre el archivo de Power BI:

```text
dashboard/RappiPlus_Dashboard.pbix
```

7. Actualiza las rutas de los archivos CSV en Power BI si es necesario.

---



**[Tu nombre completo]**

Proyecto final desarrollado como parte de la formación en análisis de datos.
