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
```text
Algoritmo ComisionesVentas
    Definir v1, v2, v3, c1, c2, c3, total Como Real
    v1 <- 30000; v2 <- 29000; v3 <- 33000
    c1 <- v1 * 0.04
    c2 <- v2 * 0.04
    c3 <- v3 * 0.04
    total <- c1 + c2 + c3
    Escribir "El total a pagar es:", total
FinAlgoritmo
