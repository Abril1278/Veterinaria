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

#### `cantidadControles`

* **Tipo:** `int`
* **Visibilidad:** `private`
* **Propósito:** Lleva el registro de cuántos controles de peso han sido almacenados. También permite identificar cuál es la siguiente posición disponible dentro del arreglo.

### Constructor

#### `Mascota(String nombre, String especie, int edad)`

Crea una nueva mascota utilizando su nombre, especie y edad.

Al crear una mascota:

* Se crea un arreglo con espacio para 10 pesos.
* `cantidadControles` comienza en `0`, debido a que la mascota todavía no posee controles registrados.

### Métodos

#### `registrarPeso(double peso)`

Registra un nuevo control de peso en la siguiente posición disponible del arreglo.

Antes de almacenarlo verifica que:

* El peso sea mayor que `0`.
* Exista espacio disponible en el arreglo.

Después de registrar correctamente el peso, aumenta `cantidadControles`.

---

#### `consultarPeso(int numeroControl)`

Permite obtener el peso correspondiente a un control específico.

Recibe el número del control que se desea consultar y verifica que dicho control haya sido registrado antes de acceder al arreglo.

---

#### `modificarPeso(int numeroControl, double nuevoPeso)`

Permite cambiar el peso almacenado en un control existente.

Verifica que:

* El número de control corresponda a un control registrado.
* El nuevo peso sea mayor que `0`.

---

#### `calcularPromedio()`

Calcula el promedio de los pesos registrados.

El método recorre únicamente las posiciones utilizadas del arreglo, desde la posición `0` hasta `cantidadControles - 1`.

---

#### `obtenerPesoMayor()`

Recorre los controles registrados y determina cuál es el peso más alto almacenado.

---

#### `obtenerPesoMenor()`

Recorre los controles registrados y determina cuál es el peso más bajo almacenado.

---

#### `getCantidadControles()`

Devuelve la cantidad de controles de peso que han sido registrados.

---

#### `getControlesDisponibles()`

Calcula y devuelve cuántos controles todavía pueden registrarse.

El resultado se puede obtener mediante:

`10 - cantidadControles`

---

#### `getNombre()`

Devuelve el nombre de la mascota.

#### `getEspecie()`

Devuelve la especie de la mascota.

#### `getEdad()`

Devuelve la edad de la mascota.

---

## Clase `Main`

### Propósito

La clase `Main` funciona como el **driver program** del sistema.

Es responsable de interactuar con el usuario, mostrar el menú principal, solicitar los datos necesarios y utilizar los métodos de la clase `Mascota`.

### Atributos posibles

#### `scanner`

* **Tipo:** `Scanner`
* **Visibilidad:** `private static`
* **Propósito:** Permite leer la información ingresada por el usuario desde la consola.

#### `mascota`

* **Tipo:** `Mascota`
* **Visibilidad:** `private static`
* **Propósito:** Mantiene una referencia a la mascota que se encuentra activa actualmente en el sistema.

### Métodos

#### `main(String[] args)`

Es el punto de inicio del programa.

Se encarga de:

* Mostrar el menú.
* Leer la opción seleccionada por el usuario.
* Ejecutar la operación correspondiente.
* Mantener el programa funcionando hasta seleccionar la opción de salir.

### Métodos auxiliares posibles

Para mantener organizado el programa, el menú puede dividirse en métodos auxiliares como:

* `crearMascota()`
* `registrarControl()`
* `mostrarHistorial()`
* `consultarControl()`
* `modificarPeso()`
* `mostrarPromedio()`
* `mostrarMayorMenor()`
* `mostrarControlesDisponibles()`

Estos métodos se encargan principalmente de la interacción con el usuario y utilizan los métodos correspondientes del objeto `Mascota`.

---

# Uso del arreglo

Los controles de peso se almacenan en el atributo:

`double[] pesos = new double[10];`

El arreglo tiene una capacidad fija de 10 posiciones.

La variable `cantidadControles` indica cuántas posiciones han sido utilizadas y permite determinar la siguiente posición disponible.

Por ejemplo, si:

`cantidadControles = 3`

significa que las posiciones utilizadas son:

`pesos[0]`
`pesos[1]`
`pesos[2]`

y la siguiente posición disponible es:

`pesos[3]`

De esta manera, para recorrer únicamente los controles registrados se recorren las posiciones desde `0` hasta `cantidadControles - 1`.

---

# Encapsulamiento

Los atributos de la clase `Mascota` se declaran como `private` para evitar que otras clases puedan modificarlos directamente.

Las operaciones sobre los controles de peso se realizan mediante métodos `public`, permitiendo controlar y validar los cambios realizados sobre los datos.

De esta manera se aplica el principio de **encapsulamiento** de la programación orientada a objetos.

---

# Estructura general

```text
Main
 └── Mascota
      ├── nombre : String
      ├── especie : String
      ├── edad : int
      ├── pesos : double[]
      └── cantidadControles : int
```

La clase `Main` utiliza una instancia de `Mascota`, mientras que la clase `Mascota` es responsable de almacenar su información y administrar los controles de peso.
