[Regresar](README.md)
# 📂 Unidad 3: Modularidad y Arreglos

### 1. Contenidos de la Unidad
En esta unidad avanzamos de la programación estructurada secuencial y condicional hacia un enfoque más robusto y escalable: la **modularidad**. Aprendimos a fragmentar problemas complejos en subprogramas (funciones) independientes y reutilizables, así como a manejar colecciones de datos homogéneas mediante **arreglos** (vectores y matrices), fundamentales para el procesamiento de grandes volúmenes de información.

---

## 🧩 2. Modularidad

La modularidad es un principio de diseño de software que consiste en dividir un programa extenso en partes más pequeñas, independientes y con una función específica, llamadas **funciones** o **subprogramas**. Cada función recibe datos de entrada (parámetros), ejecuta un proceso interno y puede o no devolver un resultado.

**Ventajas principales:**
* **Reutilización de código:** una misma función puede invocarse múltiples veces desde distintos puntos del programa.
* **Abstracción:** quien usa la función no necesita conocer su implementación interna, solo su propósito.
* **Mantenibilidad:** facilita la depuración, ya que los errores quedan aislados dentro de bloques concretos.
* **Trabajo en equipo:** permite que distintas personas desarrollen módulos diferentes del mismo sistema de forma simultánea.

Un aspecto crítico de la modularidad es la forma en la que los datos "viajan" entre el programa principal (`main`) y las funciones, lo cual se conoce como **paso de parámetros**.

### 2.1. Paso de Parámetros por Valor

Cuando un parámetro se pasa **por valor**, la función recibe una **copia** del dato original. Cualquier modificación que se realice sobre esa copia dentro de la función **no afecta** a la variable original del programa que la invocó.

#### 📝 Planteamiento del Problema
Calcular el IVA (15%) de un producto sin alterar el precio original almacenado en el programa principal.

#### 📐 Pseudocódigo
```
Funcion iva <- calcularIVA(precio)
    iva <- precio * 0.15
    precio <- precio + iva      // Solo modifica la copia local
    Retornar iva
FinFuncion

Algoritmo Principal
    Definir precioProducto, ivaCalculado Como Real
    precioProducto <- 100.00
    ivaCalculado <- calcularIVA(precioProducto)
    Escribir "Precio original:", precioProducto
    Escribir "IVA calculado:", ivaCalculado
```

#### 💻 Codificación (Código Fuente en C)
```c
#include <stdio.h>

float calcularIVA(float precio) {
    float iva;
    iva = precio * 0.15;      // 15% de IVA
    precio = precio + iva;    // Solo modifica la copia local de la funcion
    return iva;
}

int main() {
    float precioProducto = 100.00;
    float ivaCalculado;

    ivaCalculado = calcularIVA(precioProducto);

    printf("Precio original (en main): %.2f$\n", precioProducto);
    printf("IVA calculado (15%%): %.2f$\n", ivaCalculado);
    printf("Precio final con IVA (solo dentro de la funcion): %.2f$\n", precioProducto + ivaCalculado);

    return 0;
}
```

#### 🧪 Validación (Prueba de Escritorio)

| Paso | Instrucción / Acción | precioProducto (main) | precio (copia local, función) | iva | ivaCalculado | Salida por Pantalla |
| :--- | :--- | :---: | :---: | :---: | :---: | :--- |
| 1 | Inicio del programa | - | - | - | - | (Ejecución iniciada) |
| 2 | Asignación de entrada | 100.00 | - | - | - | - |
| 3 | Llamada a `calcularIVA(precioProducto)` | 100.00 | 100.00 (copia) | - | - | - |
| 4 | Cálculo `iva = precio * 0.15` | 100.00 | 100.00 | 15.00 | - | - |
| 5 | `precio = precio + iva` (solo local) | 100.00 | 115.00 | 15.00 | - | - |
| 6 | `Retornar iva` (fin de función) | 100.00 | *(destruida)* | 15.00 | 15.00 | - |
| 7 | Impresión de resultados | 100.00 | - | 15.00 | 15.00 | **Precio original: 100.00$ / IVA: 15.00$** |

