# ¿Cuál es la influencia de la tasa de interés de referencia en la dinámica de la inflación en el corto plazo en el Perú?

## *Descripción:*

### Primera presentación

<div align="justify">
  
La elección de las variables  se centra en **capturar los principales canales de transmisión de la política monetaria hacia la inflación en el corto plazo**. La tasa de referencia es el instrumento central del BCRP, y su influencia se transmite a través de la tasa interbancaria y las tasas de los instrumentos de mercado abierto, como los CD-BCRP. Al incluir tanto las tasas de interés como los saldos de los instrumentos (repos de valores, CD-BCRP, depósitos públicos y depósitos overnight), es posible observar cómo el banco central regula simultáneamente el costo y la disponibilidad de liquidez en el sistema financiero, mecanismos fundamentales para explicar la dinámica inflacionaria.

Sin embargo, existen limitaciones relevantes en la base de datos disponible. En particular, **no ha sido posible incluir las tasas de colocación de repos**, ya que estas no se publican como series mensuales en el API del BCRP, sino que aparecen únicamente en notas informativas tras cada subasta. De igual modo, los repos GART y Reactiva, que fueron instrumentos excepcionales durante la pandemia, tampoco se encuentran como series separadas en el API. Esto restringe la posibilidad de capturar con precisión el canal de transmisión durante el contexto extraordinario del COVID-19, donde la liquidez inyectada a través de estas operaciones tuvo un papel relevante.

A pesar de estas limitaciones, el conjunto de variables seleccionado permite un análisis sólido y representativo del funcionamiento de la política monetaria en el Perú. Los saldos y tasas de los instrumentos tradicionales (CD-BCRP, repos de valores, depósitos) constituyen la base del marco operativo del BCRP y reflejan adecuadamente la dinámica de liquidez y de precios en el mercado monetario. Si bien no se logra aislar el impacto de instrumentos extraordinarios como GART o Reactiva, el enfoque adoptado sigue siendo pertinente para responder la pregunta de investigación, ya que captura los mecanismos regulares de transmisión de la tasa de referencia hacia la inflación en el corto plazo.
</div>

### Segunda presentación

Se analiza el efecto de la **tasa de interés de referencia** sobre la **inflación mensual subyacente** del Perú (serie PN01278PM) utilizando datos del Banco Central de Reserva del Perú (BCRP) entre 2013 y 2025. En esta segunda parte se eligió la inflación subyacente en lugar del IPC general porque es menos volátil y refleja mejor la tendencia de fondo de los precios. Así, permite analizar con mayor precisión el efecto de la tasa de referencia sobre la inflación controlada por la política monetaria.


El objetivo principal es construir modelos supervisados de predicción a un mes adelante, donde la variable dependiente es la inflación subyacente futura, y la principal variable explicativa es la tasa de referencia (PD04722MM) junto con sus rezagos y otras variables financieras transformadas.

Se verificó la estacionariedad de las series mediante las pruebas ADF y KPSS, concluyendo que ambas variables presentan comportamientos cercanos a la estacionariedad. Posteriormente, se generaron rezagos de la tasa de referencia y se construyó un conjunto de datos para modelado, preservando el orden temporal. Se aplicaron tres modelos predictivos: Regresión Lineal, Ridge y Random Forest, evaluados mediante validación cruzada temporal (TimeSeriesSplit) y un conjunto de prueba (hold-out del 25%).

Los resultados muestran que los modelos lineales (especialmente Ridge) obtienen los mejores desempeños, con un error cuadrático medio (MSE) cercano a 0.035 y un R² en torno a 0.24, mientras que el modelo no lineal (Random Forest) presentó sobreajuste. Estos hallazgos sugieren que la relación entre la tasa de interés de referencia y la inflación subyacente es predominantemente lineal y estable en el corto plazo, confirmando que los métodos lineales son adecuados para capturar la dinámica entre ambas variables.

