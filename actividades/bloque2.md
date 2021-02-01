# ggplot2

## Gramática de gráficos

1. ¿Cuáles son los componentes básicos de la gramática que tienen que estar en todos los gráficos? ¿Cuáles son opcionales?

## Aesthetics


1. Realizar un gráfico de puntos de las variables `mass`, en el eje x, y `height`, en el eje y. Además el color de los puntos tiene que representar la variable `sex`

2. Repetir el gráfico anterior pero solo con las filas del dataframe `starwars` cuyo valor de `mass` es menor que 500.

## geoms

1. Representa la evolución temporal de la columna población (`pop`) contenida en el dataframe `economics` (incluído en ggplot2)

2. Representa en una misma gráfica la evolución temporal de la columna población (`pop`) en negro y la evolución temporal de la columna de desempleo (`unemploy`) en rojo. Utiliza ajustes globales de ggplot siempre que sea posible.

## Transformaciones estadísticas

1. Consultar la ayuda para ver la diferencia entre `geom_col` y `geom_bar`

2. Realizar un gráfico de barras con el número de filas para cada uno de los valores de la columna `sex` en el dataframe `starwars` (incluido en la librería dplyr)

3. Crear un histograma de la variable `carat` del dataframe `diamonds` (incluído en la librería ggplot2)

4. ¿Qué significa el aviso que devuelve la función?. Probar con varios valores del parámetro `bins`

## Ajustes de posición

1. Realizar un gráfico de barras a partir del dataframe `starwars` (incluido en la librería dplyr) en el que se represente la proporción de cada sexo (columna `sex`) en función del color de pelo (columna `hair_color`) del personaje

2. ¿Qué sucede cuando el color de pelo es castaño (`hair_color` es "auburn")?
