# 📂 Unidad 2: Estructuras condicionales y Bucles repetitivos.

## 1. Estructuras Condicionales

Las estructuras condicionales permiten bifurcar el flujo de ejecución de un programa basándose en el cumplimiento o no de una condición lógica (evaluación booleana: verdadero o falso).

### Tipos de Estructuras Condicionales
1. **Condicional Simple (`if` / Si):** Ejecuta un bloque de código únicamente si la condición es verdadera.
2. **Condicional Compuesta (`if-else` / Si-Sino):** Ejecuta un bloque de código si la condición es verdadera y un bloque alternativo si es falsa.
3. **Condicional Anidada (`if-else if-else` / Si-Sino-Si):** Permite evaluar múltiples condiciones en cascada de manera secuencial.
4. **Condicional Múltiple (`switch` / Según sea):** Evalúa una variable con base en múltiples casos o valores constantes posibles.


### Condicional Simple
#### Pseudocódigo
```pseudocodigo
Si (condición) Entonces
    // Bloque de instrucciones si es verdadero
FinSi

```

#### Diagrama de Flujo
<img width="520" height="346" alt="image" src="https://github.com/user-attachments/assets/3e75be79-71a6-452a-9e3d-9fd037c9322e" />

### Condicional Compuesta
#### Pseudocódigo
```pseudocodigo
Si (condición) Entonces
    // Bloque de instrucciones si es verdadero
Sino
    // Bloque de instrucciones si es falso
FinSi

```

#### Condicional Anidada

```pseudocodigo
Si (condición_1) Entonces
    // Instrucciones 1
Sino Si (condición_2) Entonces
    // Instrucciones 2
Sino
    // Instrucciones por defecto
FinSi

```

#### Condicional Múltiple

```pseudocodigo
Según (variable) Hacer
    Caso valor_1:
        // Instrucciones 1
        Interrumpir
    Caso valor_2:
        // Instrucciones 2
        Interrumpir
    De Otro Modo:
        // Instrucciones por defecto
FinSegún

```


## 2. Estructuras Repetitivas

Las estructuras repetitivas (bucles o ciclos) permiten ejecutar un bloque de instrucciones múltiples veces de forma controlada. La repetición se mantiene mientras una condición lógica sea verdadera.

### Tipos de Estructuras Repetitivas

1. **Ciclo Mientras (`while`):** Evalúa la condición al inicio. Si es falsa desde el principio, el bloque de código nunca se ejecuta.
2. **Ciclo Hacer-Mientras (`do-while`):** Evalúa la condición al final. Garantiza que el bloque de código se ejecute al menos una vez.
3. **Ciclo Para (`for`):** Estructura diseñada para repetir un bloque de código un número determinado de veces, integrando inicialización, condición e incremento en una sola línea.

### Estructura en Pseudocódigo

#### Ciclo Mientras

```pseudocodigo
Mientras (condición) Hacer
    // Bloque de instrucciones a repetir
    // Modificación de la variable de control
FinMientras

```

#### Ciclo Hacer-Mientras

```pseudocodigo
Hacer
    // Bloque de instrucciones a repetir
    // Modificación de la variable de control
Mientras (condición)

```

#### Ciclo Para

```pseudocodigo
Para variable_control <- valor_inicial Hasta valor_final Con Paso incremento Hacer
    // Bloque de instrucciones a repetir
FinPara

```

### Estructura en Diagrama de Flujo (draw.io)

## *[Espacio reservado para insertar tu Diagrama de Flujo de Estructuras Repetitivas diseñado en draw.io]*

## 🚀 3. Ejercicio Integrador (Estructura Condicional y Repetitiva en Lenguaje C)

### 3.1. Planteamiento del Problema

Se requiere desarrollar un sistema de control de acceso básico para una plataforma informática. El programa debe solicitar al usuario un código único de acceso.

El programa debe cumplir con las siguientes **reglas de negocio**:

* El código correcto y único de acceso es `1234`.
* Si el usuario ingresa el código incorrecto, el sistema le otorgará un máximo de 2 intentos adicionales para corregirlo.
* El ciclo de solicitud se repetirá **mientras** el código ingresado sea incorrecto **y** el usuario aún disponga de intentos.
* Si el usuario agota los intentos sin ingresar la clave correcta, se mostrará un mensaje de denegación solicitando que lo intente en otro momento.
* Si introduce el código correcto en cualquiera de las oportunidades, se le otorgará un mensaje de bienvenida y se dará acceso al sistema.

### 3.2. Análisis del Problema

* **Datos de Entrada:**
* Código de acceso ingresado por el usuario (`codigo` - entero/int).


* **Datos de Salida:**
* Mensaje de éxito/bienvenida o mensaje de error/bloqueo por pantalla.


* **Variables de Control y Constantes:**
* `intentos` = 2 (Variable entera contador/decremental).
* Clave esperada implicitamente = `1234`.


