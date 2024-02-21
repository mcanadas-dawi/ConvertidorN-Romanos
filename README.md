# CONVERTIDOR DECIMAL-ROMANO Y ROMANO-DECIMAL
## CODE WARS 4KYU KATA
### TAREA
Haz 2 funciones, una que reciba por parametro un número decimal y lo pase a número Romano y otra función que reciba un número Romano y lo pase a decimal.
### CÓDIGO
```java
 //Decimal a Romano
public static String toRoman(int n) {

    String[] nr = {"M", "CM", "D", "CD", "C", "XC", "L", "XL", "X", "IX", "V", "IV", "I"};
    int[] nd = {1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1};

    String numeroRomano = "";

    // Iterar por los símbolos romanos
    for (int i = 0; i < nr.length; i++) {

      // Mientras el número decimal sea mayor o igual al valor actual
      while (n >= nd[i]) {

        // Añadir el símbolo actual al número romano
        numeroRomano += nr[i];
        // Restar el valor actual del número decimal
        n -= nd[i];
      }
    }

    return numeroRomano;
  }

  // Romano a decimal
  public static int fromRoman(String romanNumeral) {

    Map<Character, Integer> map = new HashMap<>();
    map.put('I', 1);
    map.put('V', 5);
    map.put('X', 10);
    map.put('L', 50);
    map.put('C', 100);
    map.put('D', 500);
    map.put('M', 1000);

    // Valor decimal acumulado
    int valorDecimal = 0;
    // Índice actual en la cadena
    int i = 0;

    // Iterar por los caracteres del número romano
    while (i < romanNumeral.length()) {

      // Obtener el caracter actual
      char simboloActual = romanNumeral.charAt(i);
      // Obtener el valor decimal del caracter actual
      int valorActual = map.get(simboloActual);

      // Si el siguiente caracter existe y tiene un valor mayor
      if (i + 1 < romanNumeral.length() && valorActual < map.get(romanNumeral.charAt(i + 1))) {  // Es un caso de resta (IV, IX, XL, XC, CD, CM)
        // Restar el valor actual del valor decimal
        valorDecimal -= valorActual;
        // Incrementar el índice en 2 para omitir el siguiente caracter
        i += 2;

      } else {  // No es un caso de resta
        // Sumar el valor actual al valor decimal
        valorDecimal += valorActual;
        // Incrementar el índice en 1 para avanzar al siguiente caracter
        i++;
      }
    }

    return valorDecimal;
  }
}
```
#### ENLACE AL KATA
[RomanNumeralsHelper](https://www.codewars.com/kata/51b66044bce5799a7f000003 "RomanNumeralsHelper")