> 💡 Nótese que `precioProducto` en `main` **nunca cambia**, aunque `precio` sí se modificó dentro de la función: son variables distintas, ubicadas en espacios de memoria distintos.

<!-- Sugerencia: aquí puedes insertar tu diagrama de flujo exportado desde Photopea, siguiendo el mismo formato de imagen usado en las Unidades 1 y 2 -->

---

### 2.2. Paso de Parámetros por Referencia

Cuando un parámetro se pasa **por referencia**, en lugar de enviar una copia del valor, se envía la **dirección de memoria** (mediante punteros, `*` y `&`) de la variable original. Esto permite que la función modifique directamente el valor original ubicado en `main`.

#### 📝 Planteamiento del Problema
Intercambiar (swap) el contenido de dos variables numéricas ingresadas por el usuario.

#### 📐 Pseudocódigo
```
Funcion intercambiar(Ref a, Ref b)
    Definir temp Como Entero
    temp <- a
    a <- b
    b <- temp
FinFuncion

Algoritmo Principal
    Definir numero1, numero2 Como Entero
    numero1 <- 5; numero2 <- 10
    Escribir "Antes:", numero1, numero2
    intercambiar(numero1, numero2)
    Escribir "Despues:", numero1, numero2
```

#### 💻 Codificación (Código Fuente en C)
```c
#include <stdio.h>

void intercambiar(int *a, int *b) {
    int temp;
    temp = *a;
    *a = *b;
    *b = temp;
}

int main() {
    int numero1 = 5, numero2 = 10;

    printf("Antes del intercambio: numero1 = %d, numero2 = %d\n", numero1, numero2);

    intercambiar(&numero1, &numero2);

    printf("Despues del intercambio: numero1 = %d, numero2 = %d\n", numero1, numero2);

    return 0;
}
```

#### 🧪 Validación (Prueba de Escritorio)

| Paso | Instrucción / Acción | numero1 (main) | numero2 (main) | \*a (apunta a numero1) | \*b (apunta a numero2) | temp | Salida por Pantalla |
| :--- | :--- | :---: | :---: | :---: | :---: | :---: | :--- |
| 1 | Inicio del programa | - | - | - | - | - | (Ejecución iniciada) |
| 2 | Asignación de entradas | 5 | 10 | - | - | - | - |
| 3 | Impresión inicial | 5 | 10 | - | - | - | "Antes: numero1 = 5, numero2 = 10" |
| 4 | Llamada `intercambiar(&numero1, &numero2)` | 5 | 10 | 5 | 10 | - | - |
| 5 | `temp = *a` | 5 | 10 | 5 | 10 | 5 | - |
| 6 | `*a = *b` (modifica numero1 directamente) | **10** | 10 | 10 | 10 | 5 | - |
| 7 | `*b = temp` (modifica numero2 directamente) | 10 | **5** | 10 | 5 | 5 | - |
| 8 | Fin de la función / impresión final | 10 | 5 | - | - | - | **"Despues: numero1 = 10, numero2 = 5"** |

> 💡 A diferencia del ejemplo anterior, aquí `numero1` y `numero2` **sí cambian** en `main`, porque la función trabajó directamente sobre sus direcciones de memoria (`&numero1`, `&numero2`).

<!-- Sugerencia: aquí puedes insertar tu diagrama de flujo exportado desde Photopea -->

---

## 📊 3. Arreglos

Un **arreglo** (array) es una estructura de datos que permite almacenar una colección de elementos **del mismo tipo**, bajo un único nombre de variable, accediendo a cada uno mediante un índice numérico (que en C inicia en `0`). Su uso es fundamental cuando se necesita procesar conjuntos de datos relacionados (notas, precios, coordenadas, etc.) sin declarar una variable independiente para cada valor.

### Tipos de Arreglos

