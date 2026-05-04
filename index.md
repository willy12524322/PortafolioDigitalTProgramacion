# Portafolio Digital de Aprendizaje - Teoría de la Programación

## 📑 Carátula
| Datos Informativos | Detalle |
| :--- | :--- |
| **Institución** | Universidad Nacional de Loja |
| **Facultad** | Energía, las Industrias y los Recursos Naturales no Renovables |
| **Carrera** | Computación |
| **Asignatura** | Teoría de la Programación |
| **Ciclo** | 1er Ciclo "A" |
| **Docente** | Ing. Lissette Geoconda López Faicán |
| **Estudiante** | Willy Javier Ramírez Medina |
| **Período** | Marzo - Agosto 2026 |

---

## 📂 Unidad 1: Fundamentos de Programación y Estructuras Secuenciales

### 1. Contenidos de la Unidad
En esta unidad introductoria, hemos sentado las bases del pensamiento algorítmico, explorando los pilares fundamentales que permiten transformar un problema complejo del mundo real en una solución computacional eficiente, escalable y estructurada.

*   **Algoritmo y la Lógica Computacional:** Constituye la esencia misma de la informática. Se define como un conjunto ordenado, finito y preciso de operaciones que guían la resolución de una tarea. Durante las clases, hemos enfatizado que un algoritmo de calidad debe poseer tres propiedades críticas:
    *   **Precisión:** Cada paso debe estar claramente definido sin ambigüedades.
    *   **Finitud:** Debe terminar tras un número determinado de pasos[cite: 1].
    *   **Eficiencia:** El enfoque en optimizar el uso de recursos (tiempo de ejecución y memoria), un concepto vital para nuestra formación en la UNL[cite: 1].

*   **Pseudocódigo (Lenguaje de Especificación):** Es una herramienta de diseño de alto nivel que utiliza una mezcla de lenguaje natural con convenciones sintácticas de programación (como `Escribir`, `Leer` o `Asignar`)[cite: 1]. Su importancia radica en que permite al programador concentrarse exclusivamente en la lógica del flujo de datos sin las distracciones de la sintaxis estricta de un compilador[cite: 1]. Actúa como el plano arquitectónico antes de levantar la estructura del código[cite: 1].

*   **Diagrama de Flujo y Simbología ISO:** Es la representación gráfica del algoritmo. Para su elaboración, empleamos una simbología normalizada que permite la comunicación universal entre desarrolladores[cite: 1]:
    *   **Terminal (Óvalo):** Indica los puntos de inicio y fin del programa[cite: 1].
    *   **Proceso (Rectángulo):** Define operaciones aritméticas, asignaciones de valores y manipulaciones de datos internas[cite: 1].
    *   **Entrada/Salida (Trapezoide):** Gestiona la interacción con el usuario, ya sea capturando datos por teclado o mostrando resultados por pantalla[cite: 1].
    *   **Flujo (Flechas):** Determinan la dirección lógica de ejecución, que en esta unidad ha sido estrictamente secuencial[cite: 1].

*   **Prueba de Escritorio (Validación Manual):** Actúa como un proceso de depuración (debugging) preventivo[cite: 1]. Consiste en ejecutar el algoritmo mentalmente o en papel, utilizando una tabla de seguimiento para registrar los cambios en los estados de las variables en cada paso[cite: 1]. Es una práctica académica indispensable para detectar errores de lógica y garantizar la fiabilidad del software antes de ser procesado por el computador[cite: 1].

*   **Lenguajes de Programación y el Ecosistema C:** Hemos iniciado la transición hacia lenguajes de propósito general, específicamente el lenguaje **C**[cite: 1]. A diferencia del pseudocódigo, la implementación en C exige un rigor técnico absoluto:
    *   **Directivas de Preprocesamiento:** El uso de `#include <stdio.h>` para gestionar la entrada y salida estándar[cite: 1].
    *   **Tipado de Datos:** La necesidad de definir si una variable es entera (`int`), decimal (`float`) o de carácter (`char`), optimizando así la gestión de memoria[cite: 1].
    *   **Sintaxis Estricta:** El uso obligatorio de llaves `{}` para delimitar bloques y el punto y coma (`;`) para finalizar sentencias[cite: 1].

*   **Programación por Bloques y Abstracción:** Representa un enfoque pedagógico visual donde la lógica se construye mediante el ensamblaje de piezas gráficas que representan estructuras de control[cite: 1]. 
    *   **Importancia Educativa:** Esta metodología nos ha permitido desarrollar "Pensamiento Computacional"[cite: 1]. Al eliminar el riesgo de errores tipográficos o sintácticos, podemos centrarnos en conceptos abstractos de alto nivel, lo que facilita enormemente la comprensión de la lógica necesaria antes de abordar la codificación textual compleja en proyectos de mayor envergadura[cite: 1].
