# 1-de-abril-de-2016
tendencia, estacionalidad y ciclicidad en las graficas

## 1 de abril de 2016 ##
## estacionalidad, tendencia y ciclicidad.

# normalmente se utiliza el modelo aditivo... este modelo es apropiado cuando la magnitud de las
# fluctuaciones estacionales de la serie no varian al  hacerl la tendencia

# se utiliza multiplicativo cuando la magnitud de la fluctuaaciones estacionales de la serie crece
# y decrece proporcionalmente con los crecimientos y decreciminetos de la tendencia, respect.

# una vez que logramos descomponer la st en diversos los elementos de estacionalidad y tendencia
# hay que desestacionalizar la st y elimimar la tendencia

## existe tendencia cuando existe un patron en los datos a largo plazo ya se que aumenta o disminuye 
## los datos
## la estacionalidad existe cuando la st es influenciada por factores estacionales ( por ejemplo 
## los tres primeros meses del año, el mes o el dia de la semana.)

## existe otro componente: ciclico en losb datos cuando se detectan incrementos y caidas que no 
## son de tiempo determonado
## duracion por lo general al menos de 2 años

## de estos tres elementos normalmente existen confuciones para detectarlos entre la estacionalidad
## y el componente ciclico
## principales diferencias entre estos dos componentes:
# 1) patron estacional longitud constate, patron ciclico longitud variable
# 2) duracion media del componente ciclico mas largo que la longitud del patron estacional
# 3) magnitud del ciclico mas variable que magnitud del patron estacional
# 4) el momento de picos y caidas es predecible con los datos estacionales pero impredecicle 
#    a largo plazo con datos ciclicos

install.packages("fpp")
require (fpp)
help(fpp)
plot(window(elec, start = 1980), ylab = "GWh", main = "Australlian electricity production")
# tiene una tendencia a la alza presentando menos de 8000 gwh en 1980 y va en aumento durante ese 
# periodo hasta 1995 con un maximo de 14000 gwh
# existe estacionalidad por que cada cierto tiempo se repite un comportamiento semejante 

plot(bricksq, ylab = "millon units", xlab = "Year", main = "Australian clay brick production")
# tiene una tendencia a la alza desde 1960 y a la alza hasta 1990 con 500 millones de unidades
# se observa una estacionalidad pero solo de 1960 a 1975 aproxmadamente y despues empeiza a 
# comportarse de diferente manera
# se observa una etacionalidad en 1975 aporx con una caida muy pronunciada y tambien en 1983 c
# con una caida uan mas larga 

plot(hsales, main = " Sales of new one-family house, USA", ylab = "total sales", xlab = "year")


## EJERCICIO:

LIVERPOOL <- read.csv("C:\\Users\\SALA-C9\\Downloads\\LIVERPOOL.csv", header = T)
STliverpool <- ts(LIVERPOOL[,5], start = 2000, frequency = 12)
## [,5] PARA QUE SOLO HAGA SERIE DE TIEMPO LA COLUMNA 5 DEL ARCHIVO
plot(STliverpool, main= "Liverpool precios de cierre", xlab = "año", ylab = "precio cierre")
# los precio de la accion liverpool para el año 2000 era por debajo del los 25 pesos y hata el 2005
# mantuvo una posicion muy aproximada o constante perodespues del 2005 empieza a aumentar su precio
# y asi contunio hasta inicios del 2016 alcanzando un precio de 200 pesos aproximadamente
## realmente no presenta estacionalidad porque sus comportamientos no son muy constantes
### no presenta ciclicidad

CEMEX <- read.csv("C:\\Users\\SALA-C9\\Downloads\\CEMEX.csv", header = T)
STcemex <- ts(CEMEX[,5], start = 2000, frequency = 12)
plot(STcemex, main= "Cemex precios de cierre", xlab = "año", ylab = "precio cierre")
# no presenta estacionalidad ni tendencia 
## presenta ciclicidad en el año 2005 en donde se escontraba con un precio de mas de 80 pesos aprox 
## y presenta una caida obteniendo un precio de poco mas de 40 pesos, presenta un segundo punto de 
## cilcicidad cundo en 2006 empezaba a aumentar sus precio y levantarse pero de nuevo presenta una caida
## presentando un precio de 70 aprox pero con la caida llego a los 30 pesos aprox

BIMBO <- read.csv("C:\\Users\\SALA-C9\\Downloads\\BIMBO.csv", header = T)
STbimbo <- ts(BIMBO[,5], start = 2000, frequency = 12)
plot(STbimbo, main= "Bimbo precios de cierre", xlab = "año", ylab = "precio cierre")
# presenta tendencia a la alza del 2000 al 2007 pero despues ya no presenta un tendencia definida
## presenta estacionalidad del 2000 al 2007 con pequeños decrementos e incrementos, despues ya 
## presenta cambis muy marcados
### presenta dos puntos de ciclicidad en 2008 presentando un acida de 70 a 40 pesos y despues en
### 2011 presenta una caida aun mas marcada teniendo una caida de 95 pesos hasta 25 pesos, un gran decremento

##para guardarlas como imagen

jpeg ("bimbo grafica,jpg")
plot(STbimbo, main= "Bimbo precios de cierre", xlab = "año", ylab = "precio cierre")
dev.off()

jpeg ("cemex grafica,jpg")
plot(STcemex, main= "Cemex precios de cierre", xlab = "año", ylab = "precio cierre")
dev.off()

jpeg ("liverpool grafica,jpg")
plot(STliverpool, main= "Liverpool precios de cierre", xlab = "año", ylab = "precio cierre")
dev.off()
