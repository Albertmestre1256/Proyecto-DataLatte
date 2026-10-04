# ¿Por qué DataLatte dejó de crecer? Reescritura del proyecto final

Análisis de ventas 2023–2024 de **DataLatte S.A.**, una cadena ficticia de cafeterías, hecho en Python (pandas, matplotlib, seaborn).

## Aclaración importante

Este repositorio **no es el proyecto original**. DataLatte es el caso práctico del curso de introducción a la ciencia de datos de la **UCU**: los datos, la empresa, los personajes (Lucía y Agustín) y la consigna del proyecto final pertenecen al curso.

Lo que hay acá es una **reescritura personal** del proyecto final que entregué. La rehice para aprender cómo mejorarlo: volví a recorrer el análisis con más cuidado, verifiqué cada cifra y repensé los gráficos. No reemplaza ni representa la entrega original, y no tiene fines comerciales.

> El notebook y el informe se redactaron con asistencia de IA (Claude) como herramienta de aprendizaje y verificación.

## La consigna

> La empresa dejó de crecer en ventas y necesita entender por qué. Usar los datos del curso para hacerse preguntas, encontrar pistas, sacar conclusiones, mostrar resultados con gráficos, proponer 2 o 3 acciones concretas y cerrar con un aprendizaje.

## Contenido

| Archivo | Qué es |
|---|---|
| `Proyecto_Final_DataLatte.ipynb` | Notebook con todo el análisis, los 7 gráficos y una celda final que verifica las cifras del informe |
| `Proyecto_Final_DataLatte.docx` | Informe escrito con gráficos, conclusiones, recomendaciones y aprendizaje |
| `ventas_depuradas.csv` | Dataset depurado del curso (ver nota sobre los datos) |

## Cómo ejecutarlo

1. Abrir el notebook en [Google Colab](https://colab.research.google.com) (Archivo → Subir notebook) o en Jupyter.
2. Si usás Colab, ejecutar todo con *Entorno de ejecución → Ejecutar todo*.
3. El notebook busca `ventas_depuradas.csv` en la misma carpeta y, si no lo encuentra, lo descarga del enlace del curso.

Requisitos: `pandas`, `numpy`, `matplotlib`, `seaborn`.

## Qué encontré

- **El estancamiento es un cambio de tendencia.** 2024 facturó \$11,46 M contra \$11,34 M en 2023 (+1,0 %), pero 2023 fue de crecimiento sostenido y 2024 de caída: en diciembre de 2024 las ventas estaban un 32 % por debajo del pico de enero.
- **El problema está en el ticket, no en la cantidad.** Se hacen unas 1.660 ventas por mes en los dos años y el 98 % de los clientes compra en ambos. Lo que baja es cuánto deja cada venta.
- **Online Global tuvo un quiebre en febrero de 2024.** Su ticket promedio cayó de \$553 a \$217 de un mes a otro, en todos los productos y ciudades por igual. Esa tienda perdió casi la mitad de su facturación anual (≈ \$1,5 M); sin esa caída, la empresa habría crecido cerca de un 15 %.
- **En el resto de las tiendas la caída es gradual y acompaña a la inversión en marketing.** La correlación mensual con las ventas es de 0,97 (venta por venta es de apenas 0,29).
- **Productos, ciudades y edades se mueven todos igual**, así que ninguno explica el problema por sí solo.

## Recomendaciones

1. Investigar qué pasó en Online Global en febrero de 2024 (precios, promoción, moneda o error de carga de datos).
2. Recuperar la inversión en marketing de forma medida, probando primero en una tienda.
3. Trabajar sobre el ticket aprovechando la fidelidad de los clientes (combos, venta complementaria, beneficios) y seguirlo por tienda en un tablero mensual.

## Qué practiqué en esta versión

- Descomponer el problema: **monto = cantidad de ventas × ticket promedio**, para saber qué parte explica la caída.
- Mirar los datos **por mes y por segmento** antes de confiar en el total anual, que escondía la historia.
- Entender que el **nivel de agrupación cambia la lectura**: la correlación entre marketing y ventas es 0,29 venta por venta y 0,97 mes a mes.
- Hacer gráficos que respondan una pregunta: sin doble eje Y (dos paneles con el mismo eje de tiempo), con anotaciones solo donde aportan y una paleta consistente.
- **Verificar cada cifra** con una celda que recalcula los números del informe, y chequear que las conclusiones no dependan de la imputación con la mediana hecha en la limpieza.

## Limitaciones

- La correlación entre marketing y ventas no prueba causalidad.
- 1.191 montos fueron completados con la mediana en la limpieza del curso; las conclusiones se mantienen al excluirlos, pero conviene tenerlo presente.
- Quedan 65 registros con edades mayores a 100 años sin revisar.
- La causa del quiebre de Online Global no se puede determinar con estos datos: habría que confirmarla con las áreas de Ventas o Sistemas.

## Sobre los datos

El dataset y el caso pertenecen al curso. Antes de publicar el repositorio conviene confirmar si se pueden redistribuir; si no, se puede quitar `ventas_depuradas.csv` del repo y dejar que el notebook lo descargue del enlace del curso.

## Autor

**Albert**: Licenciado en Historia (Udelar), Montevideo, Uruguay.
