# Advent of Code 2025 — Día 9: Movie Theater

## Componentes del grupo 

- Paula Cárcel Vercher
- Ánegal Sal Golnzalez
- Sara Beses Martinez
- Mar Real Osca 

## Descripción del problema

El reto consiste en encontrar el rectángulo más grande que se puede formar en un suelo de baldosas, usando dos baldosas rojas como esquinas opuestas. En la Parte 2, el rectángulo solo puede incluir baldosas rojas o verdes (las verdes forman un bucle conectando las rojas y rellenan el interior).

Ejemplo visual del enunciado:
```
..............
.......#...#..
..............
..#....#......
..............
..#......#....
..............
.........#.#..
..............
```

Objetivo:

- Parte 1: Mayor área con esquinas rojas.
- Parte 2: Mayor área con esquinas rojas y resto del rectángulo solo rojo/verde.

---

## Justificación de la elección

Este problema es ideal para aplicar geometría computacional en rejillas ortogonales:

- Permite usar técnicas como ray casting y validación de intersecciones.
- Requiere eficiencia y claridad en el diseño.

---

## Descripción técnica

1. Lectura del input: coordenadas `x,y` de baldosas rojas.
2. Construcción del contorno: aristas separadas en verticales y horizontales.
3. Generación de candidatos: todas las parejas de baldosas rojas.
4. Validaciones:
    - Centro dentro o en el borde del polígono.
    - Sin aristas atravesando el interior.
5. Poda por área para mejorar eficiencia.

Funciones principales:

- `leer_puntos()`: carga y valida el input.
- `construir_aristas()`: genera aristas y las clasifica.
- `punto_dentro_o_borde()`: ray casting.
- `tiene_cruce_interior()`: evita rectángulos inválidos.
- `calcular_mejor_area()`: busca el área máxima.

---

## Alternativas descartadas

- Fuerza bruta por celdas → demasiado costosa.
- Intersección general de segmentos → innecesaria (aristas ortogonales).
- Solo vértices adyacentes → pierde soluciones óptimas.

---

## Complejidad y eficiencia

- Emparejar puntos: O(n²).
- Validaciones: O(V+H) por candidato.
- Optimizaciones: separación vertical/horizontal y poda por área.

---

## Corrección y pruebas

- Entrada inválida → mensaje de error.
- Menos de 2 puntos → salida 0.
- Casos del enunciado reproducidos correctamente.

Resultados:

- Parte 1: `Área máxima: 4769758290`.
- Parte 2: `Área máxima: 1588990708`.

---

## Cómo compilar y ejecutar

Requisitos: C++17 o superior.

Compilar:
```
g++ -std=gnu++17 -O2 -Wall -Wextra -o day9 main.cpp
```

Ejecutar:
```
./day9 input.txt
```

Formato de `input.txt`:
```
7,1
11,1
11,7
9,7
9,5
2,5
2,3
7,3
```

---

## Reflexión personal

- Hemos aprendido a formalizar condiciones geométricas (dentro/borde, intersecciones).
- Separar aristas verticales/horizontales simplifica el diseño.
- Pequeñas podas mejoran mucho la eficiencia.

---

## Código fuente

Incluye el código completo en `main.cpp`:
```
#include <iostream>
#include <fstream>
#include <vector>
#include <utility>
#include <cmath>
#include <algorithm>
#include <string>

using ll = long long;

struct Arista { ll x1, y1, x2, y2; };
// ... (resto del código igual al proporcionado)
```
