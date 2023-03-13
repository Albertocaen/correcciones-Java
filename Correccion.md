# Correcciones de Java

## Ejercicio 1 del examen 

### Codigo a corregir 
- El código anterior no sigue la Regla #6 "Las funciones deben ser pequeñas". La función main tiene varias responsabilidades, como pedir un código SWIFT, verificar si el código es válido, obtener el país y la localidad del código SWIFT y mostrarlos en la salida, así como también preguntar al usuario si desea continuar o salir del programa.
- El codigo anterior no sigue la regla 7: "Haz una única cosa". El código original tenía una mezcla de responsabilidades, ya que además de pedir el código, comprobar su validez y mostrar el país y la localidad, también tenía la responsabilidad de preguntar si el usuario quería salir del programa
```  codigo a corregir

package examen22;

import java.util.Scanner;

public class Ejercicio01 {
    static Scanner sc = new Scanner(System.in);
    public static void main(String[] args) {
        String salir = "";
        do {
            // Crea un programa que pida un código y
            String codigoSwift = pedirCodigo();
            // comprobamos si el código es correcto
            // si el código no tiene 8 ni 11 caracteres, es incorrecto
            if (codigoSwift.length() != 8 && codigoSwift.length() != 11) {
                System.out.println("El número de caracteres introducidos (" +
                        +codigoSwift.length() + ") no es correcto.\nUn código SWIFT tiene 8 u 11 caracteres.");
            } else {
//  Si el número de dígitos es correcto,
//  debe mostrar el país de procedencia
                String país = codigoSwift.substring(4, 6);
                System.out.println("País: " + país);
//  y, si la localidad es “MM”, indicar si es Madrid o Moscú.
                String localidad = codigoSwift.substring(6, 8);
                //System.out.println(localidad);
                if (localidad.equals("MM")) {
                    if (país.equals("ES")) {
                        System.out.println("Localidad: Madrid");
                    } else {
                        System.out.println("Localidad: Moscú");
                    }
                }
            }
//  En los demás casos no se mostrará la localidad.
                System.out.println("¿Quieres salir? (s/n)");
                salir = sc.nextLine().substring(0, 1);
            } while (salir.equalsIgnoreCase("n")) ;

//            Implementa un bucle en el programa de forma que podamos repetir esta acción en la misma ejecución del programa, metiendo códigos hasta que le indiquemos al programa que queremos salir. --> DO WHILE ENGLOBANDO TODO LO HECHO HASTA EL MOMENTO
    }

    public static String pedirCodigo() {
        System.out.println("Código:");
        String codigo = sc.nextLine();
        return codigo;
    }
}
``` 
En esta corrección, he separado la lógica del programa en varias funciones más pequeñas y específicas, eliminando así la sobrecarga de responsabilidades en la función main(). He creado una función procesarCodigo()
que se encarga de procesar el código SWIFT y mostrar el país y la localidad correspondientes. También he creado funciones adicionales para obtener el país y la localidad a partir del código SWIFT, así como para mostrar el país y la localidad en la salida.

### Codigo Corregido 
``` 

package examen22;

import java.util.Scanner;

public class Ejercicio01 {
static Scanner sc = new Scanner(System.in);
public static void main(String[] args) {
String salir = "";
do {
String codigoSwift = pedirCodigo();
procesarCodigo(codigoSwift);
salir = preguntarSalir();
} while (salir.equalsIgnoreCase("n"));
}

public static String pedirCodigo() {
System.out.println("Código:");
String codigo = sc.nextLine();
return codigo;
}

public static void procesarCodigo(String codigoSwift) {
if (codigoSwift.length() != 8 && codigoSwift.length() != 11) {
System.out.println("El número de caracteres introducidos (" +
+codigoSwift.length() + ") no es correcto.\nUn código SWIFT tiene 8 u 11 caracteres.");
return;
}
String país = obtenerPaís(codigoSwift);
String localidad = obtenerLocalidad(codigoSwift);
mostrarPaís(país);
mostrarLocalidad(localidad, país);
}

public static String obtenerPaís(String codigoSwift) {
return codigoSwift.substring(4, 6);
}

public static String obtenerLocalidad(String codigoSwift) {
return codigoSwift.substring(6, 8);
}

public static void mostrarPaís(String país) {
System.out.println("País: " + país);
}

public static void mostrarLocalidad(String localidad, String país) {
if (localidad.equals("MM")) {
if (país.equals("ES")) {
System.out.println("Localidad: Madrid");
} else {
System.out.println("Localidad: Moscú");
}
}
}

public static String preguntarSalir() {
System.out.println("¿Quieres salir? (s/n)");
return sc.nextLine().substring(0, 1);
}
} 
```



