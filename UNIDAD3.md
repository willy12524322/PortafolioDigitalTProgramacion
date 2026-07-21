
[Regresar](README.md)
# 📂 Unidad 3: Modularidad y Arreglos

### 1. Contenidos de la Unidad
En esta unidad avanzamos de la programación estructurada secuencial y condicional hacia un enfoque más robusto y escalable: la **modularidad**. Aprendimos a fragmentar problemas complejos en subprogramas (funciones) independientes y reutilizables, así como a manejar colecciones de datos homogéneas mediante **arreglos** (unidimensionales, bidimensionales y multidimensionales), fundamentales para el procesamiento de grandes volúmenes de información.

---

## 🧩 2. Modularidad

La modularidad es un principio de diseño de software que consiste en dividir un programa extenso en partes más pequeñas, independientes y con una función específica, llamadas **funciones** o **subprogramas**. Cada función recibe datos de entrada (parámetros), ejecuta un proceso interno y puede o no devolver un resultado.

**Ventajas principales:**
* **Reutilización de código:** una misma función puede invocarse múltiples veces desde distintos puntos del programa.
* **Abstracción:** quien usa la función no necesita conocer su implementación interna, solo su propósito.
* **Mantenibilidad:** facilita la depuración, ya que los errores quedan aislados dentro de bloques concretos.
* **Trabajo en equipo:** permite que distintas personas desarrollen módulos diferentes del mismo sistema de forma simultánea.

```text
                main()
           /       |       \
    Función A  Función B  Función C
           \       |       /
             Resultado final
```

Un aspecto crítico de la modularidad es la forma en la que los datos "viajan" entre el programa principal (`main`) y las funciones, lo cual se conoce como **paso de parámetros**.

---

### 2.1. Paso de Parámetros por Valor

Cuando un parámetro se pasa **por valor**, la función recibe una **copia** del dato original. Cualquier modificación que se realice sobre esa copia dentro de la función **no afecta** a la variable original del programa que la invocó.

#### 📝 Planteamiento del Problema
Calcular el precio con descuento (10%) de un producto sin alterar el precio original almacenado en el programa principal.

#### 📐 Pseudocódigo
```
Funcion aplicarDescuento(precio)
    precio <- precio - (precio * 0.10)
    Escribir "Precio con descuento (dentro de la funcion):", precio
FinFuncion

Algoritmo Principal
    Definir precioOriginal Como Real
    precioOriginal <- 100
    aplicarDescuento(precioOriginal)
    Escribir "Precio original (fuera de la funcion):", precioOriginal
```

#### 💻 Codificación (Código Fuente en C)
```c
#include <stdio.h>

void aplicarDescuento(float precio) {
    precio = precio - (precio * 0.10);
    printf("Precio con descuento (dentro de la funcion): %.2f\n", precio);
}

int main() {
    float precioOriginal = 100;

    aplicarDescuento(precioOriginal);

    printf("Precio original (fuera de la funcion): %.2f\n", precioOriginal);

    return 0;
}
```

Al ejecutar este programa, dentro de `aplicarDescuento` el precio se muestra ya rebajado (90.00), pero en `main()` la variable `precioOriginal` conserva su valor de 100, porque la función trabajó únicamente con una copia.

#### 🖥️ Ejecución del Programa
<p align="center">

<img width="756" height="67" alt="image" src="https://github.com/user-attachments/assets/3e3d443d-5a3c-46fd-aea6-fe50d5bbca17" />


</p>

---

### 2.2. Paso de Parámetros por Referencia

Cuando un parámetro se pasa **por referencia**, en lugar de enviar una copia del valor, se envía la **dirección de memoria** (mediante punteros, `*` y `&`) de la variable original. Esto permite que la función modifique directamente el valor original ubicado en `main`.

#### 📝 Planteamiento del Problema
Aumentar el stock de un producto en bodega, de forma que el cambio se conserve en el programa principal.

#### 📐 Pseudocódigo
```
Funcion aumentarStock(Ref cantidad, unidades)
    cantidad <- cantidad + unidades
FinFuncion

Algoritmo Principal
    Definir stockActual Como Entero
    stockActual <- 50
    aumentarStock(Ref stockActual, 20)
    Escribir "Stock actualizado:", stockActual
```

