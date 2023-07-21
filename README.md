# examenjef
Jefferson Chuquimarca
2. Hacer un programa que muestre 3 números ordenados desendentemente, utilizar un
procedimiento para cada operación
#include <iostream>
using namespace std;

// Procedimiento para intercambiar dos números
void intercambiar(int& a, int& b) {
    int temp = a;
    a = b;
    b = temp;
}

// Procedimiento para ordenar tres números de forma descendente
void ordenarDescendente(int& a, int& b, int& c) {
    if (a < b) {
        intercambiar(a, b);
    }
    if (a < c) {
        intercambiar(a, c);
    }
    if (b < c) {
        intercambiar(b, c);
    }
}

int main() {
    int num1, num2, num3;

    cout << "Ingrese el primer número: ";
    cin >> num1;
    cout << "Ingrese el segundo número: ";
    cin >> num2;
    cout << "Ingrese el tercer número: ";
    cin >> num3;

    ordenarDescendente(num1, num2, num3);

    cout << "Números ordenados de forma descendente: " << num1 << ", " << num2 << ", " << num3 << endl;

    return 0;
}

3. Hace un programa que muestre 3 números ordenados de ascendentemente,
utilizar un procedimiento para cada operación
#include <iostream>
using namespace std;

// Procedimiento para intercambiar dos números
void intercambiar(int& a, int& b) {
    int temp = a;
    a = b;
    b = temp;
}

// Procedimiento para ordenar tres números de forma ascendente
void ordenarAscendente(int& a, int& b, int& c) {
    if (a > b) {
        intercambiar(a, b);
    }
    if (a > c) {
        intercambiar(a, c);
    }
    if (b > c) {
        intercambiar(b, c);
    }
}

int main() {
    int num1, num2, num3;

    cout << "Ingrese el primer número: ";
    cin >> num1;
    cout << "Ingrese el segundo número: ";
    cin >> num2;
    cout << "Ingrese el tercer número: ";
    cin >> num3;

    ordenarAscendente(num1, num2, num3);

    cout << "Números ordenados de forma ascendente: " << num1 << ", " << num2 << ", " << num3 << endl;

    return 0;
}
4. Hacer un programa que muestre una tabla de multiplicar hasta el 20 de un número
cualquiera por pantalla, el número se pedirá en el programa principal. Usar procedimiento
#include <iostream>
using namespace std;

// Procedimiento para mostrar la tabla de multiplicar de un número hasta el 20
void mostrarTablaMultiplicar(int numero) {
    cout << "Tabla de multiplicar del " << numero << ":" << endl;
    for (int i = 1; i <= 20; i++) {
        cout << numero << " x " << i << " = " << numero * i << endl;
    }
}

int main() {
    int numero;

    cout << "Ingrese un número: ";
    cin >> numero;

    mostrarTablaMultiplicar(numero);

    return 0;
}
5. Hacer un programa que pida por pantalla una temperatura en grados Celsius,
muestre un menú para convertirlos a Fahrenheit o Kelvin y muestre el equivalente por
pantalla, utilizar funciones.
#include <iostream>
using namespace std;

// Función para convertir grados Celsius a grados Fahrenheit
double celsiusToFahrenheit(double celsius) {
    return (celsius * 9/5) + 32;
}

// Función para convertir grados Celsius a grados Kelvin
double celsiusToKelvin(double celsius) {
    return celsius + 273.15;
}

int main() {
    double temperaturaCelsius;

    cout << "Ingrese la temperatura en grados Celsius: ";
    cin >> temperaturaCelsius;

    cout << "Seleccione la opción de conversión:" << endl;
    cout << "1. Convertir a grados Fahrenheit" << endl;
    cout << "2. Convertir a grados Kelvin" << endl;

    int opcion;
    cout << "Ingrese su opción: ";
    cin >> opcion;

    double temperaturaConvertida;

    switch(opcion) {
        case 1:
            temperaturaConvertida = celsiusToFahrenheit(temperaturaCelsius);
            cout << "La temperatura equivalente en grados Fahrenheit es: " << temperaturaConvertida << endl;
            break;
        case 2:
            temperaturaConvertida = celsiusToKelvin(temperaturaCelsius);
            cout << "La temperatura equivalente en grados Kelvin es: " << temperaturaConvertida << endl;
            break;
        default:
            cout << "Opción inválida." << endl;
            break;
    }

    return 0;
}
6. Utilizar la función fopen(), para determinar si existe un archivo de texto (.txt)
o no.
fopen(nombre de archivo , modo);
nombre de archivo = cadena ... contiene el identificar externo del archivo
modo = cadena ... contiene el modo en que va a ser tratado el archivo
#include <iostream>
using namespace std;

int main() {
    const char* nombreArchivo = "archivo.txt";
    FILE* archivo = fopen(nombreArchivo, "r");

    if (archivo) {
        cout << "El archivo existe." << endl;
        fclose(archivo);
    } else {
        cout << "El archivo no existe." << endl;
    }

    return 0;
}
7. Crear un archivo de texto (.txt), donde guardar los emails de amigos.
fprintf(puntero, informacion);
fwrite(dato a guardar, tamaño, longitud, puntero)
#include <stdio.h>

