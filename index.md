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
En esta unidad hemos explorado los conceptos base que permiten transformar una idea en una solución computacional.

*   **Algoritmo:** Es una secuencia lógica y finita de pasos para resolver un problema.
    *   *Ejemplo:* Pasos para calcular el área de un cuadrado.
*   **Pseudocódigo:** Narrativa técnica similar al lenguaje humano que describe el algoritmo antes de programarlo.
*   **Diagrama de Flujo:** Representación gráfica del algoritmo mediante símbolos estandarizados (inicio, proceso, decisión, fin).
*   **Prueba de Escritorio:** Técnica manual para verificar que la lógica del algoritmo es correcta antes de codificar.
*   **Lenguajes de Programación:** Herramientas (como C) que permiten al computador ejecutar nuestras instrucciones.
*   **Programación por Bloques:** Es una metodología que permite crear software mediante la unión de piezas visuales (bloques) que encajan entre sí. 
    *   *Ventaja:* Permite enfocarse en la **lógica del algoritmo** sin preocuparse por los errores de sintaxis (puntos y coma, paréntesis), facilitando el aprendizaje inicial antes de pasar a lenguajes basados en texto como C.
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