#### 💻 Codificación (Código Fuente en C)
```c
#include <stdio.h>

void aumentarStock(int *cantidad, int unidades) {
    *cantidad = *cantidad + unidades;
}

int main() {
    int stockActual = 50;

    aumentarStock(&stockActual, 20);

    printf("Stock actualizado: %d\n", stockActual);

    return 0;
}
```

Aquí, `stockActual` sí queda modificado después de llamar a la función, porque `aumentarStock` no trabajó con una copia, sino con la dirección de memoria real de la variable, a través del puntero `cantidad`.

#### 🖥️ Ejecución del Programa
<p align="center">

<img width="723" height="46" alt="image" src="https://github.com/user-attachments/assets/df15a17e-afef-408e-ada6-f2089e3bb6b1" />


</p>

---

## 📊 3. Arreglos

Un **arreglo** (array) es una estructura de datos que permite almacenar una colección de elementos **del mismo tipo**, bajo un único nombre de variable, ocupando posiciones consecutivas en memoria. Cada valor se identifica mediante un índice, que en lenguaje C siempre empieza en `0`. Su principal ventaja frente a declarar variables sueltas es que permite recorrer y procesar grandes cantidades de datos mediante ciclos, en lugar de escribir una instrucción por cada dato.

### Tipos de Arreglos
1. **Unidimensional (Vector):** una sola fila de datos, un índice `arreglo[i]`.
2. **Bidimensional (Matriz):** filas y columnas, dos índices `arreglo[i][j]`.
3. **Multidimensional:** tres o más dimensiones, útil para representar información con varios niveles de clasificación (`arreglo[i][j][k]...`).

---

### 3.1. Arreglo Unidimensional (Vector)

El arreglo unidimensional, o vector, organiza los datos en una sola fila, accesible mediante un único índice. Es útil para representar listas simples, como una serie de mediciones tomadas a lo largo de varios días.

```text
Índice   0    1    2    3    4    5    6
        ┌───┬───┬───┬───┬───┬───┬───┐
        │22 │24 │19 │21 │26 │23 │20 │
        └───┴───┴───┴───┴───┴───┴───┘
```

#### 📝 Planteamiento del Problema
Leer las 5 notas de un estudiante, almacenarlas en un vector y calcular el promedio del curso.

#### 💻 Codificación (Código Fuente en C)
```c
#include <stdio.h>

int main() {
    float notas[5];
    float suma = 0, promedio;
    int i;

    for (i = 0; i < 5; i++) {
        printf("Ingrese la nota %d: ", i + 1);
        scanf("%f", &notas[i]);
        suma = suma + notas[i];
    }

    promedio = suma / 5;

    printf("\nEl promedio del curso es: %.2f\n", promedio);

    return 0;
}
```

#### 🖥️ Ejecución del Programa
<p align="center">

<img width="287" height="153" alt="image" src="https://github.com/user-attachments/assets/91b3a82f-9128-4492-b9f2-16cf4cf1c313" />


</p>

---

### 3.2. Arreglo Bidimensional (Matriz)

El arreglo bidimensional organiza la información en filas y columnas, como una tabla. Resulta natural para representar datos que tienen dos dimensiones, por ejemplo, la distribución de asientos en un bus o un cine.

```text
          Columna
          0    1    2    3
Fila 0   [L]  [L]  [O]  [L]
Fila 1   [O]  [L]  [L]  [L]
Fila 2   [L]  [O]  [L]  [O]
```
*(L = asiento libre, O = asiento ocupado)*

#### 📝 Planteamiento del Problema
Leer dos matrices de 2x2, sumarlas elemento a elemento y mostrar la matriz resultante.

#### 💻 Codificación (Código Fuente en C)
```c
#include <stdio.h>

int main() {
    int matrizA[2][2], matrizB[2][2], matrizSuma[2][2];
    int i, j;

    printf("Ingrese los 4 elementos de la Matriz A:\n");
    for (i = 0; i < 2; i++) {
        for (j = 0; j < 2; j++) {
            scanf("%d", &matrizA[i][j]);
        }
    }

    printf("Ingrese los 4 elementos de la Matriz B:\n");
    for (i = 0; i < 2; i++) {
        for (j = 0; j < 2; j++) {
            scanf("%d", &matrizB[i][j]);
        }
    }

    for (i = 0; i < 2; i++) {
        for (j = 0; j < 2; j++) {
            matrizSuma[i][j] = matrizA[i][j] + matrizB[i][j];
        }
    }

    printf("\nMatriz Resultante (A + B):\n");
    for (i = 0; i < 2; i++) {
        for (j = 0; j < 2; j++) {
            printf("%d\t", matrizSuma[i][j]);
        }
        printf("\n");
    }

    return 0;
}
```

