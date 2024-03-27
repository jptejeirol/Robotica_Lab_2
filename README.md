# Robotica_Lab_2
CAPACITACIÓN BÁSICA EPSON RC+ 7.0 – ROBOTS SCARA SERIE T  
## Integrantes:  
Juan Pablo Tejeiro Londoño  

## Descripción de la práctica:  

Para el desarrollo del laboratorio 2 se realiza la práctica propuesta por la guía de capacitación de CDM en las instalaciones físicas de la empresa CDM con ayuda del robot EPSON VT6L. EL principal requerimiento para la práctica es la instalación del software EPSON RC+ 7.5.2, ya con esta herramienta informática se puede generar una simulación de rutina para el robot y además implementarla en la práctica real haciendo uso de la conexión por USB al controlador integrado del robot.  

Para empezar a diseñar una rutina del robot, primero se debe configurar el robot en el entrono de simulación y un controlador virtual, seguido a esto se debe utilizar la herramienta de robot manager para manipular manualemnte el robot y configurar las posiciones del mismo. En la guía se pideque se ubiquen varios puntos y se ejecute diversas instrucciones de movimiento entre estos puntos. Durante la implementación se presnetan muchs errores realcionados con el tipo de movmiento y la velocidad de movimiento, para solucionar esto solo se tuvo que limitar la velocidad y aceleración de acercamiento y en algunnos casos variar el órden de ejecución de las isntrucciones. De igual manera en un caso en particular fue necesario crear una interpolación entre puntos, modificando la trayectoria de un puntoa otro y evitando singularidades del robot en la trayectoria original.  

![image](https://github.com/jptejeirol/Robotica_Lab_2/assets/164267794/420031a2-b07e-4725-90c4-440fdef149e2)  

EL lenguaje de programación utilizado en los controladores de robot EPSON es el lenguaje SPEL+, la declaración en este lenguaje es bastante simple, y la interfaz de desarrollo del entorno facilita mucho mas la programación con las asistencias en la sintaxis del lenguaje. En el código se observa las declaraciones inciales de poder y velocidad y aceleración, tanto para las instrucciones de movimiento GO como las Move. Además se observa la declaración de los bucles de las rutinas de ejemplo en la guía práctica que únicamente rqeuiere del comando "Do" con la palabra "Loop" al final de las instrucciones.  

![image](https://github.com/jptejeirol/Robotica_Lab_2/assets/164267794/23b94a70-26de-46a2-94a3-fdb87b0d4dd4)

El código anterior, declara de manera muy simple la llamada condicional de las 3 funciones tipo pallet de cumplirse la condición de que la respectiva entrada se encuentre activa.  

![image](https://github.com/jptejeirol/Robotica_Lab_2/assets/164267794/6f05cfa7-8b6e-4167-b7b4-6894cae6c95f)  

![image](https://github.com/jptejeirol/Robotica_Lab_2/assets/164267794/0b5f1e21-4c35-4c0a-a619-c6ca01ef3f29)  

![image](https://github.com/jptejeirol/Robotica_Lab_2/assets/164267794/1ce22190-faa6-4bec-8e35-4299f226bf24)

El las figuras anteriores se observa la sintaxis de la declaración de funciones en SPEL+, se observa que cada pallet utiliza ciclos for, y el lenguaje permite declarar las variables de iteración de manera global ahorrando lineas de código en cada declaración de las funciones. Se utiliza de diferentes formas el ciclo for para diseñar el tipo de creación del pallet, en el primer caso es sencillo pues se utiliza la foma estándar del pallet en su órden del 1 al 9 para un pallet de 3x3. En el segundo caso se varía el tipo de construcción del pallet generando 3 ciclos for en serie invirtiendo el órden de iteración del segundo cliclo. Y en el tercer caso se implementan 2 for anidados para extender en cada fila y columna la dimensión del pallet. 

En la siguiente imágen se observa 

## Simulación en software EPSON:  

En el software se pudo ejecutar toda la rutina planteada por la guía, que incluye las instrucciones de movimiento de los puntos descritos al principio de la guía en bucle, pero finalmente la implementación en el robot físico es únicamente de las funciones de pallet, por lo cuál la simulación se muestra solo con esta parte de la rutina pero incluyendo la gestión de entradas para activar cada llamado de función de pallet.  

En el video se observa para la simulación se utiliza el controlador "lab2", un controlador virtual creado por medio del software para la utilización del modelo del robot en el entorno de EPSON. PAra ejecutar la simulación se contruye el programa y se ejecuta a nivel de POWER HIGH, puesto que en el entorno de simulación no hay peligro alguno al utilizar la velocidad máxima del robot. Al incio de la simulación se ve que el robot no inicia la rutina automáticamente, para esto se activa el gestor de entradas y salidas y se activa la entrada 9 como se configuró en el código, en este momento se observa como el robot incia su rutina de movimiento, cuando cada rutina termina se activa la siguiente entrada y se observa que el patrón del pallet cambia dependiendo de la función de pallet que cada entrada llama en el código.  

https://github.com/jptejeirol/Robotica_Lab_2/assets/164267794/95f12765-97b9-41da-8668-f6266a53b676

## Implementación en práctica real:  

Para la práctica con el robot físico es indispensable realizar cambios en el código, el principal es cambiar de "POWER HIGH" a "POWER LOW" en la declaración del código, luego de esto el ingeniero encargado pidió también que se comentara las rutinas de bucle y la declaración de entradas para el llamado de las funciones de pallet. En el video se observa que únicamente se ejecuta en órden las rutinas de las funciones de pallet. Algo que destacar del entorno EPSON es que permite ejecutar el programa realizado solo con cambiar el controlador virtual, por el la conexión USB al controlador integrado del robot. En este caso, al ejecutar la rutina se puede observar en tiempo real como el robot se mueve dentro del entorno virtual y en el mundo físico al mismo tiempo.

https://github.com/jptejeirol/Robotica_Lab_2/assets/164267794/26f6be4f-6f62-4332-90ad-c9fb29c8db14

