# Laboratorio 3: Clasificar

    Puede colaborar con uno o dos compañeros de clase en este laboratorio, aunque se espera que todos los estudiantes de dicho grupo contribuyan por igual al laboratorio.

Analiza tres programas de ordenación para determinar qué algoritmos utilizan.

# Antecedentes
Recordemos que en la clase vimos algunos algoritmos para ordenar una secuencia de números: ordenación por selección, ordenación por burbuja y ordenación por fusión.

- La ordenación por selección recorre las partes no ordenadas de una lista, seleccionando cada vez el elemento más pequeño y moviéndolo a su ubicación correcta.
- La ordenación por burbuja compara pares de valores adyacentes de uno en uno y los intercambia si están en el orden incorrecto. Esto continúa hasta que la lista está ordenada.
- La ordenación por fusión divide recursivamente la lista en dos repetidamente y luego fusiona las listas más pequeñas de nuevo en una más grande en el orden correcto.

# Cómo empezar
    ¿Empezó con CS50x en 2021 o antes y necesita migrar su trabajo del IDE de CS50 al nuevo espacio de código de VS Code? Asegúrese de consultar nuestras instrucciones sobre cómo [migrar](https://cs50.harvard.edu/x/2022/new/) sus archivos.

Open [VS Code](https://code.cs50.io/).

Comience por hacer clic dentro de su ventana de terminal, luego ejecute cd por sí mismo. Debería encontrar que su "prompt" se parece al de abajo.

    $

Haz clic dentro de esa ventana de terminal y luego ejecuta

    wget https://cdn.cs50.net/2021/fall/labs/3/sort.zip

seguido de Enter para descargar un ZIP llamado sort.zip en su espacio de código. Tenga cuidado de no pasar por alto el espacio entre wget y la siguiente URL, o cualquier otro carácter.

Ahora ejecuta

    unzip sort.zip

para crear una carpeta llamada sort. Ya no necesitas el archivo ZIP, así que puedes ejecutar

    rm sort.zip

y responda con "y" seguido de "Enter" en la pregunta para eliminar el archivo ZIP que ha descargado.

Ahora escriba

    cd sort

seguido de Enter para entrar en ese directorio (es decir, abrirlo). El indicador debería parecerse al siguiente.

    sort/ $

Si todo ha ido bien, deberías ejecutar

    ls

y deberías ver una colección de archivos .txt junto a los programas ejecutables sort1, sort2 y sort3.

Si tiene algún problema, vuelva a seguir estos mismos pasos y vea si puede determinar en qué se equivocó.

# Instrucciones

Te proporcionamos tres programas en C ya compilados, sort1, sort2 y sort3. Cada uno de estos programas implementa un algoritmo de ordenación diferente: ordenación por selección, ordenación por burbuja o ordenación por fusión (¡aunque no necesariamente en ese orden!). Tu tarea es determinar qué algoritmo de ordenación utiliza cada archivo.

- sort1, sort2 y sort3 son archivos binarios, por lo que no podrá ver el código fuente en C de cada uno. Para evaluar qué ordenación implementa cada algoritmo, ejecute las ordenaciones en diferentes listas de valores.
- Se le proporcionan múltiples archivos .txt. Estos archivos contienen n líneas de valores, ya sea invertidos, barajados u ordenados.
    - Por ejemplo, reversed10000.txt contiene 10000 líneas de números que están invertidos de 10000, mientras que random10000.txt contiene 10000 líneas de números que están en orden aleatorio.
- Para ejecutar la ordenación de los archivos de texto, en el terminal, ejecute ./[nombre_del_programa] [archivo_de_texto.txt]. Asegúrese de que ha utilizado cd para entrar en el directorio de clasificación.
    - Por ejemplo, para ordenar reversed10000.txt con sort1, ejecute ./sort1 reversed10000.txt.
- Puede resultarle útil cronometrar sus ordenaciones. Para ello, ejecute time ./[archivo_de_ordenación] [archivo_de_texto.txt].
    - Por ejemplo, puede ejecutar time ./sort1 reversed10000.txt para ejecutar sort1 en 10.000 números invertidos. Al final de la salida de tu terminal, puedes mirar el tiempo real para ver cuánto tiempo transcurrió realmente mientras se ejecutaba el programa.
- Registra tus respuestas en answers.txt, junto con una explicación para cada programa, rellenando los espacios en blanco marcados como TODO.

# Recorrido

    Este vídeo se grabó cuando el curso todavía utilizaba el IDE CS50 para escribir código. Aunque la interfaz puede parecer diferente a la de su espacio de código, el comportamiento de los dos entornos debería ser muy similar.

[Video](https://www.youtube.com/watch?v=-Bhxxw6JKKY&t=6s)

# Consejos

- Los diferentes tipos de archivos .txt pueden ayudarle a determinar cuál es la clasificación. Considera cómo funciona cada algoritmo con una lista ya ordenada. ¿Qué tal una lista invertida? ¿O con una lista barajada? Puede ser útil trabajar con una lista más pequeña de cada tipo y recorrer cada proceso de ordenación.

# Cómo comprobar sus respuestas

Ejecuta lo siguiente para evaluar la corrección de tus respuestas usando check50. Pero asegúrate de rellenar también tus explicaciones, que check50 no comprobará aquí.

    check50 cs50/labs/2022/x/sort

# Cómo presentarse

En su terminal, ejecute lo siguiente para enviar su trabajo.

    submit50 cs50/labs/2022/x/sort