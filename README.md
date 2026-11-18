# Parte P3 — Flow Shop Permutacional (C++17)

## Archivos
- `include/neh.hpp`: heurística NEH y cálculo auxiliar del makespan.
- `include/gantt.hpp`: diagrama de Gantt textual en consola.
- `src/main.cpp`: menú, entrada de datos y medición del tiempo NEH.

## Compilación
Desde la carpeta raíz:
```bash
g++ -std=c++17 -O2 -Wall -Wextra -pedantic src/main.cpp -o flowshop
```
En Windows se puede generar `flowshop.exe`:
```bash
g++ -std=c++17 -O2 -Wall -Wextra -pedantic src/main.cpp -o flowshop.exe
```

## Ejecución
```bash
./flowshop
```
En Windows: `flowshop.exe`.

## Entrada de ejemplo
Instancia de 4 trabajos y 3 máquinas. Ingrese primero `4`, luego `3`, y después las filas:
```text
5 6 4
4 3 5
7 5 6
3 4 3
```
Los trabajos se numeran internamente desde 0 y se muestran desde 1.

## Pasos de NEH
1. Sumar los tiempos de cada trabajo en todas las máquinas.
2. Ordenar de mayor a menor suma.
3. Construir la secuencia insertando cada trabajo en todas las posiciones posibles.
4. Calcular el makespan de cada candidata y conservar la de menor valor.

## Complejidad de esta implementación
Esta versión vuelve a calcular el makespan desde cero para cada inserción candidata. Por tanto, la cota conservadora de la fase de inserciones es **O(n³·m)**. La ordenación inicial cuesta O(n·m + n log n). El plan del grupo menciona O(n²·m), pero esa cota no debe atribuirse a este código sin implementar una evaluación optimizada de inserciones.

## Integración
El proyecto es ejecutable independientemente para que P3 pueda avanzar. Al unirlo con P2, el equipo debe acordar la firma de `makespan.hpp` y reemplazar/unificar `makespanNEH` con la función oficial. Al unirlo con P1, se debe integrar `fuerza_bruta.hpp` y medir ambos algoritmos sobre exactamente las mismas instancias. Los tiempos experimentales deben obtenerse ejecutando el programa; no deben inventarse.
