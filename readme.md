# Gestor de Vuelos en C++ · POO y Grafos

<p align="center">
  <img src="https://img.shields.io/badge/C++-OOP-00599C?style=for-the-badge&logo=cplusplus&logoColor=white" alt="C++ OOP" />
  <img src="https://img.shields.io/badge/CLI-Application-111827?style=for-the-badge&logo=gnubash&logoColor=white" alt="CLI Application" />
  <img src="https://img.shields.io/badge/Makefile-Build-374151?style=for-the-badge" alt="Makefile" />
  <img src="https://img.shields.io/badge/Academic%20Project-UAB-38BDF8?style=for-the-badge" alt="Academic Project UAB" />
</p>

Aplicación de consola desarrollada en **C++** para gestionar vuelos, pilotos, pasajeros y estructuras relacionadas, aplicando conceptos de **programación orientada a objetos**, gestores, arrays reservados, ficheros, templates y grafos.

El proyecto fue desarrollado como práctica universitaria y como refuerzo personal antes de empezar segundo curso de Ingeniería Informática, con el objetivo de mejorar la base en C++, diseño de clases, organización de código y gestión manual de estructuras.

---

## Objetivos del proyecto

* Practicar **programación orientada a objetos** en C++.
* Crear diferentes gestores para manejar colecciones de objetos.
* Trabajar con **arrays reservados** y control manual de memoria.
* Implementar un gestor de vuelos usando estructuras propias.
* Practicar el uso de **templates** para reutilizar lógica de ordenación.
* Introducir una clase para trabajar con **grafos**.
* Mejorar la organización del proyecto mediante **Makefile**.
* Utilizar ficheros con `<fstream>` para cargar datos.

---

## Funcionalidades principales

* Crear vuelos.
* Mostrar vuelos registrados.
* Modificar vuelos.
* Eliminar vuelos.
* Ordenar vuelos por diferentes criterios.
* Gestionar pilotos y pasajeros.
* Cargar información de pilotos desde archivo `.txt`.
* Estructurar el proyecto con clases y gestores.
* Compilar el proyecto en Windows y macOS mediante Makefile.

---

## Conceptos trabajados

| Área                             | Conceptos aplicados                                               |
| -------------------------------- | ----------------------------------------------------------------- |
| Programación orientada a objetos | Clases, constructores, setters, getters, composición              |
| Memoria y estructuras            | Arrays reservados, inicialización, eliminación y desplazamiento   |
| C++                              | Templates, punteros a funciones miembro, ficheros con `<fstream>` |
| Organización                     | Separación en `.h` y `.cpp`, Makefile, estructura de carpetas     |
| Algoritmos y datos               | Ordenación, gestores, primeros pasos con grafos                   |
| CLI                              | Menús en consola e interacción con el usuario                     |

---

## Diseño del proyecto

El proyecto se organiza alrededor de diferentes clases y gestores.

La idea principal es separar la responsabilidad de los objetos individuales de la gestión de colecciones. Por ejemplo, un vuelo representa una entidad concreta, mientras que `CGestorVuelos` se encarga de gestionar el conjunto de vuelos.

También se utiliza composición en algunas clases. Por ejemplo, `CPiloto` y `CPasajero` contienen internamente un objeto `CPersona`, en lugar de heredar directamente de él.

```cpp
CPersona piloto;
```

Esta decisión permite practicar composición y separar mejor las responsabilidades, aunque en otros diseños también podría estudiarse el uso de herencia y polimorfismo.

---

## Estructura esperada del proyecto

```txt
.
├── src/                  # Archivos .cpp principales
├── include/              # Archivos .h / headers
├── data/                 # Archivos de datos, como pilotos.txt
├── Makefile              # Compilación principal
├── Makefile_MacOS        # Compilación para macOS, si aplica
└── README.md
```

La estructura puede variar según la versión actual del repositorio, pero el objetivo es mantener el código separado, legible y fácil de compilar.

---

## Instalación y compilación

### Windows

Para compilar el proyecto en Windows es recomendable tener instalado **MSYS2** y configurar el compilador de C++ en Visual Studio Code.

Guía oficial:

```txt
https://code.visualstudio.com/docs/cpp/config-mingw
```

Después de instalar MSYS2 y configurar el entorno, compila el proyecto usando el Makefile correspondiente.

```bash
make
```

Si el proyecto incluye un Makefile específico para Windows, utiliza ese archivo según la configuración del repositorio.

---

### macOS

Desde la raíz del proyecto:

```bash
make distclean
find . -name "*.o" -delete
find . -name "*.d" -delete
make -f Makefile_MacOS
```

Si ya existe un Makefile unificado para Windows/macOS, se puede usar:

```bash
make
```

---

## Ejecución

Una vez compilado el proyecto, ejecuta el binario generado desde la terminal.

Ejemplo:

```bash
./main
```

En Windows puede generarse un ejecutable `.exe`:

