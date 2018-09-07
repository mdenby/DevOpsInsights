---

copyright:
  years: 2016, 2018
lastupdated: "2018-8-2"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Developer Insights
{: #gettingstarted}

{{site.data.keyword.DRA_full}} Developer Insights proporciona una forma averiguar el riesgo en el desarrollo de un proyecto. Permite identificar los archivos más propensos a contener errores y obtener una vista de conformidad del proyecto con relación a los procedimientos de DevOps.
{:shortdesc}

Después de abrir {{site.data.keyword.DRA_short}} desde la cadena de herramientas, pulse **Developer Insights**. Desde allí, puede seleccionar una categoría analítica para profundizar en el codebase del proyecto. Lo que indica cada conjunto de datos puede variar de equipo a equipo. Podrá profundizar en cada visualización para obtener ayuda e información. 

## Categorías de datos
Los datos que utiliza {{site.data.keyword.DRA_short}} para llenar sus paneles de control se extraen automáticamente desde el repositorio de control de código fuente del equipo. Podrá obtener más información sobre lo que significan los datos y cómo se aplican a su proyecto pulsando **Información** o **Instrucciones** en cualquier gráfico.

### Prácticas recomendadas para los desarrolladores

Developer Insights proporciona una serie de diagramas que evalúan su proyecto con relación a las prácticas recomendadas para los desarrolladores y DevOps. Utilice esta categoría para obtener una visión de alto nivel de la madurez, salud y eficacia de su proyecto. 

### Problemas

La categoría de Problemas visualiza todos los problemas de seguimiento de trabajo del equipo en un único lugar. Los problemas se agrupan automáticamente según el tipo, la prioridad y las etiquetas, y se pueden mostrar a lo largo del tiempo. 

Estas agrupaciones de problemas pueden tener un significado diferente para cada equipo. Un equipo podría querer saber si se han cerrado la mayoría de los elementos etiquetados para un release concreto, mientras que otro equipo podría no querer etiquetar releases y, en su lugar, trabajar de acuerdo a la prioridad de los problemas abiertos.  

### Confirmaciones

Las confirmaciones indican el trabajo que los miembros del equipo aportan al codebase. Examine los datos de las confirmaciones para entender dónde se ha realizado históricamente el esfuerzo y cómo equilibrar mejor las cargas de trabajo de los miembros del equipo. 

### Solicitudes de extracción

Las solicitudes de extracción muestran el código que los miembros del equipo incorporan a otra rama.  Sumérjase en los datos de las solicitudes de extracción para conocer los riesgos asociados a añadir código nuevo a una rama de código limpia.

### Archivos

La categoría de Archivos muestra cuáles de los archivos del proyecto son los más activos. Los cambios en el número de líneas, las confirmaciones, los autores o los defectos indican dónde es más activo el equipo. Además, puede ver dónde residen los riesgos de los archivos revisando el separador de propensión a errores de los archivos.

Habitualmente, se debe intentar reducir el número de personas que trabajan en un archivo y la frecuencia de cambios en los archivos. Este objetivo puede ser imposible con determinados archivos, como por ejemplo los archivos de configuración comunes. Sin embargo, muchos desarrolladores realizando muchos cambios en el mismo archivo al mismo tiempo puede dar lugar a problemas. 

DevOps Insights omite los archivos con estas extensiones:
* .bin
* .cdr
* .jpeg
* .jpg
* .json
* .markdown
* .md
* .png
* .pyc
* .svg
* .text
* .yaml
* .yml
{: tip}
