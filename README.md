Actividades por desarrollar
Implementar listas simplemente enlazadas circular como primer proyecto lo siguiente:
1.	Crear un programa en java que permita Invertir una cadena usando una Pila. - Este programa leerá una cadena de texto ingresada por el usuario, utilizará una pila para invertir la cadena y luego mostrará la cadena invertida. Ejemplo Ingresa “ESTUDIANTES”, mostrará “SETNAIDUTSE”
import java.util.Scanner;
import java.util.Stack;

public class InvertirCadenaConPila {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Leer la cadena de texto ingresada por el usuario
        System.out.print("Ingrese una cadena de texto: ");
        String input = scanner.nextLine();

        // Crear una pila para almacenar los caracteres
        Stack<Character> pila = new Stack<>();

        // Empujar todos los caracteres en la pila
        for (char c : input.toCharArray()) {
            pila.push(c);
        }

        // Extraer los caracteres de la pila para formar la cadena invertida
        StringBuilder cadenaInvertida = new StringBuilder();
        while (!pila.isEmpty()) {
            cadenaInvertida.append(pila.pop());
        }

        // Mostrar la cadena invertida
        System.out.println("Cadena invertida: " + cadenaInvertida.toString());

        scanner.close();
    }
}
Ingrese una cadena de texto: ESTUDIANTES
Cadena invertida: SETNAIDUTSE

=== Code Execution Successful ===
2.-Crea un programa que permita ingresar 10 valores en una Cola y luego muestre la Cola ordenada en forma ascendente.
import java.util.LinkedList;
import java.util.Queue;
import java.util.Scanner;
import java.util.PriorityQueue;

public class ColaOrdenada {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Crear una cola para almacenar los valores
        Queue<Integer> cola = new LinkedList<>();

        // Leer 10 valores ingresados por el usuario
        System.out.println("Ingrese 10 valores:");
        for (int i = 0; i < 10; i++) {
            System.out.print("Valor " + (i + 1) + ": ");
            int valor = scanner.nextInt();
            cola.add(valor);
        }

        // Crear una cola de prioridad para ordenar los valores en forma ascendente
        PriorityQueue<Integer> colaOrdenada = new PriorityQueue<>(cola);

        // Mostrar la cola ordenada
        System.out.println("Cola ordenada en forma ascendente:");
        while (!colaOrdenada.isEmpty()) {
            System.out.print(colaOrdenada.poll() + " ");
        }
        System.out.println();

        scanner.close();
    }
}
java -cp /tmp/BupcNh2cey/ColaOrdenada
Ingrese 10 valores:
Valor 1: 9
Valor 2: 8
Valor 3: 7
Valor 4: 6
Valor 5: 5
Valor 6: 4
Valor 7: 3
Valor 8: 2
Valor 9: 1
Valor 10: 0
Cola ordenada en forma ascendente:
0 1 2 3 4 5 6 7 8 9 

=== Code Execution Successful ===
3.Crear un programa que permita ingresar dos Colas de enteros por separado, además deberá ordenarlas de menor a mayor y que devuelva una nueva Cola como unión de ambas con sus elementos ordenados de la misma forma.
import java.util.LinkedList;
import java.util.Queue;
import java.util.Scanner;
import java.util.PriorityQueue;

public class ColasOrdenadas {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Crear dos colas para almacenar los valores
        Queue<Integer> cola1 = new LinkedList<>();
        Queue<Integer> cola2 = new LinkedList<>();

        // Leer valores para la primera cola
        System.out.println("Ingrese los valores para la primera cola (separados por espacios): ");
        String[] valores1 = scanner.nextLine().split(" ");
        for (String valor : valores1) {
            cola1.add(Integer.parseInt(valor));
        }

        // Leer valores para la segunda cola
        System.out.println("Ingrese los valores para la segunda cola (separados por espacios): ");
        String[] valores2 = scanner.nextLine().split(" ");
        for (String valor : valores2) {
            cola2.add(Integer.parseInt(valor));
        }

        // Ordenar ambas colas usando PriorityQueue
        PriorityQueue<Integer> colaOrdenada1 = new PriorityQueue<>(cola1);
        PriorityQueue<Integer> colaOrdenada2 = new PriorityQueue<>(cola2);

        // Mostrar la primera cola ordenada
        System.out.println("Primera cola ordenada: ");
        while (!colaOrdenada1.isEmpty()) {
            System.out.print(colaOrdenada1.poll() + " ");
        }
        System.out.println();

        // Mostrar la segunda cola ordenada
        System.out.println("Segunda cola ordenada: ");
        while (!colaOrdenada2.isEmpty()) {
            System.out.print(colaOrdenada2.poll() + " ");
        }
        System.out.println();

        scanner.close();
    }
}
Ingrese los valores para la primera cola (separados por espacios): 
2 3 4 5 6 7
Ingrese los valores para la segunda cola (separados por espacios): 
1 7 8 9 0 
Primera cola ordenada: 
2 3 4 5 6 7 
Segunda cola ordenada: 
0 1 7 8 9 
.-Diseñe un programa en java que permita el ingreso de 10 números (entre cero y diez) de forma desordenada en una pila, luego el programa imprima en letra el número que contiene la pila, Ejemplo:
import java.util.Scanner;
import java.util.Stack;

public class NumerosEnLetra {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Crear una pila para almacenar los números
        Stack<Integer> pila = new Stack<>();

        // Leer los 10 números ingresados por el usuario
        System.out.println("Ingrese 10 números (entre cero y diez):");
        for (int i = 0; i < 10; i++) {
            System.out.print("Número " + (i + 1) + ": ");
            int numero = scanner.nextInt();
            if (numero >= 0 && numero <= 10) {
                pila.push(numero);
            } else {
                System.out.println("Número no válido. Por favor, ingrese un número entre cero y diez.");
                i--; // Decrementar el contador para volver a solicitar el número
            }
        }

        // Imprimir en letra el número contenido en la pila
        System.out.println("Números en letra:");
        while (!pila.isEmpty()) {
            int numero = pila.pop();
            String numeroEnLetra = convertirNumeroEnLetra(numero);
            System.out.println(numeroEnLetra);
        }

        scanner.close();
    }

    // Método para convertir un número en letra
    public static String convertirNumeroEnLetra(int numero) {
        switch (numero) {
            case 0: return "cero";
            case 1: return "uno";
            case 2: return "dos";
            case 3: return "tres";
            case 4: return "cuatro";
            case 5: return "cinco";
            case 6: return "seis";
            case 7: return "siete";
            case 8: return "ocho";
            case 9: return "nueve";
            case 10: return "diez";
            default: return "";
        }
    }
}
Ingrese 10 números (entre cero y diez):
Número 1: 5
Número 2: 8
Número 3: 3
Número 4: 11
Número no válido. Por favor, ingrese un número entre cero y diez.
Número 4: 7
Número 5: 2
Número 6: 0
Número 7: 9
Número 8: 4
Número 9: 10
Número 10: 1
Números en letra:
uno
diez
cuatro
nueve
cero
dos
siete
tres
ocho
cinco