#### 🖥️ Ejecución del Programa
<p align="center">

<img width="356" height="177" alt="image" src="https://github.com/user-attachments/assets/daae91da-2574-4ad4-83b0-a02d45e3b587" />


</p>

---

### 3.3. Arreglo Multidimensional

Cuando la información requiere más de dos dimensiones, se utilizan arreglos multidimensionales. Son comunes en aplicaciones como el procesamiento de imágenes a color, videojuegos, o el control de inventario distribuido en varias bodegas y estantes.

```text
inventario[bodega][estante][producto]
```

#### 📝 Planteamiento del Problema
Registrar el inventario de una empresa con 2 bodegas, cada una con 3 estantes, y cada estante con 4 tipos de producto, y luego consultar la cantidad almacenada en una posición específica.

#### 💻 Codificación (Código Fuente en C)
```c
#include <stdio.h>

int main() {
    int inventario[2][3][4]; // 2 bodegas, 3 estantes, 4 productos por estante
    int bodega, estante, producto;

    // Llenado del inventario
    for (bodega = 0; bodega < 2; bodega++) {
        for (estante = 0; estante < 3; estante++) {
            for (producto = 0; producto < 4; producto++) {
                printf("Cantidad Bodega %d, Estante %d, Producto %d: ",
                        bodega + 1, estante + 1, producto + 1);
                scanf("%d", &inventario[bodega][estante][producto]);
            }
        }
    }

    // Consulta puntual: Bodega 1, Estante 3, Producto 2
    printf("\nCantidad en Bodega 1, Estante 3, Producto 2: %d\n",
            inventario[0][2][1]);

    return 0;
}
```

En este ejemplo, `inventario[0][2][1]` representa la cantidad de un producto específico ubicado en la bodega 1, estante 3, en la segunda posición de producto. Este tipo de arreglo permite modelar información con múltiples niveles de clasificación dentro de una sola estructura.

#### 🖥️ Ejecución del Programa
<p align="center">

<img width="447" height="578" alt="image" src="https://github.com/user-attachments/assets/ffde261c-ac3a-454b-9347-46be39b17879" />


</p>

---

## 🚀 4. Ejercicio Integrador (Modularidad + Arreglos)

### 4.1. Planteamiento del Problema
Se requiere un programa que registre las temperaturas de los 7 días de una semana en un arreglo, calcule mediante una función el promedio semanal, y determine, a través de una estructura condicional, si la semana se clasifica como "calurosa" (promedio mayor a 25 grados) o "templada" (promedio de 25 grados o menos).

### 4.2. Análisis del Problema
* **Datos de entrada:** 7 temperaturas diarias (`temperaturas[7]`, tipo real).
* **Datos de salida:** promedio semanal y clasificación de la semana.
* **Proceso lógico:** una función `leerTemperaturas` llena el arreglo; en C, los arreglos se pasan automáticamente por referencia, por lo que los valores ingresados quedan disponibles para el resto del programa sin necesidad de retornarlos explícitamente. Una segunda función `calcularPromedio` recorre el arreglo y retorna el promedio, el cual se evalúa después con una estructura `if-else`.

### 4.3. Diseño del Algoritmo (Pseudocódigo)
```
Funcion leerTemperaturas(Ref temperaturas[])
    Para i <- 0 Hasta 6 Con Paso 1 Hacer
        Leer temperaturas[i]
    FinPara
FinFuncion

Funcion promedio <- calcularPromedio(temperaturas[])
    Definir suma Como Real
    suma <- 0
    Para i <- 0 Hasta 6 Con Paso 1 Hacer
        suma <- suma + temperaturas[i]
    FinPara
    Retornar suma / 7
FinFuncion

Algoritmo Principal
    Definir temperaturas[7] Como Real
    Definir promedioSemanal Como Real

    leerTemperaturas(Ref temperaturas)
    promedioSemanal <- calcularPromedio(temperaturas)

    Si promedioSemanal > 25 Entonces
        Escribir "Semana calurosa"
    Sino
        Escribir "Semana templada"
    FinSi
```

