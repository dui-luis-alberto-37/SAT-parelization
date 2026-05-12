# Paralelización del Problema SAT (NP-Hard) 🚀

Este proyecto implementa una solución paralela para el problema de **Satisfacibilidad Booleana (SAT)** utilizando el lenguaje **C** y la librería de paso de mensajes **MPI**.

## 📝 Descripción del Proyecto
El objetivo es determinar si existe una asignación de valores de verdad que satisfaga una fórmula lógica dada[cite: 1]. Al ser un problema de tipo **NP-Hard**, el tiempo de ejecución crece exponencialmente con el número de variables, por lo que la paralelización es clave para obtener resultados en un tiempo razonable.

## ⚙️ ¿Qué vamos a paralelizar?
El proceso principal a paralelizar es el **espacio de búsqueda de soluciones**. 

*   Una fórmula con $n$ variables tiene $2^n$ combinaciones posibles.
*   En lugar de probar cada combinación secuencialmente, dividiremos este universo de combinaciones en **bloques o grupos**.
*   Cada procesador recibirá un bloque distinto para analizarlo de forma independiente y simultánea.

## 💈 Metodología: El Algoritmo del Barbero
Para gestionar la carga de trabajo entre los procesadores, utilizaremos una adaptación del **Problema del Barbero** bajo una arquitectura de **Maestro-Trabajador (Master-Worker)**:

*   **Proceso Maestro (El Barbero):** Gestiona el estado global del problema. Se encarga de asignar los rangos de combinaciones a los trabajadores y queda a la espera de que alguno encuentre la solución.
*   **Procesos Trabajadores (Los Clientes):** Reciben un segmento específico del problema, realizan el procesamiento intensivo y notifican al maestro si encuentran una combinación que haga verdadera la fórmula.



## 🛠 Tecnologías Utilizadas
*   **Lenguaje C:** Elegido por su eficiencia y control de bajo nivel en el manejo de memoria.
*   **MPI (Message Passing Interface):** Estándar utilizado para la comunicación y coordinación entre los diferentes nodos o núcleos de procesamiento.