* **Proceso Lógico:**
1. Se solicita el primer código de acceso en la entrada general.
2. Se evalúa un ciclo repetitivo `while` con la condición compuesta: `codigo != 1234 && intentos > 0`.
3. Dentro del ciclo, se notifica el error, se reduce la variable `intentos` en 1 unidad y se vuelve a leer el código.
4. Al salir del bucle, se valida mediante una estructura condicional compuesta `if-else` si la salida fue por intentos agotados (`codigo != 1234`) o por éxito, mostrando el resultado correspondiente.



### 3.3. Diseño del Algoritmo (Diagrama de Flujo)

> 🗺️ **[Espacio reservado para insertar el Diagrama de Flujo del Ejercicio Integrador diseñado en draw.io]**

### 3.4. Codificación (Código Fuente en C)

```c
#include <stdio.h>

int main() {
    // Definición de variables
    int codigo, intentos = 2; 

    // Entrada
    printf("Bienvenido usuario, por favor ingrese codigo de acceso unico\n");
    scanf("%i", &codigo);

    // Proceso
    while (codigo != 1234 && intentos > 0) {
        printf("codigo incorrecto, tiene %i intentos restantes\n", intentos);
        intentos--;
        scanf("%i", &codigo);
    } 

    if (codigo != 1234) {
        printf(" Codigo incorrecto, Intentelo nuevamente en otro momento \n");
    } else {
        // Salida
        printf("Codigo correcto, bienvenido usuario\n ");
    }

    return 0;
}

```

### 3.5. Validación (Prueba de Escritorio)

A continuación se presenta la simulación del comportamiento del algoritmo recreando dos escenarios típicos de ejecución (Acceso fallido y Acceso exitoso al segundo intento).

| Paso | Variable `codigo` (Entrada) | Variable `intentos` | Condición Bucle (`codigo!=1234 && intentos>0`) | Condición Final (`codigo != 1234`) | Salida en Pantalla / Estado |
| --- | --- | --- | --- | --- | --- |
| **Caso 1: Clave Incorrecta (Bloqueo)** |  |  |  |  |  |
| **0** | --- | 2 | --- | --- | Inicialización de variables |
| **1** | 9999 | 2 | V && V (Verdadero) | --- | "Bienvenido usuario..." -> Ingresa 9999 |
| **2** | --- | 1 | --- | --- | "codigo incorrecto, tiene 2 intentos..." -> Disminuye intento |
| **3** | 8888 | 1 | V && V (Verdadero) | --- | Lee nuevo código: 8888 |
| **4** | --- | 0 | --- | --- | "codigo incorrecto, tiene 1 intentos..." -> Disminuye intento |
| **5** | 7777 | 0 | V && F (Falso) | --- | Lee nuevo código: 7777 -> Rompe Bucle |
| **6** | --- | 0 | --- | Verdadero | Evalúa IF -> "Codigo incorrecto, Intentelo nuevamente..." |
| **Caso 2: Clave Correcta al reintento** |  |  |  |  |  |
| **1** | 5555 | 2 | V && V (Verdadero) | --- | Lee 5555. Entra al bucle. |
| **2** | --- | 1 | --- | --- | "codigo incorrecto..." -> Baja intentos a 1 |
| **3** | 1234 | 1 | F && V (Falso) | --- | Lee nuevo código: 1234 -> Rompe Bucle |
| **4** | --- | 1 | --- | Falso | Evalúa IF (Falso) -> Salta al ELSE -> "Codigo correcto..." |

---

## 🧠 4. Principales Dificultades y Reflexión Crítica

### ❌ Principales Dificultades Encontradas

1. **Lógica de Condición Compuesta en Bucles:** El manejo de operadores lógicos relacionales y booleanos (operador `&&`) requirió un análisis preciso, asegurando que el ciclo terminara inmediatamente si cualquiera de las dos condiciones dejaba de cumplirse.
2. **Sincronización del Decremento y Lectura:** Controlar el orden en el que se reduce el contador (`intentos--`) y el momento en el que el usuario digita el nuevo dato fue clave para evitar desfasar el número real de intentos mostrados en los mensajes informativos.
3. **Validación del Estado Post-Bucle:** Comprender que al salir del ciclo se requiere una condicional extra (`if (codigo != 1234)`) para discernir exactamente el motivo de la salida (si fue por código exitoso final o por agotamiento de intentos).

### 📝 Reflexión Crítica sobre el Aprendizaje

El estudio y aplicación práctica de las estructuras condicionales y repetitivas constituye la piedra angular del desarrollo de software estructurado y la resolución algorítmica de problemas. Estas estructuras permiten transformar un código estático y lineal en un sistema inteligente, dinámico y capaz de tomar decisiones autónomas basadas en datos en tiempo real.

La integración de herramientas como draw.io para el modelado visual junto con la codificación en lenguaje C ayuda a cerrar la brecha entre el pensamiento conceptual-analítico y la implementación tecnológica rígida. Diseñar un algoritmo robusto nos enseña que la programación no se limita a escribir sintaxis, sino a prever comportamientos, estructurar soluciones eficientes y blindar los sistemas contra fallas mediante validaciones exhaustivas. Este aprendizaje consolida mi perfil técnico al aportarme un enfoque lógico, modular y altamente estructurado para resolver problemas complejos de la ingeniería de software en mi futuro formativo y profesional.

```

```
