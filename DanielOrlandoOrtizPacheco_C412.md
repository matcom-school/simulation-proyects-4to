# Proyecto de Eventos Discretos

    Daniel Orlando Ortiz Pacheco C-412

# Problema Seleccionado (Aeropuerto de Barajas)

En el Aeropuerto de Barajas, se desea conocer cuánto tiempo se encuentran vacías las pistas de aterrizaje. Se conoce que el aeropuerto cuenta con un máximo de 5 pistas de aterrizaje dedicadas a aviones de carga y que se considera que una pista está ocupada cuando hay un avión aterrizando, despegando o cuando se encuentra cargando o descargando mercancía o el abordaje o aterrizaje de cada pasajero.
Se conoce que el tiempo cada avión que arriba al aeropuerto distribuye, mediante una función de distribución exponencial con λ = 20 minutos.

Si un avión arriba al aeropuerto y no existen pistas vacías, se mantiene esperando hasta que se vacíe una de ellas (en caso de que existan varios aviones en esta situación, pues se establece una suerte de cola para su aterrizaje.
Se conoce además que el tiempo de carga y descarga de un avión distribuye mediante una función de distribución exponencial con λ = 30 minutos. Se considera además que el tiempo de aterrizaje y despegue de un avión distribuye normal (N(10,5)) y la probabilidad de que un avión cargue y/o descargue en cada viaje corresponde a una distribución uniforme.
Además de esto se conoce que los aviones tiene una probabilidad de tener una rotura de 0.1. Así, cuando un avión posee alguna rotura debe ser reparado en un tiempo que distribuye exponencial con λ = 15 minutos. Las roturas se identifican justo antes del despegue de cada avión.

Igualmente cada avión, durante el tiempo que está en la pista debe recargar combustible y se conoce que el tiempo de recarga de combustible distribuye exponencial λ = 30 minutos y se comienza justamente cuando el avión aterriza.
Se asume además que los aviones pueden aterrizar en cada pista sin ninguna preferencia o requerimiento.
Simule el comportamiento del aeropuerto por una semana para estimar el tiempo total en que se encuentran vacía cada una de las pistas del aeropuerto.

# Principales Ideas

Para la resolución del problema se realizó un análisis basado en los conocimientos adquiridos en la asignatura Simulación y Probabilidades. Siguiendo la descripción del problemas, se necesito la implementación de las distintas variables aleatorias con distribuciones bernoulli, exponencial y normal. En el caso particular de las variables que distribuyan de forma exponencial; en la descripción del ejercicio señalan λ = (15,20,30), como cuando una VA distribuye como una exponencial tiene valor esperado 1/λ, entonces en conjunto con los profesores se valoro que los valores 1/15, 1/20, 1/30 eran muy pequeños para representas el tiempo de las respectivas acciones, finalmente se fijaron valores de λ = (1/15, 1/20, 1/30). Las variables con distribución bernoulli fuero usadas para la representación de los eventos de rotura (bernoulli de parametro p=0.1) y carga y/o descarga (bernoulli de parametro p=0.5).

Partiendo de esta base; se aplicaron los conocimientos de simulación para diseñar un patrón de eventos que describa la situación planteada y preparar una estructura para repetir la simulación varias vez. Siguiendo las pautas marcadas en clases, se realizaron inicialmente 30 simulaciones y a partir de ellas se continuo el procesos almacenado cada uno de los resultados. En cada uno de los pasos posteriores al paso 30, luego de almacenar los resultados, se realizan calculos para estimar la media y la varianza de cada uno de los 5 conjuntos de resultados (uno por cada pista). A partir de la varianza estimada se puede calcular un buen punto de parada para la simulación, en este caso se fijo S/√n = 0.2, realizandose aproximadamente 1200 simulaciones

# Modelo de Simulación de Eventos Discretos

La simulación se baso en dos eventos en concreto, los cuales desencadenaban o no el resto de los eventos descritos:

- Arribo de un avión: En el momento que arriba un avión al aeropuerto se pueden dar dos situaciones que exista pista libre o no. En caso que no exista pista libre dicho avión se añade a una cola hasta que le toque aterrizar. En caso contrario; entonces existe una pista libre antes de que llegue el avión, por tanto el tiempo entre que se liberó la pista y arribó el avión es el tiempo que interesa contabilizar, dicha pista es ocupada por este avion y se genera el próximo tiempo de liberación de la pista. Dicho tiempo esta formado por el arribo, el maximo entre el tiempo de recarga de combustible o el de carga y descarga si la hubiera, la solución de roturas si la hubiera y finalmente el despegue
- Despegue de un avión: En el momento en que despegue un avión se chequea si hay algún otro esperando en la cola, de ser así, se saca al mismo de la cola y se genera su proximo despegue como se explico anteriormente. Este caso no aporta al tiempo libre de la pista, pues el avión que ocupa la pista llego antes de que se liberara la misma

# Consideraciones obtenidas a partir de la ejecución de las simulaciones del problema

Luego de la ejecución de la simulación, implementada bajo las pautas antes expuestas se obtuvieron los siguientes resultados:

- La pista 0 esta libre aproximadamente 6.43 horas a la semana
- La pista 1 esta libre aproximadamente 16.78 horas a la semana
- La pista 2 esta libre aproximadamente 27.85 horas a la semana
- La pista 3 esta libre aproximadamente 38.98 horas a la semana
- La pista 4 esta libre aproximadamente 55.41 horas a la semana

### El enlace al repositorio del proyecto en Github

http://a.com
