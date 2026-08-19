# Control de Peso en Clínica Veterinaria

## Descripción

Este programa permite llevar el control del peso de una mascota durante un tratamiento veterinario.

El sistema trabaja con una mascota a la vez y permite almacenar un máximo de 10 controles de peso. Los pesos se guardan con un un arreglo y pueden ser registrados, consultados y modificados.

Además, el programa permite calcular estadísticas a partir de los controles que se guardaron, como el peso promedio, el peso mayor y el peso menor.

## Funcionalidades

El programa permite hacer lo siguiente:

1. Crear una nueva mascota.
2. Registrar un nuevo control de peso.
3. Consultar el historial de pesos registrados.
4. Consultar el peso de un control específico.
5. Modificar el peso de un control previamente registrado.
6. Calcular el promedio de los pesos registrados.
7. Obtener el peso mayor y el peso menor.
8. Consultar cuántos controles han sido registrados y cuántos continúan disponibles.
9. Salir del programa.

El sistema se encarga de verificar que el peso sea mayor que 0, que no se registren más de 10 controles y que no se consulten o modifiquen posiciones que todavía no hayan sido utilizadas.

# Modelo Vista Controlador

El programa utilizará el modelo vista controlador para separar las diferentes partes del programa.

- Modelo: La clase Mascota será el modelo, porque es la que guarda la información de la mascota y los controles de peso.
- Vista: La clase Vista será la encargada de interactuar con el usuario, mostrar el menú, pedir los datos y mostrar los resultados.
- Controlador: La clase Controlador será la encargada de comunicar la Vista con la clase Mascota y realizar las acciones dependiendo de lo que seleccione el usuario.

# Modelo

## Clase Mascota

### Propósito

La clase Mascota será la mascota que se encunetre en ese momento activa en la clínica

Esta clase almacena la información básica de la mascota y administra sus controles de peso.

### Atributos de Masctoa

#### nombre

* Tipo: string
* Privado
* Propósito: Almacena el nombre de la mascota.

#### especie

* Tipo: enum
* Privado
* Propósito Almacena la especie de la mascota.

#### edad

* Tipo: float
* Privado

- **Propósito:** Almacena la edad de la mascota.

#### peso

* Tipo: double[]
* Privado
* Proposito: almacenar el peso de las mascotas, con un máximo de 10 posiciones

#### cantidadControles

* Tipo: int
* Privado
* Proposito: Lleva el registro de cuántos controles de peso han sido almacenados. También permite identificar cuál es la siguiente posición disponible dentro del arreglo.

### Constructor

#### Mascota(String nombre, String especie, int edad)

Crea una nueva mascota utilizando su nombre, especie y edad.

Al crear una mascota:

- Se crea un arreglo con espacio para 10 pesos.
- cantidadControles comienza en 0, porque la mascota todavía no posee controles que se hayan guardado.

### Métodos

#### registrarPeso(double peso)

Registra un nuevo control de peso en la siguiente posición disponible del arreglo.

Antes de guardarlo verifica que:

- El peso sea mayor que 0.
- Aun haya espacio en el arreglo, porque maximo son 10 espacios.

Después de registrar el peso, aumenta cantidadControles.

---

#### consultarPeso(int numeroControl)

Permite obtener el peso de la mascota de un control en especifico.

Recibe el número del control que se desea consultar y verifica que ese control haya sido registrado antes de usar el arreglo.

---

#### modificarPeso(int numeroControl, double nuevoPeso)

Permite que se cambie el peso que se guardo antes.

Verifica que:

- El número de control corresponda a un control que si exista.
- El nuevo peso sea mayor que 0.

---

#### calcularPromedio()

Calcula el promedio de todos los pesos guardados

El método recorre únicamente las posiciones utilizadas del arreglo, desde la posición 0 hasta cantidadControles - 1.

---

#### obtenerPesoMayor()

Recorre los controles que se han guardado y busca cuál es el peso más alto que se haya guardado.

---

#### obtenerPesoMenor()

Recorre los controles que se guardaron antes y busca cuál es el peso más bajo que se haya guardado.

---

#### getCantidadControles()

Devuelve la cantidad de controles de peso que han sido guardado.

---

#### getControlesDisponibles()

Calcula y devuelve cuántos controles todavía se pueden guardar.

---

#### getNombre()

Devuelve el nombre de la mascota.

#### getEspecie()

Devuelve la especie de la mascota.

#### getEdad()

Devuelve la edad de la mascota.

---

# Vista

## Clase Vista

### Propósito

La clase Vista es la encargada de interactuar con el usuario, mostrar el menú, pedir los datos que se necesitan y mostrar los resultados.

### Atributos

#### scanner

 Será el que lee los datos ingresados por el usuario

### Métodos

#### mostrarMenu()

Muestra al usuario todas las opciones que puede realizar en el programa y obtiene la opción que seleccione.

---

#### pedirNombre()

Pide al usuario el nombre de la mascota.

---

#### pedirEspecie()

Pide al usuario la especie de la mascota.

---

#### pedirEdad()

Pide al usuario la edad de la mascota.

---

#### pedirPeso()

Pide al usuario el peso de la mascota.

---

#### pedirNumeroControl()

Pide al usuario el número de control que quiere consultar o modificar.

---

#### mostrarMensaje()

Muestra al usuario los mensajes o resultados del programa.

---

# Controlador

## Clase Controlador

### Propósito

La clase Controlador es la encargada de comunicar la Vista con el Modelo. Recibe lo que el usuario selecciona en la Vista y utiliza los metodos de Mascota para realizar lo que se necesite.

### Atributos

#### mascota

- Tipo: Mascota
- Privado
- Proposito: Guarda la mascota que está siendo usada en ese momento en el programa.

#### vista

Permite utilizar la Vista para pedir datos y mostrar información al usuario.

### Métodos

#### ejecutar()

Este es el encargado de:

* Mostrar el menú utilizando la Vista.
* Recibir la opción que seleccione el usuario.
* Realizar la acción dependiendo de la opción seleccionada.
* Utilizar los métodos de Mascota cuando se necesiten.
* Repetir el menú hasta que el usuario quiera salir.

---

#### crearMascota()

Obtiene los datos de la mascota utilizando la Vista y crea una nueva mascota.

---

#### registrarControl()

Obtiene el peso utilizando la Vista y utiliza Mascota para registrar el nuevo control.

---

#### consultarHistorial()

Obtiene los pesos que se han guardado de la mascota y los muestra al usuario.

---

#### consultarControl()

Obtiene el número de control que quiere consultar el usuario y muestra el peso que se guardó en ese control.

---

#### modificarPeso()

Obtiene el número de control y el nuevo peso que ingresa el usuario y utiliza Mascota para modificar el peso.

---

#### mostrarPromedio()

Utiliza Mascota para calcular el promedio de los pesos guardados y muestra el resultado al usuario.

---

#### mostrarPesoMayorMenor()

Utiliza Mascota para obtener el peso mayor y el peso menor y muestra los resultados al usuario.

---

#### mostrarControlesDisponibles()

Obtiene la cantidad de controles que se han registrado y los que todavía están disponibles y los muestra al usuario.

# Clase Main

### Propósito

La clase Main es el driver program del sistema y es donde comienza la ejecución del programa.

### Métodos

#### main(String[] args)

Este es el encargado de:

- Crear la Vista.
- Crear el Controlador.
- Iniciar el programa utilizando el Controlador.
