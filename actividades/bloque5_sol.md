# Soluciones

## stringr

### Expresiones regulares

La nueva expresión regular es `"^[:alnum:]+@[^\\d\\s]+\\.(com|es)$"`

### Funciones stringr

#### Ejercicio 1
1. Solución

   ```{r}
   library(dplyr)
   library(stringr)
   sales1 <- mutate(sales_clean, region_country = str_to_title(`REGIONS/COUNTRIES`))
   ```

2. Solución

   ```{r}
   library(dplyr)
   library(stringr)
   sales2 <- filter(sales1, str_detect(region_country, "^Z"))
   ```

#### Ejercicio 2

```{r}
bicis_long %>% 
   mutate(Tipo_uso = str_replace(Tipo_uso, "^Usos bicis ", "")) %>% 
   filter(Tipo_uso != "total")
```


## forcats

### Factores

1. Son de tipo numeric y factor

2. `summarize(PlantGrowth, niveles = levels(group))`

3. Las etiquetas del eje x tienen el mismo orden que los niveles del factor, que es orden alfabético

### Funciones forcats

Actividades

1. `mutate(PlantGrowth, group = fct_collapse(group, trt = c("trt1", "trt2")))`

2. Solución

   ```{r}
   starwars %>%
       summarize(fct_count(homeworld)) %>%
       arrange(desc(n))
   ```

3. `sw <- mutate(starwars, homeworld = fct_lump(homeworld, n = 5))`

## lubridate

### Fechas

1. Solución

   ```{r}
   library(readr)
   accidentes <- read_csv2('AccidentesBicicletas_2017.csv',
                           skip = 2, 
                           locale = locale(encoding = 'latin1'))
   ```

2. `accidentes <- mutate(accidentes, Fecha_hora = dmy_hm(Fecha))`
3. `accidentes <- mutate(accidentes, Fecha = as_date(Fecha_hora))`

### Funciones lubridate

```{r}
bicis_hasta_1503 <-
  bicis_long %>%
    filter(DIA <= ymd("20200315")) %>%  # apartado 1
    mutate(dia_semana = wday(DIA))      # apartado 2

# apartado 3
bicis_hasta_1503 %>%
  group_by(dia_semana, Tipo_uso) %>%
  summarize(total_usos = sum(Usos))
  
# apartados 4 y 5
bicis_long %>% 
   mutate(DIA = as_date(DIA)) %>% 
   ggplot(aes(x = DIA, y = Usos)) +
     geom_col() +
     geom_vline(xintercept = ymd("2020-03-16"), linetype = "dashed") +
     annotate("text", x = ymd("2020-03-17"), y = 10000,
              label = "Cierre BiciMAD\npor estado de alarma",
              hjust = "left") +
     labs(x = "Día", y = "Número total de usos")
```
