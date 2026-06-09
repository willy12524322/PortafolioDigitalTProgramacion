content = """# 📑 Unidad 2: Estructuras Repetitivas en la Resolución de Problemas

Este espacio recopila las actividades prácticas, el diseño lógico, la codificación y la validación de software desarrollados en la Unidad 2, enfocados en la transición de la programación secuencial hacia la lógica iterativa o cíclica.

---

## 📂 1. Desarrollo del Contenido Temático (Conceptos Clave)

Las estructuras repetitivas (también conocidas como bucles o ciclos) son estructuras de control que permiten ejecutar un bloque de instrucciones de forma cíclica mientras una determinada condición lógica se mantenga como verdadera. A diferencia de las estructuras secuenciales (que se ejecutan una sola vez y finalizan), los bucles optimizan el código al reutilizar las mismas líneas para procesar múltiples conjuntos de datos.

### 🔄 Tipos de Estructuras Repetitivas Utilizadas

* **Bucle `while` (Pre-prueba):** Evalúa la condición lógica *antes* de ingresar al ciclo. Si la condición es falsa desde el primer instante, el bloque de código nunca se ejecuta. En esta práctica, se utilizó como el núcleo principal para procesar una cantidad dinámica de estudiantes y para los minibucles internos de validación de rangos.
* **Bucle `do...while` (Post-prueba):** Ejecuta el bloque de instrucciones al menos una vez antes de evaluar la condición. Es ideal para la construcción de menús interactivos.
* **Bucle `for` (Controlado por Contador):** Diseñado para escenarios donde se conoce con exactitud el número de iteraciones antes de iniciar la ejecución del bucle.

---

## 🛠️ 2. Evidencia Práctica: Caso Computacional Realizado

Como eje de aplicación práctica, se tomó como base el ejercicio lineal previo denominado `NotaUnidad.c` (el cual solo procesaba los datos de un único estudiante) y se lo reestructuró por completo usando bucles cíclicos independientes y un contador progresivo ascendente.

### 📝 Código Fuente Implementado (`NotaUnidad_Repetitivo.c`)