int main() {
    FILE* archivo = fopen("emails.txt", "w");

    if (archivo) {
        fprintf(archivo, "amigo1@example.com\n");
        fprintf(archivo, "amigo2@example.com\n");
        fprintf(archivo, "amigo3@example.com\n");

        fclose(archivo);
        printf("Se han guardado los emails en el archivo.\n");
    } else {
        printf("No se pudo crear el archivo.\n");
    }

    return 0;
}
8. Crear un programa en C++, que pueda seguir agregando contactos de email, hacia el
archivo que creamos en el ejercicio 7
#include <iostream>
#include <fstream>
using namespace std;

int main() {
    ofstream archivo("emails.txt", ios::app); // Abrir el archivo en modo "append"

    if (archivo.is_open()) {
        char opcion;

        do {
            string email;

            cout << "Ingrese el email del contacto: ";
            cin >> email;

            archivo << email << endl; // Agregar el email al archivo

            cout << "¿Desea agregar otro contacto? (S/N): ";
            cin >> opcion;
        } while (opcion == 'S' || opcion == 's');

        archivo.close();
        cout << "Los contactos han sido agregados al archivo." << endl;
    } else {
        cout << "No se pudo abrir el archivo." << endl;
    }

    return 0;
}
9. Hacer una estructura llamada alumno, en la cual se tendrán los siguientes
Campos: Nombre, edad, promedio, pedir datos al usuario para 3 alumnos, comprobar cuál
de los 3 tiene el mejor promedio y posteriormente imprimir los datos del alumno
#include <iostream>
using namespace std;

struct alumno {
    string nombre;
    int edad;
    float promedio;
};

int main() {
    alumno alumnos[3];

    for (int i = 0; i < 3; i++) {
        cout << "Ingrese el nombre del alumno " << i + 1 << ": ";
        cin >> alumnos[i].nombre;
        cout << "Ingrese la edad del alumno " << i + 1 << ": ";
        cin >> alumnos[i].edad;
        cout << "Ingrese el promedio del alumno " << i + 1 << ": ";
        cin >> alumnos[i].promedio;
        cout << endl;
    }

    int indiceMejorPromedio = 0;
    float mejorPromedio = alumnos[0].promedio;

    for (int i = 1; i < 3; i++) {
        if (alumnos[i].promedio > mejorPromedio) {
            mejorPromedio = alumnos[i].promedio;
            indiceMejorPromedio = i;
        }
    }

    cout << "El alumno con el mejor promedio es:" << endl;
    cout << "Nombre: " << alumnos[indiceMejorPromedio].nombre << endl;
    cout << "Edad: " << alumnos[indiceMejorPromedio].edad << endl;
    cout << "Promedio: " << alumnos[indiceMejorPromedio].promedio << endl;

    return 0;
}
10. Pedir al usuario que digite una palabra. luego mostrar la palabra invertida y
comprobar si es capicúa
#include <iostream>
#include <string>
using namespace std;

bool esPalindromo(const string& palabra) {
    int longitud = palabra.length();
    for (int i = 0; i < longitud / 2; i++) {
        if (palabra[i] != palabra[longitud - i - 1]) {
            return false;
        }
    }
    return true;
}

string invertirPalabra(const string& palabra) {
    string palabraInvertida = palabra;
    int longitud = palabra.length();
    for (int i = 0; i < longitud / 2; i++) {
        char temp = palabraInvertida[i];
        palabraInvertida[i] = palabraInvertida[longitud - i - 1];
        palabraInvertida[longitud - i - 1] = temp;
    }
    return palabraInvertida;
}

int main() {
    string palabra;

    cout << "Ingrese una palabra: ";
    cin >> palabra;

    string palabraInvertida = invertirPalabra(palabra);

    cout << "Palabra invertida: " << palabraInvertida << endl;

    if (esPalindromo(palabra)) {
        cout << "La palabra es un palíndromo." << endl;
    } else {
        cout << "La palabra no es un palíndromo." << endl;
    }

    return 0;
}
11 CONSTRUCCIÓN DE LA PLANTILLA PARA EL PROGRAMA MENU FUNCIONES CON
SWITCH CASE
#include <iostream>
using namespace std;

// Declaración de funciones
void opcion1();
void opcion2();
void opcion3();

int main() {
    int opcion;

    do {
        // Mostrar el menú de opciones
        cout << "MENU DE OPCIONES" << endl;
        cout << "1. Opción 1" << endl;
        cout << "2. Opción 2" << endl;
        cout << "3. Opción 3" << endl;
        cout << "4. Salir" << endl;
        cout << "Ingrese su opción: ";
        cin >> opcion;

        // Ejecutar la opción seleccionada
        switch (opcion) {
            case 1:
                opcion1();
                break;
            case 2:
                opcion2();
                break;
            case 3:
                opcion3();
                break;
            case 4:
                cout << "Saliendo del programa..." << endl;
                break;
            default:
                cout << "Opción inválida. Intente nuevamente." << endl;
                break;
        }
    } while (opcion != 4);

    return 0;
}

// Definición de las funciones de cada opción
void opcion1() {
    cout << "Ha seleccionado la Opción 1." << endl;
    // Lógica de la Opción 1
}

void opcion2() {
    cout << "Ha seleccionado la Opción 2." << endl;
    // Lógica de la Opción 2
}

void opcion3() {
    cout << "Ha seleccionado la Opción 3." << endl;
    // Lógica de la Opción 3
}
