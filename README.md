# Blog-Robotica-Movil
## Practica 1: Vacuum Cleaner
Para emepezar he tenido unos problemas a la hora de leer el laser, porque habia veces que me decia que el indice no era valido y otras veces que con el mismo codigo si que de volvia un valor, esto se debe a que el laser puede tardar un tiempo en hacer el primer escaneo. Para solucionarlo he tenido que crear una variable con el contenido del laser y luego he tenido que comprobar si el tamaño del atributo values es mayor que 0. En el momento que se cumple la condicion cambiaremos el valor de una variable de condicion y asi no estamos comprobando el tamaño todo el rato.
En nuestro caso hemos elegido tres estados distintos: FORWARD, que avanza hacia adelante con velocidad constante, TURNING, que se encarga de girar a una velocidad constante un tiempo aleatorio y por último, SPIRAL, que se encarga de hacer un movimiento en espiral. Para estos 3 estados hemos definido un enumerador que hace referencia a cada estado.

Para esta practica he definido una funcion que se encarga de devolver la menor distancia que captura el laser desde el angulo 45 hasta el 135, porque se solo usaba el angulo de 90, en obstaculos finos como las patas de la silla, no lo detectaba anque se estuviera chocando con él, entonces decidi ampliar el rango y logre arreglar ese bugg. 

En la parte secuencial lo que hemos definido las variables que usaremos en el bucle de control. Una variable que se incrementa cada vez que se repite el bucle, la utilizaremos de forma similar al tiempo de ejecucion. Otras que se usaran para marcar el valor de tick en un determinado momento y así poder calcular la diferencia de ticks que llevamos, que seria algo como calcular las diferencias de tiempo. Luego tenmos otras que seran unos numeros aleatorios que marcaran el limite de la diferencia entre un tick y el actual. Por otro lado, tenemos la variable de condicion de si nos ha llegado la primera información del laser. Y por último una variable que indica el estado actual y otra que indica el previo.

La parte del bucle iterativo se repite a una frecuencia de 10 hercios. En primer lugar se hace una comprobacion de si existen valores del laser, y hasta que no llegue esa informacion no podemos hacer nada. Una vez llega se cambia el valor de condicion y no se vuelve a preguntar. 

Ahora llegamos a la parte mas importante. En funcion del estado que estemos ejecutaremos unas acciones u otra:
- Caso **FORWARD**: Cuando entramos por primera vez, es como si configurasemos el estado, guardamos el tick, obtenemos el limite aleatorio e indicamos que el estado previo ya es FORWARD. Ahora en la siguiente, ya esta todo configurado y podemos seguir con la logica. Basicamente comprobamos la distancia minima, si es menor que un valor, entonces pone a cero la velocidad lineal y cambia al estado de TURNING, si la distancia es mayor le da un valor a la velocidad lineal. Por último, comprobamos si la diferencia de ticks ha pasado el limite, si superamos el limite, significa que llevamos un tiempo avanzando sin chocarnos con nada, por tanto, poedemos cambiar al estado SPIRAL y barrer mas superficie que en linea recta.
- Caso **TURNING**: La configuración practicamente como la de FORWARD, sacamos el tick actual, el limite aleatorio e indicamos que TURNING es el estado previo. Ahora en su ejecucion hace lo siguiente, estara girando a velocidad constante hasta que la diferencia de ticks supere el limite aleatorio, cuando lo supera, ponea 0 la velocidad angular y cambia al estado de FORWARD.
- Caso **SPIRAL**: Esta configuracion es distinta a las anteriores, aqui usamos una variable de velocidad linear igualada a cero, despues le damos una velocidad constante de giro e inidcamos que el estado previo es SPIRAL. En se ejecución, lo que hace es comprobara la distancia minima, si es mayor incrementa un poquito la velocidad linear, si es menor, pone ambas velocidades a cero y pasa a TURNING

Para la practica hemos tenido que hacer muchas pruebas de los rangos aleatorios de los limites, las constantes de velocidad y las distancia minima para evitar los choques en cada caso, hasta llegar a los valores que mejor nos han funcionado.

Aqui tenemos un video en camara rápida de una de las mejores ejecuciones que he logrado:
[[https://www.youtube.com/watch?v=TU_ID_DE_VIDEO](https://youtu.be/wUAAo6-uV7s)]([https://www.youtube.com/watch?v=TU_ID_DE_VIDEO](https://youtu.be/wUAAo6-uV7s))






