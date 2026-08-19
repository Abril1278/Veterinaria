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


# Clases

## Clase Mascota

### Propósito

La clase Mascota será la mascota que se encunetre en ese momento activa en la clínica

Esta clase almacena la información básica de la mascota y administra sus controles de peso.

### Atributos de Masctoa

#### nombre

- Tipo: string
- Privado
- Propósito: Almacena el nombre de la mascota.

#### especie

- Tipo: enum
- Privado
- Propósito Almacena la especie de la mascota.

#### edad

- Tipo: float
- Privado
* **Propósito:** Almacena la edad de la mascota.

#### peso

- Tipo: double[]
- Privado
- Proposito: almacenar el peso de las mascotas, con un máximo de 10 posiciones

#### cantidadControles

- Tipo: int
- Privado
- Proposito: Lleva el registro de cuántos controles de peso han sido almacenados. También permite identificar cuál es la siguiente posición disponible dentro del arreglo.

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

## Clase Main

### Propósito

La clase Main es el driver program del sistema, es decir que el Main es el que va a interactuar con el usuario, el que muestra el menú, el que podrá solicitar los datos que se necesitan y usat los metodos de la clase Mascota

### Atributos

#### scanner

- Tipo: scanner
- Proposito: Lee los datos que ingrea el usuario

#### mascota

- Tipo mascota
- Proposito: Guarda la mascota que está siendo usada en ese momento en el programa.

### Métodos

#### main(String[] args)

Este es el encargado de: 

* Crear el Scanner.
* Pedir los datos de la mascota.
* Crear el objeto Mascota.
* Mostrar el menú de opciones.
* Leer la opción que el usuario seleccione.
* Llamar a los métodos de Mascota dependiendo de la opción seleccionada.
* Repetir el menú hasta que el usuario quiera salir.