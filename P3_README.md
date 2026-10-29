# VFFCo

Bueno en esta practica lo que estamos haciendo es un formula 1 que va por un circuito y tiene que completarlo evitando los obstaculos que se va encontrnado por el camino, para ello utilizaremos los datos que nos devuelve el lidar que tenemos en el morro del formula 1.

En primer lugar lo que hemos hecho es una comprobacion de si hay un target activo en caso de que no lo haya, obtendremos el nuevo target y pondremos en una condicion que esta activo, a partir de ahí dibujaremos con la interfaz de debugging la posicion del target al inicio de cada iteracion.

Después pasaremos a sacar el vector del checkpoint en relación con el formula 1 a través de la función que se proporciona en el guión de la práctica. Esta será nuestra fuerza atractiva. Como el vector puede ser muy grande cuando nos dan un nuevo checkpoint, hemos decidido darle un valor máximo para que no sea muy superior a la fuerza repulsiva. Después, utilizaremos la una función que nos devolverá el vector repulsivo. Para calcular este vector, la función recoge todos los vectores cuya distancia es menor que un threshold (distancia minima para ser considerada obstaculo), luego normalizamos estos vectores, los invertimos y los hacemos inversamente proporcionales a la distancia. Con todas esas fuerzas repulsivas calculamos cual es la media de todas ellas y devolvemos el resultado. Para que todo funcionase correctamente y la fuerza repulsiva fuera muy debil, he obtado por hacer que los vectores repulsivos fuesen inversamente proporcionales al cubo de la distancia, porque sino no ejercian la fuerza necesaria para no chocarse. De esta manera, logramos obtener el vector atractivo y el repulsivo, los cuales nos sirven para obtener el vector resultante de sumar ambos vectores. Dibujaremos estos 3 vectores a través de la herramienta de debugging del guión.

Ahora que tenemos el vector resultante o más bien el vector de la trayectoria que hemos de seguir, se lo pasaremos a un controlador proporcional que se encargará de ver cuál es el error entre el ángulo que deberia ser cero para estar centrado y calculamos la velocidad angulare en función de ese error y una constante de proporcionalidad. Además, en función del módulo del vector tendremos una velocidad lineal mayor o menor, aunque estará acotada a unos límites de velocidad. 

Finalmente, llamaremos a una función que comprueba si hemos llegado a un rango cercano al checkpoint, en ese caso establecemos el checkpoint como marcado y devolvemos false, ya que es valor se le asigna a esa variable condición que nos indicaba si había un target activo. En caso contrario, devolverá true y así seguiremos buscando el target.




