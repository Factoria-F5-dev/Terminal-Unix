
# Clase sobre la Terminal Unix

## Índice

1. [Introducción](#1-introducción)
2. [Conceptos Fundamentales](#2-conceptos-fundamentales)
3. [Comandos Esenciales](#3-comandos-esenciales)
4. [Navegación y Manipulación de Archivos](#4-navegación-y-manipulación-de-archivos)
5. [Permisos y Usuarios](#5-permisos-y-usuarios)
6. [Redirección y Tuberías](#6-redirección-y-tuberías)
7. [Ejercicio Práctico](#7-ejercicio-práctico)
8. [Recursos Adicionales](#8-recursos-adicionales)

---

## 1. Introducción

La terminal Unix es una poderosa interfaz de línea de comandos que permite a los usuarios interactuar directamente con el sistema operativo. Dominar la terminal es esencial para cualquier desarrollador o administrador de sistemas.

🚀 La terminal Unix proporciona acceso directo a las funciones del sistema operativo, permitiendo realizar tareas complejas de manera eficiente.

👨‍💻 Desarrollada originalmente para los sistemas Unix en los años 70, la interfaz de línea de comandos ha evolucionado pero mantiene su potencia y flexibilidad en los sistemas modernos.

💻 Aunque las interfaces gráficas de usuario (GUI) son comunes hoy en día, la terminal sigue siendo indispensable para tareas avanzadas, automatización y desarrollo de software.

🚨 ¿Entendemos por qué es importante aprender a usar la terminal? ¿Qué ventajas ofrece sobre las interfaces gráficas? 🚨

## 2. Conceptos Fundamentales

📁 **Directorio**: Equivalente a una carpeta en una interfaz gráfica.

📄 **Archivo**: Unidad básica de almacenamiento en un sistema Unix.

🔗 **Ruta**: Ubicación de un archivo o directorio en el sistema de archivos.

👤 **Usuario**: Entidad que interactúa con el sistema.

🔐 **Permisos**: Controlan el acceso a archivos y directorios.

🔧 **Shell**: Intérprete de comandos que procesa las instrucciones del usuario.

## 3. Comandos Esenciales

- `ls`: Lista el contenido de un directorio.
- `cd`: Cambia el directorio actual.
- `pwd`: Muestra el directorio de trabajo actual.
- `mkdir`: Crea un nuevo directorio.
- `touch`: Crea un nuevo archivo vacío.
- `cp`: Copia archivos o directorios.
- `mv`: Mueve o renombra archivos o directorios.
- `rm`: Elimina archivos o directorios.
- `cat`: Muestra el contenido de un archivo.
- `grep`: Busca patrones en archivos.
- `chmod`: Cambia los permisos de un archivo o directorio.
- `sudo`: Ejecuta un comando con privilegios de superusuario.

🚨 ¿Podemos explicar para qué sirve cada uno de estos comandos? 🚨

## 4. Navegación y Manipulación de Archivos

### Navegación

```bash
cd /ruta/al/directorio    # Cambia al directorio especificado
cd ..                     # Sube un nivel en la jerarquía de directorios
cd ~                      # Va al directorio home del usuario
pwd                       # Muestra la ruta del directorio actual
```

### Manipulación de Archivos

```bash
touch archivo.txt         # Crea un nuevo archivo
cp archivo.txt copia.txt  # Copia un archivo
mv archivo.txt nuevo.txt  # Renombra o mueve un archivo
rm archivo.txt            # Elimina un archivo
mkdir nuevo_directorio    # Crea un nuevo directorio
rmdir directorio_vacio    # Elimina un directorio vacío
```

## 5. Permisos y Usuarios

Los permisos en Unix se dividen en tres categorías: propietario, grupo y otros. Cada categoría tiene permisos de lectura (r), escritura (w) y ejecución (x).

```bash
ls -l                     # Muestra los permisos de los archivos
chmod 755 archivo         # Cambia los permisos de un archivo
chown usuario:grupo archivo # Cambia el propietario y grupo de un archivo
```

## 6. Redirección y Tuberías

La redirección permite cambiar la entrada y salida estándar de los comandos.

```bash
comando > archivo.txt     # Redirige la salida a un archivo
comando >> archivo.txt    # Añade la salida al final de un archivo
comando < archivo.txt     # Usa el archivo como entrada para el comando
comando1 | comando2       # Envía la salida de comando1 como entrada a comando2
```

## 7. Ejercicio Práctico

Vamos a crear un script que cuente las palabras en un archivo de texto y muestre las 5 palabras más frecuentes.

### Paso 1: Crear un archivo de texto

Primero, crearemos un archivo de texto con algunas frases repetitivas:

```bash
echo "El zorro marrón rápido salta sobre el perro perezoso. El perro perezoso duerme todo el día. El zorro rápido corre por el bosque. El bosque es verde y frondoso." > texto.txt
```

### Paso 2: Crear el script

Ahora, crearemos un script llamado `contar_palabras.sh`:

```bash
#!/bin/bash

if [ $# -eq 0 ]; then
    echo "Uso: $0 <archivo>"
    exit 1
fi

if [ ! -f "$1" ]; then
    echo "Error: El archivo '$1' no existe."
    exit 1
fi

cat "$1" | tr '[:upper:]' '[:lower:]' | tr -s '[:space:]' '\n' | sort | uniq -c | sort -nr | head -5


```

Este script hace lo siguiente:

1. Verifica si se ha proporcionado un archivo como argumento.
2. Comprueba si el archivo existe.
3. Lee el contenido del archivo.
4. Convierte todo el texto a minúsculas.
5. Reemplaza los espacios por saltos de línea para tener una palabra por línea.
6. Ordena las palabras.
7. Cuenta las ocurrencias únicas de cada palabra.
8. Ordena el recuento de mayor a menor.
9. Muestra las 5 palabras más frecuentes.

Explicación detallada de cada comando:

- if [ $# -eq 0 ] 
    - Esta es una condición que verifica si el número de argumentos pasados al script es igual a cero.

- $# 
    - Es una variable especial que contiene el número de argumentos pasados al script.

- -eq 
    - es un operador de comparación que significa "igual a".

- then
    - Indica el inicio del bloque de código que se ejecutará si la condición es verdadera.

- echo "Uso: $0 <archivo>"
    - Imprime un mensaje de uso si no se proporcionaron argumentos.

- $0 
    - Es una variable especial que contiene el nombre del script.

- exit 1
    - Termina la ejecución del script con un código de salida 1, indicando que hubo un error.

- fi
    - Marca el final del bloque if.

- -f 
    - Es un operador de prueba que verifica si el argumento es un archivo regular.

- cat "$1"
    - Lee el contenido del archivo especificado como primer argumento

- "$1" 
    - Es una variable que contiene el primer argumento pasado al script.

- tr '[:upper:]' '[:lower:]'
    - Traduce (reemplaza) todas las letras mayúsculas a minúsculas

- tr -s '[:space:]' '\\n'
    - Reemplaza uno o más espacios consecutivos por un solo salto de línea
    - Esto pone cada palabra en una línea separada

- sort
    - Ordena las líneas alfabéticamente

- uniq -c
    - Cuenta las ocurrencias de líneas idénticas consecutivas
    - El '-c' añade un prefijo con el número de ocurrencias

- sort -nr
    - Ordena numéricamente (-n) en orden inverso (-r)
    - Esto pone las palabras más frecuentes al principio

- head -5
    - Muestra solo las primeras 5 líneas del resultado

### Paso 3: Dar permisos de ejecución al script

```bash
chmod +x contar_palabras.sh
```

### Paso 4: Ejecutar el script

```bash
./contar_palabras.sh texto.txt
```

### Resultado esperado

El resultado debería ser similar a esto:

```
      4 el
      3 perro
      2 zorro
      2 rápido
      2 perezoso
```

### Explicación del resultado

- El script ha contado correctamente las palabras en el texto.
- "el" aparece 4 veces y es la palabra más frecuente.
- "perro" aparece 3 veces.
- "zorro", "rápido" y "perezoso" aparecen 2 veces cada una.

Este ejercicio demuestra el uso de varios conceptos y comandos de Unix:

- Creación y manipulación de archivos (`echo`, `>`)
- Permisos de archivos (`chmod`)
- Redirección de entrada/salida
- Tuberías para conectar múltiples comandos
- Procesamiento de texto (`tr`, `sort`, `uniq`)

🚨 ¿Entendemos cómo funciona cada parte del script y cómo se combinan los comandos para lograr el resultado deseado? 🚨

## 8. Recursos Adicionales

- [The Linux Command Line, de William Shotts](https://www.libristo.es/es/libro/linux-command-line_20296719?gad_source=1&gclid=CjwKCAiA3Na5BhAZEiwAzrfagEd1paD4YBgfsahA8_4v4mcCKIJz7uKOZP0oORmCUlifzNsOt0wfnBoCQs0QAvD_BwE) - Un libro completo sobre la línea de comandos de Linux.
- [Explainshell](https://explainshell.com/) - Una herramienta web que explica comandos de shell.
- [Unix & Linux Stack Exchange](https://unix.stackexchange.com/) - Foro de preguntas y respuestas sobre Unix y Linux.
- [Bash Scripting Tutorial](https://linuxconfig.org/bash-scripting-tutorial-for-beginners) - Tutorial para principiantes sobre scripting en Bash.
- [RegexOne](https://regexone.com/) - Curso interactivo para aprender expresiones regulares, útiles en la línea de comandos.
- [ Terminal/shell de UNIX vídeo introductorio ](https://www.youtube.com/watch?v=GB35Eyb-J4c) 