```bash
main.exe
```

El programa mostrará un menú en consola desde el que se podrán ejecutar las diferentes operaciones disponibles.

---

## Notas importantes

* Los arrays reservados deben inicializarse correctamente para evitar errores como `segmentation fault`.
* Si se usa memoria dinámica, hay que controlar bien la creación, eliminación y reasignación de elementos.
* Algunos errores iniciales aparecieron al ordenar y eliminar elementos de arrays, por lo que se corrigieron desplazamientos y accesos inválidos.
* La clase `CCadena` utilizada inicialmente procede de material universitario de la UAB.
* En futuras versiones sería interesante reemplazarla por una implementación propia o por `std::string`, según el objetivo académico del proyecto.
* Actualmente se trabaja con composición en lugar de herencia en ciertas clases, como `CPiloto` y `CPasajero`.

---

## Posibles mejoras

* Crear una implementación propia de `CCadena`.
* Mejorar la validación de entradas del usuario.
* Controlar errores cuando se introduce texto en campos numéricos.
* Validar correctamente DNI y otros datos personales.
* Comprobar capacidad antes de añadir pilotos, pasajeros o vuelos.
* Implementar excepciones para entradas inválidas.
* Cancelar vuelos automáticamente si se elimina un piloto asignado.
* Mejorar la persistencia de datos mediante archivos.
* Reactivar y mejorar el uso de arrays reservados dinámicos.
* Añadir tests básicos para comprobar las operaciones principales.
* Documentar mejor la clase de grafos y sus posibles usos dentro del sistema.

---

## Evolución del proyecto

### v0.1

* Primera subida del proyecto.
* Implementación inicial de constructores y constructores por defecto.
* Definición de valores por defecto para algunos objetos.

### v0.2

* Creación inicial de la interfaz por consola.
* Añadido menú principal para llamar a las funciones.
* Integración de la clase `CCadena` proporcionada en el entorno universitario.
* Organización inicial de tareas pendientes mediante TODOs en Visual Studio Code.

### v0.3

* Creación de la clase `CGestorVuelos`.
* Separación de la lógica de gestión respecto a la clase `CVuelo`.
* Implementación de funciones para crear, mostrar, eliminar y modificar vuelos.

### v0.4

* Mejora del README.
* Corrección de setters de `CVuelo`.
* Corrección de errores al ordenar por ID, precio y duración.
* Corrección de errores al eliminar elementos del array.
* Mejora de funciones de organización con arrays estáticos.

### v0.5

* Reutilización de lógica de ordenación mediante templates.
* Uso de punteros a funciones miembro para ordenar por diferentes criterios.

Ejemplo conceptual:

```cpp
gestor.ordenar(&CVuelo::getId);
```

* Planificación de futuras mejoras para gestionar pasajeros, aviones y vuelos con arrays dinámicos.

### v0.5.1

* Corrección de errores menores.
* Reducción de warnings por consola.

### v0.6

* Mejora del Makefile.
* Reorganización de archivos.
* Uso de `<fstream>` para cargar pilotos desde archivo.
* Los pilotos pasan a recogerse desde un `.txt`.
* Deshabilitación temporal del array reservado dinámico para futuras mejoras.

### v0.6.1 - v0.6.2

* Mejora del `main`.
* Limpieza de consola adaptada a Windows y macOS.
* Modificación del Makefile para facilitar la compilación en ambos sistemas.

---

## FAQ

### ¿Por qué se ha desarrollado este proyecto?

Este proyecto se desarrolló como práctica universitaria y como ejercicio personal para reforzar conceptos fundamentales de C++ antes de avanzar a proyectos más complejos.

### ¿Qué lo diferencia de un CRUD simple?

Aunque parte de operaciones básicas como crear, mostrar, modificar y eliminar vuelos, el objetivo principal es practicar conceptos de bajo nivel y diseño en C++: gestores, arrays reservados, composición, ficheros, templates y primeros pasos con grafos.

### ¿Es un proyecto finalizado?

No completamente. Es un proyecto académico en evolución, útil para aprender y practicar. Algunas partes están pensadas como base para futuras mejoras.

---

## Aprendizajes principales

Este proyecto me ayudó a entender mejor:

* Cómo organizar código C++ en clases y gestores.
* La importancia de inicializar correctamente arrays y memoria.
* Cómo separar responsabilidades entre entidades y gestores.
* Cómo usar ficheros para cargar datos.
* Cómo mejorar progresivamente un proyecto con versiones.
* Cómo documentar problemas, decisiones y mejoras futuras.

---

## Estado del proyecto

Proyecto académico en evolución.
Actualmente sirve como base de aprendizaje para reforzar C++, POO, estructuras de datos y organización de proyectos con Makefile.

---

## Autor

Desarrollado por **Carlos Morales Artés**.

Estudiante de Ingeniería Informática en la Universitat Autònoma de Barcelona.
