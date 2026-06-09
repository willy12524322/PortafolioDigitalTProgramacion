# 📂 Unidad 2: Estructuras condicionales y Bucles repetitivos.

---

## 1. Estructuras Condicionales

Las estructuras condicionales permiten bifurcar el flujo de ejecución de un programa basándose en el cumplimiento o no de una condición lógica (evaluación booleana: verdadero o falso).

### Tipos de Estructuras Condicionales
1. **Condicional Simple (`if` / Si):** Ejecuta un bloque de código únicamente si la condición es verdadera.
2. **Condicional Compuesta (`if-else` / Si-Sino):** Ejecuta un bloque de código si la condición es verdadera y un bloque alternativo si es falsa.
3. **Condicional Anidada (`if-else if-else` / Si-Sino-Si):** Permite evaluar múltiples condiciones en cascada de manera secuencial.
4. **Condicional Múltiple (`switch` / Según sea):** Evalúa una variable con base en múltiples casos o valores constantes posibles.

### Estructura en Pseudocódigo

#### Condicional Simple
```pseudocodigo
Si (condición) Entonces
    // Bloque de instrucciones si es verdadero
FinSi

```

#### Condicional Compuesta

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

### Estructura en Diagrama de Flujo (draw.io)

## *[Espacio reservado para insertar tu Diagrama de Flujo de Estructuras Condicionales diseñado en draw.io]*

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

## 3. Ejercicio Integrador (Estructura Condicional y Repetitiva en Lenguaje C)

### 3.1. Planteamiento del Problema

Una empresa de logística requiere un sistema automatizado para gestionar el peso de los paquetes que se cargan en un camión de despacho. El camión tiene una capacidad máxima de carga de **500 kg**. El sistema debe permitir al operario registrar el peso de los paquetes uno por uno de forma continua.

El programa debe cumplir con las siguientes reglas de negocio:

1. Si se ingresa un peso negativo o igual a cero, debe mostrar un mensaje de error y solicitar de nuevo el valor sin acumularlo.
2. Si un paquete individual supera los **150 kg**, el sistema debe rechazarlo inmediatamente por motivos de seguridad industrial (exceso de peso por bulto) y permitir continuar con el siguiente paquete.
3. El proceso de carga finaliza automáticamente en el momento exacto en que la suma de los paquetes aceptados iguale o supere el límite de **500 kg**.
4. Al finalizar, el programa debe desplegar:
* El peso total acumulado final en el camión.
* La cantidad total de paquetes aceptados.
* El promedio de peso de los paquetes aceptados.



### 3.2. Análisis del Problema

* **Datos de Entrada:**
* Peso de cada paquete (`peso` - real/float).


* **Datos de Salida:**
* Peso total acumulado (`peso_total` - real/float).
* Cantidad de paquetes aceptados (`contador_paquetes` - entero/int).
* Promedio de peso (`promedio_peso` - real/float).


* **Variables de Control y Constantes:**
* LÍMITE_CAMION = 500.0 (Constante)
* LÍMITE_PAQUETE = 150.0 (Constante)


* **Proceso Lógico:**
* Se requiere un ciclo repetitivo de tipo `while` o `do-while` que se ejecute mientras `peso_total < 500`.
* Dentro del bucle, se implementa una estructura condicional simple para validar que el peso sea mayor a 0.
* Se anida una estructura condicional compuesta para evaluar si el paquete cumple con la norma de seguridad ($\le 150$ kg) o si es rechazado ($> 150$ kg).
* Si el paquete es válido, se suma al acumulador y se incrementa el contador.



### 3.3. Diseño del Algoritmo (Diagrama de Flujo)

*[Espacio reservado para insertar el Diagrama de Flujo del Ejercicio Integrador diseñado en draw.io]*

### 3.4. Codificación (Código Fuente en C)

