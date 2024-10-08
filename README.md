# Practica_2

## Integrantes
- Uriel Vladimir Alvarez Tapia 20121191
- Miguel Angel Castañeda Garcia 20120015
- Diana Alejandra Mendoza Mendoza 20121226

## Introducción 
La robótica industrial es una disciplina clave en la automatización de procesos que requieren alta precisión y eficiencia. En este contexto, los robots manipuladores como el Epson C4 desempeñan un rol crucial en la industria moderna, gracias a su capacidad para realizar tareas repetitivas con exactitud y rapidez. Este robot en particular es utilizado en una amplia gama de aplicaciones que incluyen el ensamblaje, la manipulación de materiales y el manejo de componentes delicados.
Durante esta práctica, el propósito fue familiarizarse con la programación y control de movimientos de un robot industrial mediante el entorno Epson RC+. El objetivo específico fue programar al Epson C4 para mover un fusible desde una posición inicial hacia una ubicación predeterminada, utilizando la pinza del robot para sujetar y liberar el objeto de forma precisa. La tarea consistió en diseñar y programar los movimientos que el robot debía realizar, incluyendo el control de la pinza para garantizar que el fusible fuera transportado de manera eficiente y liberado en el punto exacto.
Para lograr estos objetivos, se desarrolló una secuencia de instrucciones en el entorno Epson RC+, donde se definieron las trayectorias del robot, las posiciones de agarre y liberación, así como las velocidades y orientaciones necesarias para completar la tarea.

## Objetivos
Escribir un código en el software RC+7.0 para manipular el robot Epson que sea capaz de tomar el fusible 3 y 4 e intercambiarlos de lugar con el apoyo de una posición de "espera" sobre la caja, medinate movimientos programados.