1. **Arreglo Unidimensional (Vector):** estructura lineal de una sola fila de datos, accedida mediante un solo índice `arreglo[i]`.
2. **Arreglo Bidimensional (Matriz):** estructura de filas y columnas, accedida mediante dos índices `arreglo[i][j]`, útil para representar tablas, cuadrículas o datos matriciales.

### 3.1. Arreglo Unidimensional (Vector)

#### 📝 Planteamiento del Problema
Leer las 5 notas de un estudiante, almacenarlas en un vector y calcular el promedio del curso.

#### 📐 Pseudocódigo
```
Algoritmo PromedioNotas
    Definir notas Como Real
    Dimension notas[5]
    Definir suma, promedio Como Real
    suma <- 0

    Para i <- 0 Hasta 4 Con Paso 1 Hacer
        Leer notas[i]
        suma <- suma + notas[i]
    FinPara

    promedio <- suma / 5
    Escribir "El promedio del curso es:", promedio
```

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

#### 🧪 Validación (Prueba de Escritorio)

*Entradas de ejemplo: 8.5, 7.0, 9.2, 6.5, 10.0*

| Paso | i | notas[i] ingresada | suma (acumulada) | Salida por Pantalla |
| :--- | :---: | :---: | :---: | :--- |
| 1 | 0 | 8.5 | 8.5 | "Ingrese la nota 1:" |
| 2 | 1 | 7.0 | 15.5 | "Ingrese la nota 2:" |
| 3 | 2 | 9.2 | 24.7 | "Ingrese la nota 3:" |
| 4 | 3 | 6.5 | 31.2 | "Ingrese la nota 4:" |
| 5 | 4 | 10.0 | 41.2 | "Ingrese la nota 5:" |
| 6 | Fin de ciclo | - | 41.2 | promedio = 41.2 / 5 = **8.24** |
| 7 | Impresión final | - | - | - | **"El promedio del curso es: 8.24"** |

<!-- Sugerencia: aquí puedes insertar tu diagrama de flujo exportado desde Photopea -->

---

### 3.2. Arreglo Bidimensional (Matriz)

#### 📝 Planteamiento del Problema
Leer dos matrices de 2x2, sumarlas elemento a elemento y mostrar la matriz resultante.

#### 📐 Pseudocódigo
```
Algoritmo SumaMatrices
    Definir matrizA, matrizB, matrizSuma Como Entero
    Dimension matrizA[2,2], matrizB[2,2], matrizSuma[2,2]

    Para i <- 0 Hasta 1 Con Paso 1 Hacer
        Para j <- 0 Hasta 1 Con Paso 1 Hacer
            Leer matrizA[i,j]
        FinPara
    FinPara

    Para i <- 0 Hasta 1 Con Paso 1 Hacer
        Para j <- 0 Hasta 1 Con Paso 1 Hacer
            Leer matrizB[i,j]
        FinPara
    FinPara

    Para i <- 0 Hasta 1 Con Paso 1 Hacer
        Para j <- 0 Hasta 1 Con Paso 1 Hacer
            matrizSuma[i,j] <- matrizA[i,j] + matrizB[i,j]
        FinPara
    FinPara

    Escribir "Matriz resultante:", matrizSuma
```

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

#### 🧪 Validación (Prueba de Escritorio)

*Entradas de ejemplo: Matriz A = [[1,2],[3,4]] — Matriz B = [[5,6],[7,8]]*

