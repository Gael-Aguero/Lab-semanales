# Laboratorio 4

Para este laboratorio se compara el desempeño al igual que las diferencias de usar librerías dinámicas y estáticas. 

## Librería estática

Al enlazar con la librería estática, obteniendo un tiempo de llenado y suma de:
* fill A: 294389.375 microseconds total, 294.389 per iteration
* fill B: 283258.727 microseconds total, 283.259 per iteration
* add: 732674.818 microseconds total, 732.675 per iteration
* total: 1310324.016 microseconds
Generando un biblioteca estática -rw-r--r-- 1 gales gales 1,8K ago 30 11:04 build/lib/libvectorops.a

## Librería dinámica

Al enlazar con la librería dinámica, se obtiene tiempo de llenado y suma de:
* fill A: 651957.268 microseconds total, 651.957 per iteration
* fill B: 649846.299 microseconds total, 649.846 per iteration
* add: 911335.329 microseconds total, 911.335 per iteration
* total: 2213140.326 microseconds
Generando una biblioteca dinámica -rwxr-xr-x 1 gales gales 16K ago 30 11:04 build/lib/libvectorops.so

## Análisis de datos
fill A y fill B más que se duplican en tiempo al usar la librería dinámica (+121% y +129%). Estas funciones hacen muy poco trabajo por llamada (solo escribir un valor), así que el costo fijo de invocar la función domina el tiempo total de la operación.
add, en cambio, solo crece un 24.4% en términos relativos, aunque su diferencia absoluta (178 660 µs) es la mayor de las tres. 

Esto apunta directamente a la causa del sobrecosto que ocurre en cada llamada a una función de una librería dinámica, en contraste con el enlace directo que el linker resuelve en tiempo de compilación para la librería estática. Cuanto más pequeña y frecuente es la operación, más pesa ese overhead de indirección respecto al trabajo útil.