## Desarrollo
**Seteo del punto home**
Como primera instancia, se requirió hacer el ajuste del origen de coordenadas del robot, asignando como valores en los ejes cartesianos como “cero” en cada uno de ellos en la configuración Word, mientras que en la configuración Join se ajustaron todas las articulaciones excepto de J5 a 0°; mientras que J5 se le asignó el valor de 90°. Tal y como se muestra en la Figura 1:
![Captura de pantalla 2024-09-05 091638](https://github.com/user-attachments/assets/98850b11-6703-48b5-8896-c5016be9ff65)

Al seleccionar el menú de *home config* el programa transforma estos valores en valores numericos para las instrucciones del robot, figura 2
![Captura de pantalla 2024-09-05 091759](https://github.com/user-attachments/assets/29769186-b020-4dc9-9251-08bfc62e7b8d)

**Guardar coordenadas** 
El software ofrece la opción de mover el robot a voluntad del operador y, además, guardar la coordenada en la que se encuentra el brazo robótico en ese preciso instante mediante la seleccion del numero de movimiento se puede asignar un nombre para la posición designada y con el botón *teach* se guarda dichas coordenadas,el resumen de los puntos correspondientes se puede observar en la figura 3.
![Imagen de WhatsApp 2024-09-19 a las 04 03 24_5fa818b6](https://github.com/user-attachments/assets/bd0f5ca7-4824-4883-99b5-d4bf37df7b4d)


De esta manera, se conectó el equipo de computo con el brazo robotico mediante el cable USB, permitiendo determinar los puntos fisicos reales en la zona de trabajo y determinar las posiciones necesarias para realizar la encomienda, mover un fusible de lugar.

De igual forma, se probo la pinza neumatica mendiante el *I/O monitor* (Figura 4) que permite encender y apagar de forma manual las salidas digitales del brazo, en este caso usando la salida 2 que corresponde a la pinza neumatica.
![Captura de pantalla 2024-09-05 094516](https://github.com/user-attachments/assets/24170739-ca5b-4780-8588-a33f4b842dfa)

Con los puntos definidos y guardados se precedió con las líneas de comandos para las trayectorias. 

**Comandos básicos de movimiento**
El software cuenta con comandos predefinidos para ejecutar diversas acciones con el robot. Los comandos empleados durante el desarrollo de la práctica en el laboratorio son los que se mencionan en seguida. 
*Home* Mueve el robot hacia la posición del origen de coordenadas previamente configurada.
*Go* Mueve el robot hacia el punto de interés.
*On* Se encarga de activar la salida digital correspondiente, en este caso, la pinza neumática del efector final.
*Off* Apaga la salida digital seleccionada.

El código mostrado en la figura 5 ejecuta el objetivo de la práctica.

![image](https://github.com/user-attachments/assets/9c242315-197f-4176-a0f3-990944fc270f)

Primeramente se tiene el comando superior 1 que posiciona la pinza arriba del fusible 3, posteriormente tomar 1 ejecuta la acción de tomar el fusible colocando la pinza en posición y cerrándola, con arribaespera se posiciona el fusible arriba de la caja, tras dejar el fusible en la caja mediante el punto espera1 se procede a,con superior 2, colocarse sobre la posición del segundo fusible, depués con tomar 2 se toma el fusible 4, y se repiten los commandos anteriormente explicados para colocar el fusible 4 en la posición del fusible 3 y posteriormente tomar el fusible 3 desde la caja y dejarlo en la posición del fusible 4. 
Esta vez, se implementaron más comandos para realizar las acciones solicitadas en secuencia.


## Resultados
Tras ejecutar el código, primeramente se observó como el brazo tomó el fusible, esto se muestra en la figura 6:
![image](https://github.com/user-attachments/assets/b04a079e-a2ca-4c72-a3e1-9ac5f90cdc9a)

Posteriormente lo depositó en el lugar solicitado, en este caso, la caja, como se observa en la figura 7:
![image](https://github.com/user-attachments/assets/e6d3ebfc-8e08-4eb7-b6aa-37925a868a57)

Una vez finalizado el primer movimiento, en secuencia el brazo tomó el fusible 2, como se muestra en la figura 8:
![image](https://github.com/user-attachments/assets/b2dceb6c-10bb-4c30-85b3-ca4cf7c31ad7)

Y tras tomarlo, lo colocó en el lugar del primer fusible, como se solicitó y como se observa en la figura 9:
![image](https://github.com/user-attachments/assets/2e5b273e-3a97-49a2-9bd7-9fe1b7afbfcd)

Finalmente el brazo ejecutó el último movimiento en secuencia que fue colocar el fusible 1 en el lugar del fusbile 2, como se muestra en la figura 10:
![image](https://github.com/user-attachments/assets/db1dfa18-f459-4642-aa15-06f711ee9ff8)

Una vez completado todo el codigo, se realizaron las tareas de forma exitosa.

## Conclusiones
- **Uriel Vladimir Alvarez Tapia:** Al igual que la practica anterior, se evidencia la capacidad del robot para realizar rutinas de movimientos de forma rapida, eficaz y precisa. Sin embargo, gracias a la culminación del objetivo de esta sesion, se logró enfatizar la capacidad de generar un programa precodificado con los puntos que se requieran para la solucion y, una vez teniendo acceso al equipo, enseñar las posiciones correspondientes a los puntos necesitados. Esta metodologia permite reducir los tiempos de interaccion con el equipo y por lo tanto las paradas de una linea de produccion para la instalacion del mismo.
- **Miguel Angel Castañeda Garcia:** Durante la práctica, fue necesario repetir varias veces las acciones programadas para verificar que el robot realizara correctamente los movimientos deseados. Esta repetición ayudó a detectar y corregir posibles errores en la secuencia, asegurando que el robot operara de manera consistente. Esto nos muestra la importancia de probar continuamente la programación para lograr un rendimiento óptimo en tareas automatizadas, y tras las dificultades se obtuvo una mayor práctica con la manipulación del robot, permitiendo sustentar la teoría vista en clase.
- **Diana Alejandra Mendoza Mendoza:** La práctica mostró la importancia de una programación precisa para que el robot ejecute tareas pequeñas como mover fusibles de manera eficiente y sin errores. El uso de comandos simples en el software facilitó la automatización del proceso, demostrando que incluso sistemas avanzados pueden ser controlados de manera accesible. Además, repetir y ajustar las acciones fue clave para asegurar la consistencia en el desempeño del robot,observando la necesidad de pruebas continuas para optimizar su funcionamiento.