```c
#include <stdio.h>

int main() {
    // Declaración de variables e inicialización
    float peso = 0.0;
    float peso_total = 0.0;
    int contador_paquetes = 0;
    float promedio_peso = 0.0;
    
    const float LIMITE_CAMION = 500.0;
    const float LIMITE_PAQUETE = 150.0;

    printf("===================================================\n");
    printf("   SISTEMA DE CONTROL DE CARGA - LOGISTICA S.A.    \n");
    printf("===================================================\n");
    printf("Capacidad maxima del camion: %.2f kg\n", LIMITE_CAMION);
    printf("Peso maximo permitido por paquete: %.2f kg\n\n", LIMITE_PAQUETE);

    // Estructura repetitiva (Ciclo Mientras)
    while (peso_total < LIMITE_CAMION) {
        printf("Ingrese el peso del paquete #%d (en kg): ", contador_paquetes + 1);
        scanf("%f", &peso);

        // Estructura condicional para validar entrada de datos
        if (peso <= 0) {
            printf("[ERROR] El peso debe ser un valor positivo mayor a cero.\n\n");
            continue; // Salta el resto del ciclo y pide un nuevo peso
        }

        // Estructura condicional para reglas de negocio
        if (peso > LIMITE_PAQUETE) {
            printf("[RECHAZADO] El paquete excede los %.2f kg permitidos por seguridad.\n\n", LIMITE_PAQUETE);
        } else {
            // El paquete cumple con todos los criterios y es aceptado
            peso_total += peso;
            contador_paquetes++;
            printf("[ACEPTADO] Peso actual en el camion: %.2f / %.2f kg\n\n", peso_total, LIMITE_CAMION);
        }
    }

    // Cálculo del promedio (Condicional para evitar división por cero si fuera el caso)
    if (contador_paquetes > 0) {
        promedio_peso = peso_total / contador_paquetes;
    }

    // Despliegue de resultados finales
    printf("===================================================\n");
    printf("               RESUMEN DE DESPACHO                 \n");
    printf("===================================================\n");
    printf("Carga total del camion: %.2f kg\n", peso_total);
    printf("Total de paquetes procesados y aprobados: %d\n", contador_paquetes);
    printf("Peso promedio por paquete aceptado: %.2f kg\n", promedio_peso);
    printf("Estado del camion: Listo para salida en ruta.\n");
    printf("===================================================\n");

    return 0;
}

```

### 3.5. Validación (Prueba de Escritorio)

A continuación se presenta la tabla de seguimiento manual del algoritmo simulando una ejecución real con diferentes valores críticos de entrada (valores normales, inválidos y límites).

| Paso | Variable `peso` (Entrada) | Condición (`peso <= 0`) | Condición (`peso > 150`) | Condición Bucle (`peso_total < 500`) | Acumulador `peso_total` | Contador `contador_paquetes` | Salida en Pantalla / Estado |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 0 | - | - | - | $0.0 < 500.0$ (Verdadero) | 0.0 | 0 | Inicialización del programa |
| 1 | 120.0 | Falso | Falso | $120.0 < 500.0$ (Verdadero) | 120.0 | 1 | [ACEPTADO] Carga: 120.0 kg |
| 2 | -10.0 | Verdadero | - | $120.0 < 500.0$ (Verdadero) | 120.0 | 1 | [ERROR] Valor inválido |
| 3 | 180.0 | Falso | Verdadero | $120.0 < 500.0$ (Verdadero) | 120.0 | 1 | [RECHAZADO] Excede límite |
| 4 | 140.0 | Falso | Falso | $260.0 < 500.0$ (Verdadero) | 260.0 | 2 | [ACEPTADO] Carga: 260.0 kg |
| 5 | 110.0 | Falso | Falso | $370.0 < 500.0$ (Verdadero) | 370.0 | 3 | [ACEPTADO] Carga: 370.0 kg |
| 6 | 135.0 | Falso | Falso | $505.0 < 500.0$ (Falso) | 505.0 | 4 | [ACEPTADO] Fin del ciclo |

**Resultados calculados post-ciclo:**

* `promedio_peso` = $505.0 / 4 = 126.25$ kg.

---

## 4. Principales Dificultades y Reflexión Crítica

### Principales Dificultades Encontradas

1. **Lógica de Validación de Datos de Entrada:** Al principio, el diseño permitía que valores erróneos (como pesos negativos) incrementaran el contador o alteraran el flujo lógico. Se solventó implementando la sentencia de salto controlado `continue` combinada con condicionales anidadas.
2. **Control Extremo de Ciclos:** Sincronizar el momento exacto en el que la carga alcanza los 500 kg sin generar bucles infinitos requirió un análisis riguroso de los operadores relacionales de comparación (`<` vs `<=`).
3. **Manejo de Tipos de Datos:** El cálculo del promedio requirió una gestión estricta de variables de tipo flotante (`float`) para evitar pérdidas de precisión matemática e impedir errores de división por cero mediante filtros de exclusión preventiva.

### Reflexión Crítica sobre el Aprendizaje

El estudio y aplicación práctica de las estructuras condicionales y repetitivas constituye la piedra angular del desarrollo de software estructurado y la resolución algorítmica de problemas. Estas estructuras permiten transformar un código estático y lineal en un sistema inteligente, dinámico y capaz de tomar decisiones autónomas basadas en datos en tiempo real.

La integración de herramientas como **draw.io** para el modelado visual junto con la codificación en **lenguaje C** ayuda a cerrar la brecha entre el pensamiento conceptual-analítico y la implementación tecnológica rígida. Diseñar un algoritmo robusto nos enseña que la programación no se limita a escribir sintaxis, sino a prever comportamientos, estructurar soluciones eficientes y blindar los sistemas contra fallas mediante validaciones exhaustivas. Este aprendizaje consolida mi perfil técnico al aportarme un enfoque lógico, modular y altamente estructurado para resolver problemas complejos de la ingeniería de software en mi futuro formativo y profesional.

```

```
