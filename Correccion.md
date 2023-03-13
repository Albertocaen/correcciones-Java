# Correcciones de Java

## Ejercicio 1 del examen 

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
```json

```



