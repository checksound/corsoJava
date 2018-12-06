# CORSO INFORMATICA 5° MAINF

## MATERIALE

Specifiche Java https://docs.oracle.com/javase/specs/index.html

Java doc: https://docs.oracle.com/javase/7/docs/api/index.html?overview-summary.html

Libro: **Java in a Nutshell** - 6th edition

### Tipi primitivi in JAVA

|Type |Contains| Default| Size| Range|
|-----|--------|--------|-----|------|
| boolean |true or false| false| 1 bit | NA |
| char | Unicode character | \u0000 | 16 bits | \u0000 to \uFFFF |
| byte | Signed integer | 0 | 8 bits | -128 to 127 |
| short | Signed integer | 0 | 16 bits | -32768 to 32767 |
| int | Signed integer | 0 | 32 bits | -2147483648 to 2147483647 |
| long | Signed integer | 0 | 64 bits | -9223372036854775808 to 9223372036854775807 |
| float | IEEE 754 floating point | 0.0 | 32 bits | 1.4E-45 to 3.4028235E+380 |
| double | IEEE 754 floating point | 0.0 | 64 bits | 4.9E-324 to 1.7976931348623157E+308 |

#### Tipo booleano (boolean type)

```java
boolean isMonday = true;
boolean isChristmas = false;
```

The boolean type represents truth values. This type has only two possible values,
representing the two Boolean states: on or off, yes or no, true or false. Java reserves the words `true` and `false` to represent these two Boolean values.

#### Tipo carattere (Char type)

```java
char c = 'A';
// nonprinting ASCII characters or escape certain punctuation 
char tab = '\t', nul = '\000', aleph = '\u05D0', slash = '\\';
```
| Escape sequence | Character value |
|-----------------|-----------------|
| \b | Backspace |
| \t | Horizontal tab |
| \n | Newline |
| \f | Form feed |
|\r | Carriage return |
| \" | Double quote |
| \' | Single quote |
| \\\ | Backslash |
|\ xxx | The Latin-1 character with the encoding xxx, where xxx is an octal (base 8) number between 000 and 377. The forms \ x and \ xx are also legal, as in \0, but are not recommended because they can cause difficulties in string constants where the escape sequence is followed by a regular digit. This form is generally discouraged in favor of the \uXXXX form.|
| \u xxxx | The Unicode character with encoding xxxx, where xxxx is four hexadecimal digits. Unicode escapes can appear anywhere in a Java program, not only in character and string literals. |

#### Letterali di Stringhe

Non è uno dei tipi primitivi, infatti in java c'è la classe [String](https://docs.oracle.com/javase/7/docs/api/java/lang/String.html), ma siccome le stringhe somo molto utilizzate all'interno dei programmi, Java include una sintassi speciale per includere valori stringa nel codice sorgente.

```java
"Hello, world"
"'This' is a string!"
```
#### Tipo intero (Integer types)

Notazione ottale ( `0` - zero davanti) ed esadecimale `0x` o `0X`.

```java
0xff // Decimal 255, expressed in hexadecimal
0377 // The same number, expressed in octal (base 8)
0b0010_1111 // Decimal 47, expressed in binary
0xCAFEBABE // A magic number used to identify Java class files
```

[The magic world in java cafebabe](https://dzone.com/articles/the-magic-word-in-java-cafebabe)

Tipo `long`

```java
1234 // An int value
1234L // A long value
0xffL // Another long value
```

Dividere un intero per `0` o eseguire l'operazione modulo `0` genera l'errore a runtime [ArithmeticException](https://docs.oracle.com/javase/7/docs/api/java/lang/ArithmeticException.html).

Ogni tipo intero ha la corrispondente classe wrapper di tipo `Byte`, `Short`, `Integer` e `Long`.

Ognuna di queste classi definisce le costanti `MIN_VALUE` e `MAX_VALUE` che descrivono il range (intervallo) del tipo. 

Inoltre queste classi wrapper includono dei metodi statici come [Byte.parseByte](https://docs.oracle.com/javase/7/docs/api/java/lang/Byte.html#parseByte(java.lang.String)) o [Integer.parseInt](https://docs.oracle.com/javase/7/docs/api/java/lang/Integer.html#parseInt(java.lang.String)) per convertire da stringa a tipo primitivo. 

Esempio:

```java
package it.isisgallarate.tipi_interi;

public class Start {

	public static void main(String[] args) {
		
		byte b1 = 127, b2 = 1; // Largest byte is 127
		byte sum = (byte)(b1 + b2); // Sum wraps to -128, the smallest byte
		
		int sumInt = b1 + b2; // automaticamente promizione a int 
		
		System.out.println("Somma tipo byte:" + sum);
		System.out.println("Somma di tipo integer: " + sumInt);
		
		
		int f = 5/0; // throws java.lang.ArithmeticException
		
	}

}
```

[Perché la somma di tipi byte diventa tipo intero](https://stackoverflow.com/questions/21895078/why-is-the-sum-of-bytes-integer) - regole di promozione dei tipi.

### Tipi decimali (Floating-point types)


### Reference Types

E' un tipo di dato che è basato su una classe, istanza di una classe, che sia tra quelle fornite dal JDK o che sia stata definita da un programmatore.

Altri tipi di reference type oltre alle classi sono gli array e i tipi enumerativi.





