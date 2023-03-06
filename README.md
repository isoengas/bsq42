# bsq42

- Para hacer la tarea más sencilla, se podrían asumir algunas limitaciones:
  - El número máximo de lineas es 9 (no lo dice en ninguna parte, pero simplifica la tarea)
  - No leemos de stdin, solo trabajamos con parámetros de entrada
  - No hacemos todas las validaciones requeridas.. si el mapa es incorrecto el programa va a petar
  
1. Dentro de main, hacer el código que por cada argumento recibido llame a una función a la que pasamos el argumento. (ejemplo para tratar argumentos):
```c
#include <stdio.h>

int main(int argc, char **argv)
{
    int i = 1;
    while (i < argc)
    {
        char *fileInput;
        fileInput = argv[i];
        handleMap(fileInput);
        i++;
    }
}
```
2. El prototipo de la función podría ser algo así:
```c
void handleMap(char* filePath);
```
3. La función handleMap tiene que:
  1. Llamar a una función que me devuelve la altura del mapa (nº lineas)
  ```c
int getMapHeight(char* filePath);
```
    1.1 Abrir el fichero que recibe como parámetro (open)
    1.2 Leer la primera línea, y de esa línea extraer el número de lineas
    1.3 Cerrar el fichero
    1.4 Devolver el nº de lineas
  2. Llamar a una función que me devuelve el número de columnas
  ```c
int getMapWidth(char* filePath);
```
    2.1 Abrir el fichero que recibe como parámetro
    2.2 Leer la segunda línea y contar el número de caracters
    2.3 Cerrar el fichero
    2.4 Devolver la anchura del mapa
    
  3. Reservar memoria para un array bidimensional de caracteres de num_lines x num_cols https://www.geeksforgeeks.org/dynamically-allocate-2d-array-c/
  4. Volver a abrir el fichero
  5. Empezar a leer desde la segunda línea rellenando el array don dos bucles anidados (recorro filas, recorro columnas de cada fila)
  6. Cerrar el fichero, en este punto ya tenemos una representación del mapa en memoria
  