| Paso | Instrucción / Acción | matrizA | matrizB | matrizSuma | Salida por Pantalla |
| :--- | :--- | :---: | :---: | :---: | :--- |
| 1 | Lectura completa de Matriz A | [1,2],[3,4] | - | - | "Ingrese los 4 elementos de la Matriz A" |
| 2 | Lectura completa de Matriz B | [1,2],[3,4] | [5,6],[7,8] | - | "Ingrese los 4 elementos de la Matriz B" |
| 3 | `matrizSuma[0][0] = 1+5` | [1,2],[3,4] | [5,6],[7,8] | [6,-],[-,-] | - |
| 4 | `matrizSuma[0][1] = 2+6` | [1,2],[3,4] | [5,6],[7,8] | [6,8],[-,-] | - |
| 5 | `matrizSuma[1][0] = 3+7` | [1,2],[3,4] | [5,6],[7,8] | [6,8],[10,-] | - |
| 6 | `matrizSuma[1][1] = 4+8` | [1,2],[3,4] | [5,6],[7,8] | [6,8],[10,12] | - |
| 7 | Impresión de la matriz resultante | - | - | [6,8],[10,12] | **"6  8" / "10  12"** |

<!-- Sugerencia: aquí puedes insertar tu diagrama de flujo exportado desde Photopea -->

---

## 💡 4. Principales Dificultades y Reflexión Crítica

### ❌ Principales Dificultades Encontradas

1. **Distinción entre paso por valor y por referencia:** al inicio resultó confuso entender por qué una función podía "no cambiar" una variable del programa principal a pesar de modificarla internamente. Comprender que el paso por valor trabaja sobre una copia en memoria, mientras que el paso por referencia trabaja sobre la dirección original (`&variable` y `*puntero`), fue clave para despejar esta confusión.
2. **Manejo de punteros (`*` y `&`):** la sintaxis de los punteros en C fue uno de los puntos más complejos de la unidad, especialmente diferenciar cuándo se declara un puntero, cuándo se pasa una dirección y cuándo se desreferencia un valor (`*a` vs `&a`).
3. **Anidamiento de ciclos `for` en matrices:** trabajar con arreglos bidimensionales exigió mayor cuidado en el control de los índices `i` (filas) y `j` (columnas), ya que un error de límites o de orden en los ciclos anidados puede generar accesos incorrectos a memoria o resultados desordenados.
4. **Inicialización y recorrido de arreglos:** recordar que los índices en C inician en `0` y no en `1` fue un detalle que requirió atención constante para evitar errores de desbordamiento (*off-by-one*).

### 📝 Reflexión Crítica sobre el Aprendizaje

El estudio de la modularidad representa un salto cualitativo en la forma de programar: pasar de escribir código lineal y repetitivo a diseñar soluciones organizadas en bloques reutilizables permite construir programas más grandes, ordenados y fáciles de mantener. Entender la diferencia entre el paso de parámetros por valor y por referencia no es solo un detalle técnico, sino un concepto que determina el control real que una función tiene sobre los datos del programa, lo cual es esencial para evitar efectos secundarios no deseados en aplicaciones más complejas.

De igual manera, el manejo de arreglos —tanto unidimensionales como bidimensionales— abre la puerta al procesamiento de datos a gran escala, algo indispensable en prácticamente cualquier aplicación real: desde el manejo de calificaciones de un curso hasta la representación de imágenes o tableros de juego mediante matrices. Combinar ambos conceptos (funciones que reciben arreglos, por ejemplo) sienta las bases para las siguientes unidades del curso, donde la complejidad de los programas seguirá incrementando. En conjunto, esta unidad refuerza la idea de que programar bien no es solo lograr que el código "funcione", sino diseñarlo de forma modular, eficiente y escalable.

---

## 📚 Bibliografía de la Unidad

[1] L. Joyanes Aguilar, *Fundamentos de Programación*, 5.ª ed. México: McGraw-Hill, 2020.

[2] J. E. Guerra Salazar, M. V. Ramos Valencia, and G. E. Vallejo Vallejo, *Programando en C desde la práctica: problemas resueltos*. Puerto Madero Editorial, 2023. [En línea]. Disponible: https://dialnet.unirioja.es/servlet/libro?codigo=933288

[3] A. A. Bhuiyan and M. Amiruzzaman, *Programming with Java*, 2nd ed. The Pennsylvania Alliance for Design of Open Textbooks (PA-ADOPT), 2025. [En línea]. Disponible: https://open.umn.edu/opentextbooks/textbooks/programming-with-java