---

### 2. Ejercicio Práctico: Estructura Secuencial en C

#### 📝 Planteamiento del Problema
Calcular la comisión del 4% para tres vendedores de una concesionaria con ventas de $30,000, $29,000 y $33,000 USD, y determinar el pago total conjunto.

#### 🔍 Análisis del Problema
*   **Entradas:** auto1 = 30000, auto2 = 29000, auto3 = 33000, porcentaje = 0.04
*   **Proceso:** comision = venta * porcentaje.
*   **Salida:** Comisiones individuales y suma total.

#### 📐 Diseño del Algoritmo (Pseudocódigo)
```
Algoritmo ComisionesVentas

    Definir auto1, auto2, auto3, comision1, comision2, comision3, total Como Real
    auto1 <- 30000; auto2 <- 29000; auto3 <- 33000; porcentaje <- 0.04

    comision1 <- auto1 * porcentaje
    comision2 <- auto2 * porcentaje
    comision3 <- auto3 * porcentaje
    total <- comision1 + comision2 + comision3
    Escribir "TOTAL A PAGAR EN CONJUNTO:", total
```

#### 💻 Codificación (Código Fuente en C)
```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    // Variables
    float auto1 = 30000, auto2 = 29000, auto3 = 33000;
    float comision1, comision2, comision3, totalComisiones;
    float porcentaje = 0.04;

    // Proceso
    comision1 = auto1 * porcentaje;
    comision2 = auto2 * porcentaje;
    comision3 = auto3 * porcentaje;

    totalComisiones = comision1 + comision2 + comision3;

    // Salida de datos
    printf("Comisiones de Ventas\n\n");
    printf("Vendedor 1 (Vehiculo 30000$):\n");
    printf("- Porcentaje: 4%%\n");
    printf("- Comision a pagar: %.2f$\n\n", comision1);

    printf("Vendedor 2 (Vehiculo 29000$):\n");
    printf("- Porcentaje: 4%%\n");
    printf("- Comision a pagar: %.2f$\n\n", comision2);

    printf("Vendedor 3 (Vehiculo 33000$):\n");
    printf("- Porcentaje: 4%%\n");
    printf("- Comision a pagar: %.2f$\n\n", comision3);

    printf("TOTAL A PAGAR EN CONJUNTO: %.2f$\n", totalComisiones);

    return 0;
}
```

#### 🧪 Validación (Prueba de Escritorio)
```text
Comisiones de Ventas

Vendedor 1 (Vehiculo 30000$):
- Porcentaje: 4%
- Comision a pagar: 1200.00$

Vendedor 2 (Vehiculo 29000$):
- Porcentaje: 4%
- Comision a pagar: 1160.00$

Vendedor 3 (Vehiculo 33000$):
- Porcentaje: 4%
- Comision a pagar: 1320.00$
```
---
#### 📊 Diseño del Algoritmo (Diagrama de Flujo)
<img width="704" height="1160" alt="Captura" src="https://github.com/user-attachments/assets/d21b34f8-74f2-4f05-ad5e-6e5ee6c10ab3" />

---

### 💡 Principales dificultades y Reflexión
Esta unidad fue bastante rica en conocimiento, aprendí varias cosas sobre cómo programar y he de decir que me gustó bastante aprender la lógica y principios básicos de la programación. Fue un poco difícil el cambio de Pseint a Lenguaje C pero al mismo tiempo fue muy interesante ver como se requiere mayor conocimiento en computación y en códigos para adaptarse a este cambio, al mismo tiempo usar C como código de programación me abrió las puertas a una mayor libertad en la programación, debido a la complejidad del mismo, éste es mucho mas libre a la hora de programar ya que permite ajustar cada detalle lo cual me gusta mucho.
Las actividades que se han ejercido en esta unidad me parecieron muy interesantes y divertidas al momento de programar, ya que me gusta tener que pensar maneras de crear un algoritmo que resuelva un problema específico, y así mismo la optimización del algoritmo.


---

## 📂 Unidad 2
*En espera*

---

## 📂 Unidad 3
*En espera*

---

## 🤖 Declaración de uso de IA Generativa
Para la creación de este portafolio se utilizó **Gemini (Google)** como tutor de acompañamiento para el manejo de **Markdown** en GitHub y como recurso de refuerzo para consolidar los contenidos de programación secuencial trabajados en clase[cite: 1].

---

## 📚 Bibliografía (Formato IEEE)
[1] L. Joyanes Aguilar, *Fundamentos de Programación*, 5.ª ed. México: McGraw-Hill, 2020.[cite: 1]
