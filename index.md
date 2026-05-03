# Portafolio Digital de Aprendizaje - Teoría de la Programación

## 🎓 Carátula
*   **Institución:** Universidad Nacional de Loja
*   **Facultad:** Energía, las Industrias y los Recursos Naturales no Renovables
*   **Carrera:** Computación
*   **Asignatura:** Teoría de la Programación
*   **Ciclo:** 1er Ciclo
*   **Estudiante:** [Tu Nombre]
*   **Docente:** [Nombre del Docente]
*   **Período Académico:** 2024 - 2025

---

## 📂 Unidad 1: Algoritmos y Estructuras Secuenciales

### 📘 Contenidos Temáticos
1.  **Algoritmo:** Conjunto de pasos lógicos para resolver un problema.
2.  **Pseudocódigo:** Narrativa técnica de los pasos de un algoritmo.
3.  **Diagrama de Flujo:** Representación gráfica de la lógica.
4.  **Lenguaje de Programación:** Herramienta para traducir la lógica a código ejecutable (Lenguaje C).

### 💻 Ejercicio con Estructura Secuencial
**Problema:** Cálculo de comisiones en una concesionaria de vehículos.

#### 1. Planteamiento del problema
Una concesionaria realiza tres ventas (30000, 29000 y 33000 USD). Se requiere calcular la comisión individual del 4% para cada vendedor y el pago total en conjunto.

#### 2. Análisis del problema
*   **Entradas:** Costos de vehículos (`float auto1, auto2, auto3`).
*   **Proceso:** Multiplicar cada costo por 0.04.
*   **Salidas:** Comisiones individuales y suma total (`totalConjunto`).

#### 3. Codificación (Lenguaje C)
```c
#include <stdio.h>

int main() {
    float auto1 = 30000, auto2 = 29000, auto3 = 33000;
    float c1, c2, c3, total;
    
    c1 = auto1 * 0.04;
    c2 = auto2 * 0.04;
    c3 = auto3 * 0.04;
    total = c1 + c2 + c3;

    printf("Total Comisiones: %.2f USD\n", total);
    return 0;
}
