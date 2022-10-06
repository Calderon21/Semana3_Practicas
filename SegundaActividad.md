# La semana pasada
- Recuerde que nuestro propósito para aprender un nuevo lenguaje de programación y otras herramientas es resolver problemas. Y resolvemos esos problemas creando alguna salida a partir de la entrada:
![](https://cs50.harvard.edu/x/2022/notes/3/input_output.png)
- Aprendimos sobre la memoria, que nos permite almacenar datos como bytes y cadenas, que son matrices de caracteres

# Buscando
- Hoy nos enfocaremos en algoritmos que resuelven problemas con arreglos.
- Resulta que, con matrices, una computadora no puede ver todos los elementos a la vez. En cambio, una computadora solo puede mirarlos uno a la vez, aunque podemos mirar en cualquier orden, como solo poder abrir un casillero a la vez:
![](https://cs50.harvard.edu/x/2022/notes/3/lockers.png)
    - Recuerde que las matrices tienen un índice cero, lo que significa que el primer elemento tiene un índice de 0. Y con n artículos, el índice más alto sería n-1.

**Buscar** es cómo resolvemos el problema de encontrar información. Un problema simple tiene una entrada de algunos valores y una salida de un bool ya sea que un valor particular esté o no en la matriz.

## Grande 

- Hoy veremos algoritmos de búsqueda. Para comparar su eficiencia, consideraremos **el tiempo de ejecución** , o cuánto tarda en ejecutarse un algoritmo dado un tamaño de entrada.

- Los informáticos tienden a describir el tiempo de ejecución con **grandes notaciónes** , que podemos pensar como "en el orden de" algo, como si quisiéramos transmitir una idea del tiempo de ejecución y no un número exacto de milisegundos o pasos.

- En la semana 0, vimos un gráfico con diferentes tipos de algoritmos y los tiempos que pueden tardar en resolver un problema:
![](https://cs50.harvard.edu/x/2022/notes/3/time_to_solve.png)
    - Recuerde que la línea roja busca linealmente, una página a la vez; la línea amarilla busca dos páginas a la vez; y la línea verde es dividir y conquistar, comenzando en el medio y dividiendo el problema por la mitad cada vez.

- En el gráfico anterior, si nos alejamos y cambiamos las unidades en nuestros ejes, veríamos que las líneas roja y amarilla terminan muy juntas:
![](https://cs50.harvard.edu/x/2022/notes/3/time_to_solve_zoomed_out.png)
    - Así que usamos grandes notaciónes para describir tanto las líneas rojas como las amarillas, ya que terminan siendo muy similares como n se vuelve más y más grande. Los describiríamos a ambos como "grandesOden” o “en el orden de n " tiempo de ejecución.
    - La línea verde, sin embargo, es fundamentalmente diferente en su forma, aun cuando n se vuelve muy grande, por lo que se necesita "granOdelog(n)" pasos. (La base del logaritmo, 2, también se elimina porque es un factor constante).

- Veremos algunos tiempos de ejecución comunes:
    - "<math xmlns="http://www.w3.org/1998/Math/MathML">
  <mi>O</mi>
  <mo stretchy="false">(</mo>
  <msup>
    <mi>n</mi>
    <mn>2</mn>
  </msup>
  <mo stretchy="false">)</mo>
</math>"
    - "<math xmlns="http://www.w3.org/1998/Math/MathML">
  <mi>O</mi>
  <mo stretchy="false">(</mo>
  <mi>n</mi>
  <mi>log</mi>
  <mo data-mjx-texclass="NONE">&#x2061;</mo>
  <mi>n</mi>
  <mo stretchy="false">)</mo>
</math>"
    - "<math xmlns="http://www.w3.org/1998/Math/MathML">
  <mi>O</mi>
  <mo stretchy="false">(</mo>
  <mi>n</mi>
  <mo stretchy="false">)</mo>
</math>"
    - "<math xmlns="http://www.w3.org/1998/Math/MathML">
  <mi>O</mi>
  <mo stretchy="false">(</mo>
  <mi>log</mi>
  <mo data-mjx-texclass="NONE">&#x2061;</mo>
  <mi>n</mi>
  <mo stretchy="false">)</mo>
</math>"
    - "<math xmlns="http://www.w3.org/1998/Math/MathML">
  <mi>O</mi>
  <mo stretchy="false">(</mo>
  <mn>1</mn>
  <mo stretchy="false">)</mo>
</math>"

- Los informáticos también pueden utilizar grandes <math xmlns="http://www.w3.org/1998/Math/MathML">
  <mi>&#x3A9;</mi>
</math>, notación Omega grande, que describe el límite inferior del número de pasos para nuestro algoritmo, o cuántos pasos podría tomar, en el mejor de los casos. Grande <math xmlns="http://www.w3.org/1998/Math/MathML">
  <mi>O</mi>
</math>, del orden de, es el límite superior del número de pasos, o cuántos pasos podría tomar, en el peor de los casos.

- Tenemos un conjunto similar de los grandes más comunes <math xmlns="http://www.w3.org/1998/Math/MathML">
  <mi>&#x3A9;</mi> tiempos de ejecución:
    - "<math xmlns="http://www.w3.org/1998/Math/MathML">
  <mi mathvariant="normal">&#x3A9;</mi>
  <mo stretchy="false">(</mo>
  <msup>
    <mi>n</mi>
    <mn>2</mn>
  </msup>
  <mo stretchy="false">)</mo>
</math>"
    - "<math xmlns="http://www.w3.org/1998/Math/MathML">
  <mi mathvariant="normal">&#x3A9;</mi>
  <mo stretchy="false">(</mo>
  <mi>n</mi>
  <mi>log</mi>
  <mo data-mjx-texclass="NONE">&#x2061;</mo>
  <mi>n</mi>
  <mo stretchy="false">)</mo>
</math>"
    - "<math xmlns="http://www.w3.org/1998/Math/MathML">
  <mi mathvariant="normal">&#x3A9;</mi>
  <mo stretchy="false">(</mo>
  <mi>n</mi>
  <mo stretchy="false">)</mo>
</math>"
    - "<math xmlns="http://www.w3.org/1998/Math/MathML">
  <mi mathvariant="normal">&#x3A9;</mi>
  <mo stretchy="false">(</mo>
  <mi>log</mi>
  <mo data-mjx-texclass="NONE">&#x2061;</mo>
  <mi>n</mi>
  <mo stretchy="false">)</mo>
</math>"
    - "<math xmlns="http://www.w3.org/1998/Math/MathML">
  <mi mathvariant="normal">&#x3A9;</mi>
  <mo stretchy="false">(</mo>
  <mn>1</mn>
  <mo stretchy="false">)</mo>
</math>"

- Finalmente, hay otra notación,<math xmlns="http://www.w3.org/1998/Math/MathML">
  <mi mathvariant="normal">&#x398;</mi>
</math>, Theta grande, que usamos para describir los tiempos de ejecución de los algoritmos si el límite superior y el límite inferior son iguales.
    - "<math xmlns="http://www.w3.org/1998/Math/MathML">
  <mi mathvariant="normal">&#x398;</mi>
  <mo stretchy="false">(</mo>
  <msup>
    <mi>n</mi>
    <mn>2</mn>
  </msup>
  <mo stretchy="false">)</mo>
</math>"
    - "<math xmlns="http://www.w3.org/1998/Math/MathML">
  <mi mathvariant="normal">&#x398;</mi>
  <mo stretchy="false">(</mo>
  <mi>n</mi>
  <mi>log</mi>
  <mo data-mjx-texclass="NONE">&#x2061;</mo>
  <mi>n</mi>
  <mo stretchy="false">)</mo>
</math>"
    - "<math xmlns="http://www.w3.org/1998/Math/MathML">
  <mi mathvariant="normal">&#x398;</mi>
  <mo stretchy="false">(</mo>
  <mi>n</mi>
  <mo stretchy="false">)</mo>
</math>"
    - "<math xmlns="http://www.w3.org/1998/Math/MathML">
  <mi mathvariant="normal">&#x398;</mi>
  <mo stretchy="false">(</mo>
  <mi>log</mi>
  <mo data-mjx-texclass="NONE">&#x2061;</mo>
  <mi>n</mi>
  <mo stretchy="false">)</mo>
</math>"
    - "<math xmlns="http://www.w3.org/1998/Math/MathML">
  <mi mathvariant="normal">&#x398;</mi>
  <mo stretchy="false">(</mo>
  <mn>1</mn>
  <mo stretchy="false">)</mo>
</math>"
- Un algoritmo con tiempo de <math xmlns="http://www.w3.org/1998/Math/MathML">
  <mi>O</mi>
  <mo stretchy="false">(</mo>
  <mn>1</mn>
  <mo stretchy="false">)</mo>
</math> ejecución designifica que se requiere un número constante de pasos, sin importar cuán grande sea el problema.

- Echemos un vistazo a algunos algoritmos que podemos describir con estos tiempos de ejecución.

## Búsqueda lineal, búsqueda binaria
- En el escenario, tenemos siete casilleros con puertas cerradas, con números escondidos detrás de ellos. Dado que una computadora solo puede mirar un elemento en una matriz a la vez, solo podemos abrir una puerta a la vez también.
- Si queremos buscar el número cero, por ejemplo, tendríamos que abrir una puerta a la vez, y si no supiéramos nada sobre los números detrás de las puertas, el algoritmo más simple sería ir de izquierda a derecha.
- Este algoritmo, de búsqueda lineal , sería correcto pero no muy eficiente. Podríamos escribir pseudocódigo con:


        - For each door from left to right
           If number is behind door
               Return true
        Return false
    - Return False  está fuera del ciclo for, ya que solo queremos hacer eso después de haber mirado detrás de todas las puertas.
- Podemos reescribir nuestro pseudocódigo para estar un poco más cerca de C:


        - For i from 0 to n-1
             If number behind doors[i]
                   Return true
           Return false
    - Ahora, estamos usando una variable, i, para ver cada ubicación en una matriz llamada doors.
- Con n las puertas, tendremos que mirarlas todas n. Y lo que hacemos para cada una de las npuertas, que es mirar hacia adentro y posiblemente regresar true, toma un número constante de pasos cada vez. Así que el grande<math xmlns="http://www.w3.org/1998/Math/MathML">
  <mi>O</mi>
</math>el tiempo de ejecución de este algoritmo sería <math xmlns="http://www.w3.org/1998/Math/MathML">
  <mi>O</mi>
  <mo stretchy="false">(</mo>
  <mi>n</mi>
  <mo stretchy="false">)</mo>
</math>.
- El límite inferior, gran Omega, sería <math xmlns="http://www.w3.org/1998/Math/MathML">
  <mi mathvariant="normal">&#x3A9;</mi>
  <mo stretchy="false">(</mo>
  <mn>1</mn>
  <mo stretchy="false">)</mo>
</math>, ya que puede que tengamos suerte y encontremos el número que buscamos enseguida, lo que requiere un número constante de pasos.  
- Si sabemos que los números detrás de las puertas están ordenados, entonces podemos comenzar en el medio y encontrar nuestro valor de manera más eficiente ya que sabemos que podemos ir a la izquierda o a la derecha, dividiendo el problema a la mitad cada vez.   
- Para la búsqueda binaria , el pseudocódigo de nuestro algoritmo podría verse así:


        - If no doors
                Return false
          If number behind middle door
                Return true
          Else if number < middle door
                Search left half
          Else if number > middle door
                 Search right half

    - Recordamos verificar si no quedan puertas, ya que eso significa que nuestro número no está detrás de ninguna de ellas.
- Podemos escribir este pseudocódigo para que se parezca más a C:


        - If no doors
            Return false
          If number behind doors[middle]
            Return true
          Else if number < doors[middle]
            Search doors[0] through doors[middle - 1]
          Else if number > doors[middle]
            Search doors [middle + 1] through doors[n - 1]
    - Podemos determinar el índice de la puerta del medio con un poco de matemática, y luego podemos dividir el problema en buscar las puertas con índices 0 hasta middle - 1 o middle + 1 hasta n - 1.
- El límite superior para la búsqueda binaria es <math xmlns="http://www.w3.org/1998/Math/MathML">
  <mi>O</mi>
  <mo stretchy="false">(</mo>
  <mi>log</mi>
  <mo data-mjx-texclass="NONE">&#x2061;</mo>
  <mi>n</mi>
  <mo stretchy="false">)</mo>
</math>, ya que es posible que tengamos que seguir dividiendo el número de puertas entre dos hasta que no queden más puertas. El límite inferior <math xmlns="http://www.w3.org/1998/Math/MathML">
  <mi mathvariant="normal">&#x3A9;</mi>
  <mo stretchy="false">(</mo>
  <mn>1</mn>
  <mo stretchy="false">)</mo>
</math>, si el número que estamos buscando está en el medio, donde empezamos.
- Aunque la búsqueda binaria puede ser mucho más rápida que la búsqueda lineal, requiere que nuestra matriz se ordene primero. Si planeamos buscar nuestros datos muchas veces, podría valer la pena tomarse el tiempo para ordenarlos primero, para que podamos usar la búsqueda binaria.

- Otros recursos que podríamos considerar más allá del tiempo que lleva ejecutar algún código incluyen el tiempo que lleva escribir el código o la cantidad de memoria requerida para nuestro código.

## Buscando con código

```Python
#include <cs50.h>
#include <stdio.h>

int main(void)
{
    int numbers[] = {4, 6, 8, 2, 7, 5, 0};

    for (int i = 0; i < 7; i++)
    {
        if (numbers[i] == 0)
        {
            printf("Found\n");
            return 0;
        }
    }
    printf("Not found\n");
    return 1;
}
```
- Aquí inicializamos una matriz con valores usando llaves y verificamos los elementos de la matriz uno a la vez, en orden, para ver si son iguales a cero.

- Si encontramos el valor de cero, devolvemos un código de salida de 0 (para indicar el éxito). De lo contrario, después de nuestro ciclo for, llamamos return 1(para indicar un código de error).
- Así es como podríamos implementar la búsqueda lineal.     
- Podemos compilar nuestro programa y ejecutarlo para ver que funciona:

```
$ make numbers
$ ./numbers
Found

```
- Y podemos cambiar lo que estamos buscando a -1, y ver que nuestro programa no lo encuentra:

```
...
if (numbers[i] == -1)
...
```
```
$ make numbers
$ ./numbers
Not found
```
- Podemos hacer lo mismo para cadenas en names.c:

```Python
#include <cs50.h>
#include <stdio.h>
#include <string.h>

int main(void)
{
    string names[] = {"Bill", "Charlie", "Fred", "George", "Ginny", "Percy", "Ron"};

    for (int i = 0; i < 7; i++)
    {
        if (names[i] == "Ron")
        {
            printf("Found\n");
            return 0;
        }
    }
    printf("Not found\n");
    return 1;
}
```
- Pero cuando tratamos de compilar nuestro programa, obtenemos:

```
$ make names
names.c:11:22: error: result of comparison against a string literal is unspecified (use an explicit string comparison function instead) [-Werror,-Wstring-compare]
        if (names[i] == "Ron")
                     ^  ~~~~~
1 error generated.
make: *** [<builtin>: names] Error 1
```
- Resulta que no podemos comparar cadenas directamente en C, ya que no son un tipo de datos simple integrado en el lenguaje, sino una matriz de muchos caracteres. Afortunadamente, la **string** biblioteca tiene una función, comparación **strcmpde** *cadenas* , que compara cadenas por nosotros. **strcmp** devuelve un valor negativo si la primera cadena viene antes de la segunda cadena, **0** si las cadenas son iguales, y un valor positivo si la primera cadena viene después de la segunda cadena.
- Cambiaremos nuestro condicional a **if (strcmp(names[i], "Ron") == 0)** , para que podamos verificar si nuestras dos cadenas son realmente iguales.
- Y si escribimos **if (strcmp(names[i], "Ron"))**, entonces se consideraría cualquier valor distinto de cero, positivo o negativo, **true** que sería lo contrario de lo que queremos. 

    - De hecho, podríamos escribir **if (!strcmp(names[i], "Ron"))** para invertir el valor, lo que funcionaría en este caso, pero podría decirse que sería un diseño peor, ya que no verifica explícitamente el valor de 0como indica la documentación. 
    
# estructuras
- Podríamos querer implementar una guía telefónica, con nombres y números de teléfono, en **phonebook0.c**:
    ```Python
        #include <cs50.h>
        #include <stdio.h>
        #include <string.h>
        
        int main(void)
        {
            string names[] = {"Carter", "David"};
            string numbers[] = {"+1-617-495-1000", "+1-949-468-2750"};
        
            for (int i = 0; i < 2; i++)
            {
                if (strcmp(names[i], "David") == 0)
                {
                    printf("Found %s\n", numbers[i]);
                    return 0;
                }
            }
            printf("Not found\n");
            return 1;
        }
    ``` 
    - Tenemos dos matrices, **names** y **numbers**, y nos aseguraremos de que el número de teléfono de cada persona tenga el mismo índice que su nombre en cada matriz.
    -Buscaremos en nuestra **names** matriz el nombre de alguien y luego devolveremos su número de teléfono correspondiente en el mismo índice.
    - Este programa es correcto, pero no está bien diseñado ya que tendremos que mantener ambas matrices con cuidado para asegurarnos de que los nombres y los números coincidan.
    - ¡Y siéntase libre de llamar o enviar un mensaje de texto a David para una sorpresa!
- Resulta que en C podemos definir nuestro propio tipo de **datos o estructura de datos** . Sería un mejor diseño para nuestro programa tener una matriz con un tipo de datos personque incluya tanto su nombre como su número de teléfono, por lo que solo podemos decir **person people[]**;.
En C, podemos crear una **estructura** con la siguiente sintaxis:
    ```c
    typedef struct

    {
        string name;
        string number;
    }

    person;
    ```
    - **typedef struct** le dice al compilador que estamos definiendo nuestra propia estructura de datos. Y **person** final de las llaves estará el nombre de esta estructura de datos.
    - Dentro de nuestra estructura, tendremos dos cadenas **name** y **number**. Usaremos cadenas para los números de teléfono, ya que pueden incluir signos de puntuación, y otros tipos de números, como los códigos postales, pueden tener un 0 inicial que desaparecería si se tratara como un número.
- Usaremos esto en **phonebook1.c**:
    ```c
    #include <cs50.h>
    #include <stdio.h>
    #include <string.h>

    typedef struct
    {
        string name;
        string number;
    }
    person;

    int main(void)
    {
        person people[2];

        people[0].name = "Carter";
        people[0].number = "+1-617-495-1000";

        people[1].name = "David";
        people[1].number = "+1-949-468-2750";

        for (int i = 0; i < 2; i++)
        {
            if (strcmp(people[i].name, "David") == 0)
            {
                printf("Found %s\n", people[i].number);
                return 0;
            }
        }
        printf("Not found\n");
        return 1;
    }
    ```
   - Vemos una nueva sintaxis para establecer los valores de cada variable dentro de cada **person** estructura mediante el operador de punto, ..
    - En nuestro ciclo, también podemos usar **.name** o **.number** para acceder a variables en nuestras estructuras, y estar seguros de que son del mismo person.
- En informática, la **encapsulación** es la idea de que los datos relacionados se agrupan, y aquí hemos encapsulado dos piezas de información **name** en **number** la misma estructura de datos. El color de un píxel, con valores de rojo, verde y azul, también puede estar bien representado por una estructura de datos.
-También podemos imaginar que una estructura se puede usar para almacenar valores decimales precisos o valores enteros grandes, tal vez con matrices que podemos usar para almacenar una gran cantidad de dígitos.
# Clasificación
- **Ordenar** es resolver el problema que toma una lista de números sin ordenar como entrada y produce una salida de una lista ordenada de números:
    ![Primera Imagen!](https://cs50.harvard.edu/x/2022/notes/3/sorting.png)

    - Por ejemplo
     > 6 3 8 5 2 7 4 1
     >
    podría ser entrada y salida sería 
    > 1 2 3 4 5 6 7 8.
# Demostración de clasificación por selección
- Tendremos ocho voluntarios subiendo al escenario, en orden desordenado:
    > 5 2 7 4 1 6 3 0
>
- Pedimos a nuestros voluntarios que se clasifiquen y todos se mueven a la posición correcta:
    >0 1 2 3 4 5 6 7
>
- Desafortunadamente, las computadoras solo pueden mirar un número y mover uno de ellos a la vez, al menos con los programas que hemos escrito hasta ahora.
- Comenzaremos con los números sin ordenar de nuevo y, paso a paso, buscaremos primero el número más pequeño, observando cada número en orden:
    > 5 2 7 4 1 6 3 0
    >         ^
    >
- Ahora, intercambiaremos el número más pequeño con el número del principio, ya que es más fácil que cambiar todos los demás números hacia abajo:
    > 0 | 2 7 4 1 6 3 5
    >
- Ahora, nuestro problema se ha vuelto más pequeño, ya que sabemos que al menos el comienzo de nuestra lista está ordenado. Entonces podemos repetir lo que hicimos, comenzando desde el segundo número de la lista:
    >0 | 2 7 4 1 6 3 5
          ^    
    0 | 1 7 4 2 6 3 5
>
- **1** es el número más pequeño ahora, así que lo cambiaremos con el segundo número.
- Repetiremos esto otra vez…
    >0 1 | 7 4 2 6 3 5
          ^     
0 1 | 2 4 7 6 3 5
>
- … y otra vez …

    >0 1 2 | 4 7 6 3 5
              ^     
0 1 2 | 3 7 6 4 5
>
- … y otra vez …
> 0 1 2 3 | 7 6 4 5
              ^     
0 1 2 3 | 4 6 7 5
> 
- … y otra vez …
> 0 1 2 3 4 | 6 7 5
                ^     
0 1 2 3 4 | 5 7 6
>
- … y otra vez, hasta que hayamos intercambiado el último número de nuestra lista:
>0 1 2 3 4 5 | 7 6
                ^     
0 1 2 3 4 5 | 6 7
>
# Demostración de clasificación de burbujas
- Comenzaremos con nuestra lista desordenada, pero esta vez veremos pares de números y los cambiaremos si están desordenados:

> 5 2 7 4 1 6 3 0 
^ ^
2 5 7 4 1 6 3 0
  ^ ^
2 5 7 4 1 6 3 0
    ^ ^
2 5 4 7 1 6 3 0
      ^ ^
2 5 4 1 7 6 3 0
        ^ ^
2 5 4 1 6 7 3 0
          ^ ^
2 5 4 1 6 3 7 0
            ^ ^
2 5 4 1 6 3 0 7
>
- Ahora, el número más alto está completamente a la derecha, así que hemos mejorado nuestro problema.
Repetiremos esto de nuevo:
>2 5 4 1 6 3 0 | 7
^ ^
2 5 4 1 6 3 0 | 7
  ^ ^
2 4 5 1 6 3 0 | 7
    ^ ^
2 4 1 5 6 3 0 | 7
      ^ ^
2 4 1 5 6 3 0 | 7
        ^ ^
2 4 1 5 3 6 0 | 7
          ^ ^
2 4 1 5 3 0 6 | 7
>
- Ahora los dos valores más grandes están a la derecha.
- Repetiremos de nuevo…
>2 4 1 5 3 0 | 6 7
^ ^
2 4 1 5 3 0 | 6 7
  ^ ^
2 1 4 5 3 0 | 6 7
    ^ ^
2 1 4 5 3 0 | 6 7
      ^ ^
2 1 4 3 5 0 | 6 7
        ^ ^
2 1 4 3 0 5 | 6 7
>
- … y otra vez …

>2 1 4 3 0 | 5 6 7
^ ^
1 2 4 3 0 | 5 6 7
  ^ ^
1 2 3 4 0 | 5 6 7
    ^ ^
1 2 3 4 0 | 5 6 7
      ^ ^
1 2 3 0 4 | 5 6 7

- … y otra vez …
>1 2 3 0 | 4 5 6 7
^ ^
1 2 3 0 | 4 5 6 7
  ^ ^
1 2 3 0 | 4 5 6 7
    ^ ^
1 2 0 3 | 4 5 6 7

- … y otra vez …
> 1 2 0 | 3 4 5 6 7
^ ^
1 2 0 | 3 4 5 6 7
  ^ ^
1 0 2 | 3 4 5 6 7

- … y finalmente:
1 0 | 2 3 4 5 6 7
^ ^
0 1 | 2 3 4 5 6 7

- Tenga en cuenta que, a medida que avanzamos en nuestra lista, sabemos que cada vez se ordena más, por lo que solo necesitamos mirar los pares de números que aún no se han ordenado.
# Clasificación de selección
- El primer algoritmo que vimos se llama ordenación por selección y podríamos escribir un pseudocódigo como:
    >   For i from 0 to n–1
            Find smallest number between numbers[i] and numbers[n-1]
            Swap smallest number with numbers[i]
    
    - Necesitamos ordenar todos los **n** números en nuestra lista, por lo que tendremos un bucle **i** para realizar un seguimiento de cuántos números hemos ordenado hasta ahora.
    - El primer paso en el bucle es buscar el número más pequeño en la parte no ordenada de la lista, desde el índice **i** hasta el **n-1**.
    - Luego, intercambiamos el número más pequeño que encontramos con el número en el índice **i**, lo que hace que todo esté iordenado.
    - Y repetiremos esto hasta que toda la lista esté ordenada, de izquierda a derecha, **i** de **0** a **n-1**.
- Para este algoritmo, comenzamos observando todoselementos, solo entonces, después, y así:

$n + (n - 1) + (n - 2) + ... + 1$

$n(n+1)/2$

$n(n+1)/2$

$O(n^2)$




-   Podemos usar algunas fórmulas matemáticas para llegar a $n^2/2+n/2$ pasos. Ya quees el factor más grande, o dominante, comose hace realmente grande, podemos decir que el algoritmo tiene un límite superior para el tiempo de ejecución de $O(n^2)$.

- En el mejor de los casos, cuando la lista ya está ordenada, nuestro algoritmo de ordenación de selección aún buscará todos los números y repetirá el ciclo, por lo que tiene un límite inferior para el tiempo de ejecución de 
$ \Omega(n^2)$.













# Ordenamiento Burbuja


- El pseudocódigo para la ordenación de burbuja podría verse así:

        Repetir n-1 veces
            Para i de 0 a n–2
                Si el número[i] y el número[i+1] están fuera de osrden
                    cambiarlos

    
    - Como estamos comparando cada par de números en i e i+1, solo necesitamos subir a n–2 para i.
    - Luego, intercambiamos los dos números si están desordenados.
    - Necesitamos repetir esto (n-1) veces ya que cada vez que repasamos la lista, solo un número se  mueve completamente hacia la derecha.
- Para determinar el tiempo de ejecución de la ordenación de burbujas, tenemos (n-1) comparaciones en el bucle, y (n-1) bucles:

            (n-1) x (n-1)
            n²-1n-1n+1
            n²-2n+1s
            O(n²)

- El factor más importante es de nuevo n² como n se vuelve cada vez más grande, por lo que podemos decir que el tipo de burbuja tiene un límite superior para el tiempo de ejecución de O(n²).
- Si añadimos un poco de lógica a nuestro algoritmo, podemos optimizar el tiempo de ejecución en el mejor de los casos:

            Repetir n-1 veces
                Para i de 0 a n–2
                    Si el número[i] y el número[i+1] están fuera de orden
                        cambiarlos
                    Si no hay permutas
                        Abandonar

    - Si miramos todos los números y no hicimos ningún intercambio, entonces sabemos que nuestra lista ha sido ordenada.
- El límite inferior para el tiempo de ejecución del tipo de burbuja sería X(n).
- Observamos una [visualización](https://www.cs.usfca.edu/~galles/visualization/ComparisonSort.html) con animaciones sobre cómo se mueven los números para la clasificación por selección y la clasificación por burbujas.

# Recursividad

- **La recursividad** es la capacidad de una función para llamarse a sí misma. Todavía no hemos visto esto en código, pero lo hemos visto en pseudocódigo para búsqueda binaria:

        si no hay puertas
            Falso retorno
        Si el número detrás de la puerta del medio
            Devolver verdadero
        De lo contrario, si el número < puerta central
            Buscar mitad izquierda
        De lo contrario, si el número> puerta central
            Buscar mitad derecha
            
    - Estamos usando el mismo algoritmo de "búsqueda" para cada mitad. Esto parece un proceso cíclico que nunca terminará, pero en realidad estamos cambiando la entrada a la función y dividiendo el problema por la mitad cada vez, deteniéndonos una vez que no queden más puertas.
- Nuestro pseudocódigo de la semana 0 usaba "volver atrás" para repetir algunos pasos, como un bucle:

        1 Recoger guía telefónica
        2 Abierto hasta la mitad de la guía telefónica
        3 Mira la página
        4 Si la persona está en la página
        5 Persona de llamada
        6 De lo contrario, si la persona es anterior en el libro
        7 Abierto a la mitad de la mitad izquierda del libro
        8 Vuelve a la línea 3
        9 De lo contrario, si la persona está más tarde en el libro
        10 Abierto a la mitad de la mitad derecha del libro
        11 Volver a la línea 3
        12 más
        13 Salir    

- Pero de manera similar podemos hacer que nuestro algoritmo se use solo después de dividir el problema:

        1 Recoger guía telefónica
        2 Abierto hasta la mitad de la guía telefónica
        3 Mira la página
        4 Si la persona está en la página
        5 Persona de llamada
        6 De lo contrario, si la persona es anterior en el libro
        7 Buscar en la mitad izquierda del libro
        8 De lo contrario, si la persona está más tarde en el libro
        9 Buscar en la mitad derecha del libro
        10 más
        11 Salir

- En la semana 1 también implementamos una "pirámide" de bloques con la siguiente forma:

        #
        ##
        ###
        ####

- Nuestro código para imprimir esto podría verse así:

        #include <cs50.h>
        #include <stdio.h>
        
        void draw(int n);
        
        int main(void)
        {
            int height = get_int("Height: ");
        
            draw(height);
        }
        
        void draw(int n)
        {
            for (int i = 0; i < n; i++)
            {
                for (int j = 0; j < i + 1; j++)
                {
                    printf("#");
                }
                printf("\n");
            }
        }

    - Tenemos una función de dibujo que toma un argumento, n, y usa un bucle para imprimir n filas con más y más ladrillos en cada fila.
    - Podemos ejecutar nuestro código y ver que funciona:

            $ make iteration
            $ ./iteration 
            Height: 4
            #
            ##
            ###
            ####

- Pero observe que una pirámide de altura 4 es en realidad una pirámide de altura 3 con una fila extra de 4 bloques añadidos. Y una pirámide de altura 3 es una pirámide de altura 2 con una fila extra de 3 bloques. Una pirámide de altura 2 es una pirámide de altura 1 con una fila extra de 2 bloques. Y finalmente, una pirámide de altura 1 es una pirámide de altura 0 (sin bloques) con una fila de 1 bloque añadido.
- Dado que una pirámide es una estructura recursiva, podemos escribir una función recursiva para dibujar una pirámide, una función que se llama a sí misma para dibujar una pirámide más pequeña antes de agregar otra fila:

        #include <cs50.h>
        #include <stdio.h>
        
        void draw(int n);
        
        int main(void)
        {
            int height = get_int("Height: ");

            draw(height);
        }
        
        void draw(int n)
        {
            if (n <= 0)
            {
                return;
            }
        
            draw(n - 1);
        
            for (int i = 0; i < n; i++)
            {
                printf("#");
            }
            printf("\n");
        }

    - Podemos reescribir nuestra función de dibujo para usarla.
    - Si n es 0 (o negativo de alguna manera) nos detendremos sin imprimir nada. Y debemos asegurarnos de detenernos en algún **caso base**, para que nuestra función no se llame a sí misma una y otra vez para siempre.
    - De lo contrario, llamaremos a dibujar de nuevo, para imprimir primero una pirámide de tamaño n - 1.
    - Luego, imprimiremos la fila de bloques que necesitamos para nuestra pirámide, de tamaño n.
    - Podemos ejecutar nuestro código y ver que funciona:

            $ make recursion
            $ ./recursion 
            Height: 4
            #
            ##
            ###
            ####

- Podemos cambiar nuestro condicional a si (n == 0) y escribir un número negativo para ver qué sucede:

        $ make recursion
        $ ./recursion
        Height: -100
        Segmentation fault (core dumped)

    - Una falla de segmentación significa que hemos tocado memoria en nuestra computadora que no deberíamos haber tocado, y esto sucedió porque nuestra función se llamó a sí misma una y otra vez y terminó usando demasiada memoria.

# Ordenar por fusión

- Podemos llevar la idea de la recusación a la clasificación, con otro algoritmo llamado **clasificación por fusión**. El pseudocódigo podría verse así
    
        Si solo un numero
            Abandonar
        Sino
            Ordenar la mitad izquierda del número
            Ordenar la mitad derecha del número
            Combinar mitades ordenadas

* Nuestra estrategia será clasificar cada mitad y luego fusionarlas. Comencemos con dos mitades ordenadas que se ven así:

        2 4 5 7 | 0 1 3 6

    * Veremos solo el primer número de cada lista y moveremos el 0 más pequeño al comienzo de una nueva lista. Entonces podemos mirar el siguiente número en la lista:

            2 4 5 7 | 0 1 3 6
            ^         ^

            2 4 5 7 |   1 3 6
            ^           ^
            0

    * Moveremos el siguiente número más pequeño, 1, hacia abajo, y miraremos el siguiente número en esa lista:

            2 4 5 7 |     3 6
            ^             ^
            0 1

    * Esta vez, el 2 es el siguiente más pequeño, así que lo moveremos hacia abajo y repetiremos este proceso:

            4 5 7 |     3 6
            ^           ^
            0 1 2

            4 5 7 |       6
            ^             ^
            0 1 2 3

                5 7 |       6
                ^           ^
            0 1 2 3 4
                    7 |       6
                    ^         ^
            0 1 2 3 4 5

                7 |
                ^
            0 1 2 3 4 5 6

                    |
            0 1 2 3 4 5 6 7

- Así es como uniríamos dos mitades ordenadas.
- Comenzaremos desde el principio ahora con una lista de números completamente desordenada:

        5 2 7 4 1 6 3 0

    - Comenzamos mirando la primera mitad, que es una lista de tamaño 4:

            5 2 7 4

        - Tendremos que ordenar la mitad izquierda, que es una lista de tamaño 2:

                    5 2

            - La mitad izquierda es de tamaño 1, por lo que hemos terminado, y la mitad derecha también es de tamaño 1, por lo que podemos fusionar ambas mitades:

                        2 5

        - Ahora tendremos que ordenar la mitad derecha:

                    7 4

            - Nuevamente, fusionaremos ambas mitades, tomando el elemento más pequeño de cada lista.

                        4 7

        - Ahora hemos clasificado ambas mitades, cada una de tamaño 2, y podemos fusionarlas:

                    2 5 | 4 7
                    ^     ^

                    5 | 4 7
                    ^   ^
                    2

                    5 |   7
                    ^     ^
                    2 4

                    |   7
                        ^
                    2 4 5

                    2 4 5 7

    - Repetiremos esto para la mitad derecha, otra lista de tamaño 4:

            1 6 3 0

        - Ordenar la mitad izquierda nos da 1 6, y la mitad derecha se fusiona con 0 3.
        - Los fusionaremos con:

                1 6 | 0 3
                ^     ^

                1 6 |   3
                ^       ^
                0

                6 |   3
                ^     ^
                0 1

                6 |
                ^
                0 1 3 

                0 1 3 6

        - Ahora, tenemos dos mitades ordenadas, 2 4 5 7 y 0 1 3 6, que podemos fusionar como vimos arriba.
- Cada vez que fusionamos dos mitades, solo necesitábamos mirar cada número una vez. Y dividimos nuestra lista de 8 números tres veces, o log(n) veces. Necesitábamos más memoria para fusionar nuestras nuevas listas, pero el límite superior para el tiempo de ejecución de la ordenación por fusión es solo O(n*log(n)) ya que log(n) es menos que n, O(n*log(n))es menos que  O(n²).
- El límite inferior de nuestro ordenamiento por fusión sigue siendo X(n*log(n)), ya que tenemos que hacer todo el trabajo aunque la lista esté ordenada. Entonces asi funciona también tiene U(n*log(n)).
- Observamos una [visualización final](https://www.youtube.com/watch?v=ZZuD6iUe3Pc) de algoritmos de clasificación con una mayor cantidad de entradas, ejecutándose al mismo tiempo.

