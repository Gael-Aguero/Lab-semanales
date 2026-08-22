# Laboratorio de clase 2

Este laboratorio de clase explica distintos conceptos de AVX2 por medio de algoritmos de multiplicación de matrices: una escalar que usa los conceptos tradicionales de multiplicación y una vectorial que usa los intrínsecos de AVX2.

## Análisis de datos 
Al generarse los códigos siguiendo lo que hizo el profesor, se pudo completar el algortimo de multiplicación de matrices vectorial, el cuál se tiene que comparar con el algoritmo escalar. El algoritmo escalar dio los siguientes resultados:

Tamano matriz: 2048x2048

Repeticiones: 1

Checksum: 86972906452.000000

C[0][0]: 26800.500000

C[1023][1023]: 26836.500000

Operaciones: 17179869184

Tiempo: 4.180194 segundos

Rendimiento: 4.109826 GFLOP/s

El algoritmo vectorial dio retornó:

Tamano matriz: 2048x2048

Repeticiones: 1

Checksum: 86972906452.000000

C[0][0]: 26800.500000

C[1023][1023]: 26836.500000

Operaciones: 17179869184

Tiempo: 1.954612 segundos

Rendimiento: 8.789401 GFLOP/s

Estos datos implican un speedup del algoritmo vectorial sobre el escalar del 2.1 veces, esto, como lo explicó el profesor, este speeup es con la optimización del compilador, cuando se le pide al compilador que no optimice, baja el speedup ya que se vuelve ineficiente la traducción a ensamblador, ejemplificando la ley de Amdahl.