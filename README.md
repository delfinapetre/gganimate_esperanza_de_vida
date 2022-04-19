# gganimate_esperanza_de_vida

#Instalacion de paquetes

library(tidyverse)
library(gganimate)
library(rgl)
library(gapminder)
library(ggplot2)
library(animation)
library(gt)
library(datasets)

#los datos provienen del paquete gapminder y el archivo gapminder. Estos datos representa la expectativa de supervivencia en diferentes 142 países entre 1952 y 2007

p <- ggplot(
  gapminder2, 
  aes(x = gdpPercap, y=lifeExp, size = pop, colour = country)) +
  geom_point(show.legend = FALSE, alpha = 0.8) +
  scale_size(range = c(2, 12)) +
  scale_x_log10() +
  labs(x = "GDP per capita", y = "Expectativa de Vida")
p

#añadimos transicion en el tiempo

GDP_time=p + transition_time(year) +
 labs(title = "Año: {frame_time}")

#si queremos añadir graficos por grupos

p + facet_wrap(~continent) +
  transition_time(year) +
  labs(title = "Año: {frame_time}")

#animacion de los ejes

p + transition_time(year) +
  labs(title = "Año: {frame_time}") +
  view_follow(fixed_y = TRUE)
#Listo!
