Emilio Pinelo Landarte - A01710103

TC.1030.301 Proyecto POO 

# SISTEMA DE RESERVACIONES DE CADENA HOTELERA

## CONTEXTO/UML 
Para este proyecto decidí crear un sistema de reservaciones de una cadena hotelera. La idea principal del programa es generar una serie de reservaciones de hotel para los clientes de diferentes hoteles. El cliente tendrá la opción de elegir el tipo de habitación que deseé y se le hará la cotización y confirmación de su reservación con los métodos correspondientes. El programa está sujeto a cambios indefinidos y hay detalles que se deben afinar en las próximas semanas para lograr el objetivo. Detalles que podrían provocar errores en el programa, como el tipo de atributos y/o métodos utilizados, la definición de las clases y las relaciones entre estas o algunos métodos que podrían funcionar de forma diferente o no funcionar correctamente. 

El programa tiene como base 7 clases diferentes: Hotel, Habitacion, HabitancionSimple, HabitacionDoble, Suite, Cliente y Reservacion. Donde la clase Hotel está compuesta por una serie de habitaciones, sabiendo que un hotel debe tener habitaciones para cumplir con su funcionamiento, y la clase base Habitacion tiene una relación de herencia con las clases derivadas HabitacionSimple, Habitacion Doble y Suite, debido a que las clases derivadas son los tipos de habitación con las que el hotel puede contar. La clase Cliente tiene una relación de agregación con la clase Hotel, pues el hotel no depende del cliente para ser un hotel, pero es una parte importante para la actividad en este. Finalmente, la clase Reservacion está asociada con las clases Cliente, Habitacion y Hotel, pues para realizar una reservación se necesita información sobre el cliente, como el nombre y el número de teléfono, sobre la habitación reservada, como el tipo de habitación, y sobre el hotel, como en que hotel de la cadena se realizó la reservación. 

## Implementación de las clases 

Comencé con la implementación de las clases propuestas en el UML. La definición y la implementación de cada elemento de las clases se realizaron por separado. 

Comenzando por la clase Habitacion, clase base de las clases derivadas HabitacionSimple, HabitacionDoble y Suite, las cuales heredan los atributos y métodos de Habitacion. Se declaran los atributos de la clase Habitacion protegidos para que sean accesibles por las clases derivadas, y los métodos, incluyendo el constructor, setters y getters, se declaran públicos para permitir la creación y manipulación de los objetos. En el caso de los métodos mostrarDetalles() y calcularPrecio(), se sobreescriben las implementaciones para cada una de las clases derivadas, haciendo uso de virtual en cada uno.

Por otro lado, se definen e implementan las clases Cliente, Hotel y Reservacion. Que si bien no tienen una relación de herencia con otra clase serán necesarias para el funcionamiento del programa. Se utilizan modificadores private para atributos y public para métodos, constructores, setters y getters. 
Para cada una de las clases, excepto en dos de las tres clases derivadas de Habitacion, se hizo una sobrecarga con los constructores, utilizando parámetros distintos entre el constructor por omisión y el constructor con parámetros.

## Polimorfismo 
Para cumplir con el uso de Polimorfismo en mi programa, utilice un vector de apuntadores a objetos de tipo Habitacion en los objetos de tipo Hotel. El polimorfismo permite que el vector almacene diferentes tipos de habitaciones y que se llame de manera dinámica a la implementación correcta en tiempo de ejecución, basándose en el tipo de habitación apuntada por cada apuntador de tipo Habitacion*.

## Clases Abstractas 
En mi programa, convertí a la clase Habitacion en clase abstracta con el uso de virtual y const = 0. Esto provoca que no se puedan crear instancias directas de Habitacion, solo de sus clases derivadas, las cuales proporcionan una implementación específica de los métodos virtuales. Adicionalmente, permite que un apuntador o referencia de tipo Habitacion* pueda apuntar a cualquier objeto de una clase derivada de Habitacion. 

## Revisión Final
Para la entrega final del proyecto, realicé las siguientes modificaciones:

Implementé los constructores por "omisión" de las clases derivadas de Habitacion. Se usan valores por defecto, pero a la vez el paso por parámetros, así cumpliendo en cierta medida con la sobrecarga en el código. Esto debido a que cada habitación tiene su nombre y precio, por lo que poner el nombre y precio por defecto en el constructor por omisión de Habitacion no era opción.

Creé una clase más en mi programa llamada Menu. Esta clase lo que hace es generar la interacción con el usuario desplegando un menú al correr el programa. La clase menú utiliza todos los métodos de las clases necesarios para cumplir con esta interacción. Lo primero que hace es utilizar su constructor por omisión que crea tres hoteles con el constructor por omisión de la clase Hotel y los almacena en el vector de hoteles del objeto Menu. Después utiliza el método iniciar() en donde ocurre la interacción con el usuario, empezando por preguntar por el hotel con el que desea interactuar para posteriormente desplegar el menú del hotel correspondiente. En el menú se muestran diferentes opciones. Cada una de las opciones utilizará los métodos de la clase Menu, que a su vez utiliza los métodos correspondientes de las demás clases para cumplir con la tarea. Por ejemplo, el método hacerReservacion() utilizará métodos como buscarHabDisp() de la clase Hotel, que a su vez utiliza el método getDisponibilidad() de la clase Habitacion. También utiliza el método confirmaReservacion() de la clase Reservacion.

Adicional a la nueva clase Menu, dentro de esta, se realizan distintas evaluaciones sobre las entradas del usuario, como verificar que la entrada esté en el intervalo de opciones correcto, o que la entrada sea un número entero. Para esto se utilizó clear() e ignore() para eliminar el estado de error y limpiar el búfer para que el usuario intente ingresar nuevamente su entrada.

También, se modificó el main() para utilizar el constructor e iniciar la interacción con el usuario. La itención de crear una clase Menú fue para no saturar el main() de impresiones y lectura de variables y solo utilizar los métodos necesarios.

Finalmente, se modificó el diagrama UML con todos los cambios del programa.

**NOTA**: En este programa se hizo uso de vectores en lugar de arreglos. Esto debido a la capacidad de control automático de memoria de los vectores, la flexibilidad en el tamaño y la facilidad de uso, pero sobre todo porque no se sabía sobre la instrucción del uso de arreglos en vez de vectores. Sin embargo, estoy consiente de que es importante saber utilizar arreglos para futuros proyectos, por lo que me comprometo a estudiar el uso de arreglos en C++.
