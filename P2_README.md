# Follow line
En esta practica no hemos tenido que hacer mucho codigo de programación, ya que simplemente tenemos un par de funciones que hacen el control reactivo y las vamos llamando en cada iteracion del bucle infinito.
La primera funcion se encarga de realizar un filtrado de la imgaen a traves de hsv, le indicamos el valor minimo y el maximo del color rojo que queremos y obtenemos la mascara, es decir, una imagen en la que solo
los pixeles que son de color rojo. Despues obtenemos los momentos de la figura y calculamos el centroide. Por otro lado tenemos la funcion del pd, esta funcion se encarga de calcular el error entre la x del 
centroide y la x en la que el formula 1 esta en el centro de la linea, despues calculamos la diferencia entre el error anterior y el actual, y finalmente hacemos el calculo del pd para obtener la velocidad angular
y el calculo del p para la velocidad lineal.

Lo complicado de esta practica ha sido calcular los valores de las constantes de proporcionalidad y derivativa. Que he obtenido a base de prueba y error. En primer lugar empece por poner una velocidad lineal 
constante, y ajustando la KWP (constante proporcional de la angular) hasta empezara a oscilar. Despues emepece a subir la KWD para que frenara esas oscilaciones hasta obtener algo estable. Una vez que ya lo hemos 
estabilizado subimos la velocidad lineal constante y 
