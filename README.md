
# Expoandes

En Bogotá, no siempre es evidente si la capacidad del sistema de recolección y disposición de residuos funciona de manera adecuada a la demanda de los ciudadanos. Esto puede generar desequilibrios en la distribución de recursos, llevando a que localidades reciban mayor atención, mientras que otras quedan desatendidas. A su vez, esta situación genera focos de contaminación que impactan negativamente el medio ambiente y la salud pública. Estos focos suelen coincidir con sectores que presentan altos índices de inseguridad y deterioro urbano.

De acuerdo con Redacción Bogotá (2026), las quejas por el servicio de aseo en Bogotá aumentaron un 36 % entre 2024 y 2025, superando las 80.000 reclamaciones. Las localidades que tienen mayor cantidad de quejas son: Suba: 11.206 quejas, Kennedy: 9.120 quejas, Usaquén: 8.225 quejas, Engativá: 7.745 quejas. 

Estas localidades según Infobae “coinciden con cifras reveladas de la Secretaría de Seguridad, las localidades más inseguras de la capital son Suba (13.004 casos de hurto a personas y 6.239 de hurto de celulares), Kennedy (con 12.959 y 5.834, respectivamente), Engativá (12.298 y 5.708) y Chapinero (10.856 y 5.837).” (Infobae, 2023)

Partiendo de este contexto, nace la necesidad de analizar de manera cuantitativa la relación entre la demanda del servicio (PQRS y puntos críticos) y la capacidad instalada (número de contenedores), esto permitirá identificar desigualdades y aportar información objetiva del funcionamiento del sistema. Esta información a su vez será útil para futuras optimizaciones del servicio, además, permitirá implementar mejoras en el estado de las calles y la calidad de vida de los habitantes de Bogotá.



## Información
El proyecto utiliza exclusivamente datos abiertos provenientes de la Unidad Administrativa Especial de Servicios Públicos (UAESP), eliminando la necesidad de trabajo de campo directo.
Las principales variables son las siguientes:

A partir de estos datos que se explicaran a 
continuación, se podrá visualizar y comparar la proporcionalidad entre demanda y oferta, con el objetivo de evaluar la eficiencia del sistema.

Demanda:

 	• PQRS por localidad: quejas relacionadas con la gestión de residuos. (Estas con el fin de tener en cuenta la perspectiva de la ciudadanía frente al sistema)
    • Puntos críticos de residuos: zonas identificadas oficialmente con acumulación 	recurrente. (Tomando estos datos se reconocen las zonas más afectadas, para de esta manera lograr priorizarlas en futuras mejoras del sistema)


Capacidad:

    • Número de contenedores por localidad: infraestructura disponible para la disposición de residuos. (Esto es necesario para evaluar si los espacios son adecuados y tienen el volumen necesario que requieren los desechos de la ciudad)


Indicadores derivados:

Con el fin de evaluar la relación entre demanda y capacidad, se construyó el indicador: 

    • (PQRS ÷ número de contenedores) + (Puntos críticos ÷ número de contenedores) 
                    
Este índice permite medir la presión que enfrenta el sistema de aseo en cada localidad, combinando tanto la percepción ciudadana con la evidencia de acumulación de residuos en relación con la capacidad disponible. 
Para faciliar su interpretación, el indice se clasificó en cinco niveles: 
<div align="center">

| Rango     | Nivel      |
|-----------|-----------|
| 0 – 1     | Baja      |
| 1 – 15    | Media     |
| 15 – 30   | Alta      |
| 30 – 70   | Muy Alta  |
| > 70      | Crítica   |

</div>

Un valor alto del índice sugiere un posible desbalance, donde la demanda supera la capacidad disponible, mientras que valores bajos indican una mejor relación entre ambas.

## Procedimientos
Para el desarrollo del proyecto, se creará un repositorio en GitHub para almacenar y llevar registro de todas las modificaciones y avances que se realicen. Posteriormente se recopilarán 3 bases de datos de la Unidad Administrativa Especial de servicios públicos (UAESP), estos se obtendrán de los siguientes archivos de SIGAB correspondientes al año 2025 y se guardarán en una carpeta llamada Data_raw: 

   - [Sigab contenedores](https://datosabiertos.bogota.gov.co/dataset/sigab-diciembre-2025/resource/4e7137ff-d529-48bb-829f-a67fc9063450)
   - [Sigab puntos críticos](https://datosabiertos.bogota.gov.co/dataset/sigab-diciembre-2025/resource/d89bd5cc-9435-4cf8-8a3c-466e35209799)
   - [Sigab pqrs localidad](https://datosabiertos.bogota.gov.co/dataset/sigab-diciembre-2025/resource/955b4e78-fd2b-4283-826e-3c744ea06189)


Debido a que estos archivos están en formato de CSV, se pasaran al formato de tabla en Excel y se recopilaran en un mismo archivo, el cual se va a guardar en la carpeta Data_clean, para posteriormente realizar los siguientes pasos: 

a.	Limpieza de datos: 

    • Eliminación de variables irrelevantes
    • Filtrado por año 2025
    • Eliminación de datos que tengan la palabra "RE" en la variable NOVUBICACI en la base de datos de Contenedores, debido a que estos datos corresponden a contenedores no operativos (Retirados).
    • Depuración de datos vacios.
    
b. Transformación y creación de variables: 

    • Creación de la variable IDLOCALID en la base de datos de pqrs localidad 
    • Creación de una base de datos principal a partir de la integración de las 3 fuentes, utlizando IDLOCALID como unión
    • A partir de esa base, se crearon las variables agregadas de: Total PQRS, Total Puntos Críticos y Total Contenedores
    • Creación del índice antes especificado y su clasificación

    
c.	Visualización de datos: 

Se desarrollo un Dashboard interactivo en PowerBi compuesto por 4 partes: 

    • Panorama general: ¿Cómo esta el sistema de Aseo de Bogotá en el año 2025?
    • Relación demanda-capacidad: Análisis mediante gráfico de dispersión
    • Zonas críticas: Identificación de localidades con mayor desbalance
    • Exploración espacial: Mapas de contenedores y puntos críticos


## Potencial resultado

El resultado final del proyecto será un dashboard interactivo en PowerBI que permita visualizar la relación entre la demanda y la capacidad del sistema de aseo en Bogotá, identificar zonas críticas y proporcionar una herramienta de análisis que facilite la toma de decisiones futuras.

Adicionalmente, se entregará un repositorio en GitHub con todos los datos y documentos que respaldan el proyecto. Garantizando un trabajo transparente y reproducible.


## Documentos de respaldo
- [Datos Limpios](https://github.com/dayanacr2008-lab/expoandes/blob/main/Data%20Clean/Datos.xlsx)
- [Datos originales](https://github.com/dayanacr2008-lab/expoandes/tree/main/Data%20raw)


## Authors

- [@nataliarf23](https://github.com/nataliarf23)
- [@dayanacr2008-lab](https://github.com/dayanacr2008-lab)