### 4.4. Codificación (Código Fuente en C)
```c
#include <stdio.h>

void leerTemperaturas(float temperaturas[]) {
    int i;
    for (i = 0; i < 7; i++) {
        printf("Ingrese la temperatura del dia %d: ", i + 1);
        scanf("%f", &temperaturas[i]);
    }
}

float calcularPromedio(float temperaturas[]) {
    float suma = 0;
    int i;
    for (i = 0; i < 7; i++) {
        suma += temperaturas[i];
    }
    return suma / 7;
}

int main() {
    float temperaturas[7];
    float promedio;

    leerTemperaturas(temperaturas);
    promedio = calcularPromedio(temperaturas);

    printf("\nPromedio semanal: %.2f\n", promedio);

    if (promedio > 25) {
        printf("Clasificacion: Semana calurosa\n");
    } else {
        printf("Clasificacion: Semana templada\n");
    }

    return 0;
}
```

### 4.5. Ejecución del Programa

*Datos de entrada de ejemplo: 22, 24, 19, 21, 26, 23, 20 → Promedio esperado: 22.14 (Semana templada)*

<p align="center">

<img width="383" height="221" alt="image" src="https://github.com/user-attachments/assets/28bdd5ef-e839-45b3-bfca-cf8ecfeee45d" />


</p>

---

## 💡 5. Principales Dificultades y Reflexión Crítica

### ❌ Principales Dificultades Encontradas

1. **Distinción entre paso por valor y por referencia:** al inicio resultó confuso entender por qué una función podía "no cambiar" una variable del programa principal a pesar de modificarla internamente. Comprender que el paso por valor trabaja sobre una copia en memoria, mientras que el paso por referencia trabaja sobre la dirección original (`&variable` y `*puntero`), fue clave para despejar esta confusión.
2. **Manejo de punteros (`*` y `&`):** la sintaxis de los punteros en C fue uno de los puntos más complejos de la unidad, especialmente diferenciar cuándo se declara un puntero, cuándo se pasa una dirección y cuándo se desreferencia un valor (`*a` vs `&a`).
3. **Anidamiento de ciclos `for` en matrices y arreglos multidimensionales:** trabajar con arreglos de dos y tres dimensiones exigió mayor cuidado en el control de los índices (fila, columna, y en el caso multidimensional, bodega/estante/producto), ya que un error de límites o de orden en los ciclos anidados puede generar accesos incorrectos a memoria o resultados desordenados.
4. **Visualizar un arreglo multidimensional:** a diferencia del vector o la matriz, no es tan sencillo representarlo gráficamente en papel, lo que exigió pensar en términos de "niveles" o "capas" de información en lugar de una sola tabla.
5. **Arreglos como parámetro de función:** entender que en C los arreglos se pasan automáticamente por referencia (no es necesario usar `&` al llamarlos) fue un detalle que costó interiorizar, ya que rompe con la lógica aprendida previamente sobre variables simples.

### 📝 Reflexión Crítica sobre el Aprendizaje

El estudio de la modularidad representa un salto cualitativo en la forma de programar: pasar de escribir código lineal y repetitivo a diseñar soluciones organizadas en bloques reutilizables permite construir programas más grandes, ordenados y fáciles de mantener. Entender la diferencia entre el paso de parámetros por valor y por referencia no es solo un detalle técnico, sino un concepto que determina el control real que una función tiene sobre los datos del programa, lo cual es esencial para evitar efectos secundarios no deseados en aplicaciones más complejas.

De igual manera, el manejo de arreglos —unidimensionales, bidimensionales y multidimensionales— abre la puerta al procesamiento de datos a gran escala, algo indispensable en prácticamente cualquier aplicación real: desde el manejo de calificaciones de un curso hasta la representación de imágenes, tableros de juego o inventarios distribuidos en varias bodegas. Desarrollar el ejercicio integrador, combinando funciones que reciben arreglos con estructuras condicionales, permitió comprobar en la práctica cómo estos conceptos se complementan para resolver un problema completo de forma clara y ordenada. En conjunto, esta unidad refuerza la idea de que programar bien no es solo lograr que el código "funcione", sino diseñarlo de forma modular, eficiente y escalable.


[Regresar](README.md)
