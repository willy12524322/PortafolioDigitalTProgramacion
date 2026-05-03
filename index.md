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
| **Estudiante** | Willy Ramírez |
| **Período** | 2026 Primer Período cadémico |

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

---

### 2. Ejercicio Práctico: Estructura Secuencial en C

#### 📝 Planteamiento del Problema
Calcular la comisión del 4% para tres vendedores de una concesionaria con ventas de $30,000, $29,000 y $33,000 USD, y determinar el pago total conjunto.

#### 🔍 Análisis del Problema
*   **Entradas:** `v1 = 30000`, `v2 = 29000`, `v3 = 33000`.
*   **Proceso:** `comision = venta * 0.04`.
*   **Salida:** Comisiones individuales y suma total.

#### 📐 Diseño del Algoritmo (Pseudocódigo)

Algoritmo ComisionesVentas
    Definir auto1, auto2, auto3, comision1, comision2, comision3, total Como Real
    auto1 <- 30000; auto2 <- 29000; auto3 <- 33000
    comision1 <- v1 * 0.04
    comision2 <- v2 * 0.04
    comision3 <- v3 * 0.04
    total <- c1 + c2 + c3
    Escribir "El total a pagar es:", total
FinAlgoritmo

#### 💻 Codificación (Código Fuente en C)
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

#### 🧪 Validación (Prueba de Escritorio)
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

---

### 💡 Principales dificultades y Reflexión
Como conclusión de esta unidad, la mayor dificultad fue adaptar la lógica del pseudocódigo a la sintaxis del lenguaje C, especialmente el uso correcto de los especificadores de formato (`%.2f`) para los decimales. Esta actividad me permitió comprender cómo las estructuras secuenciales son la base para resolver problemas financieros de manera automática y precisa.

---

## 📂 Unidad 2
*Contenido disponible próximamente.*

---

## 📂 Unidad 3
*Contenido disponible próximamente.*

---

## 🤖 Declaración de uso de IA Generativa
Para la creación de este portafolio se utilizó **Gemini (Google)** como tutor de acompañamiento para el manejo de **Markdown** en GitHub y como recurso de refuerzo para consolidar los contenidos de programación secuencial trabajados en clase[cite: 1].

---

## 📚 Bibliografía (Formato IEEE)
[1] L. Joyanes Aguilar, *Fundamentos de Programación*, 5.ª ed. México: McGraw-Hill, 2020.[cite: 1]
