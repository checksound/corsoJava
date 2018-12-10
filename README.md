# CORSO INFORMATICA 5° MAINF

## MATERIALE

Specifiche Java https://docs.oracle.com/javase/specs/index.html

Java doc: https://docs.oracle.com/javase/7/docs/api/index.html?overview-summary.html

Libro: **Java in a Nutshell** - 6th edition

## Tipi primitivi in JAVA

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

La dimensione del tipo non cambia a seconda dell'architettura della macchina come avvine nella maggiorparte dei linguaggi, garantendo in questo modo maggiore partabilità del codice.

Importante sapere che per ogni tipo primitivo esiste il corrispettivo tipo wrapper, di tipo reference.

|Type |Wrapper type|
|-----|--------|
| boolean |Boolean|
| char | Character |
| byte | Byte |
| short | Short |
| int | Integer |
| long | Long |
| float | Float |
| double | Double |

Esempio utilizzo tipo prinitivo e wrapper:

```java
double b1 = 123.65;

Double b2 = new Double(123.65); //wrapper class
```
I tipi wrapper sono classi che incapulano i tipi primitivi: per instanziare la classe si utilizza la **new** che alloca la memoria per l'oggetto.

![primitive_vs_wrapper_types](./primitive_vs_wrapper_types.png)

Utilizzzati all'interno di un metodo, i tipi primitivi vengono allocati nell'area di memoria dello stack e la variabile contiene il valore direttamente, i tipi corrispondenti di tipo reference, instanziati con l'operazione di **new**, sono allocati invece, nell'area di memoria dello heap (più lenta come operazione di allocazione).

La scelta di mantenere tipi primitivi, utilizzati nelle operazioni matemetiche, all'interno del linguaggio Java, è stata giustificata proprio per questioni di performance.

I tipi wrapper servono per inserire i dati nelle java collection: tipi di dati astratti come *Liste*, *Stack*, *Map*, *Set* che servono per lavorare su collezioni di oggetti (Vedremo in seguito le collection in java).

### Tipo booleano (boolean type)

```java
boolean isMonday = true;
boolean isChristmas = false;
```

The boolean type represents truth values. This type has only two possible values,
representing the two Boolean states: on or off, yes or no, true or false. Java reserves the words `true` and `false` to represent these two Boolean values.

### Tipo carattere (Char type)

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

### Letterali di Stringhe

Non è uno dei tipi primitivi, infatti in java c'è la classe [String](https://docs.oracle.com/javase/7/docs/api/java/lang/String.html), ma siccome le stringhe somo molto utilizzate all'interno dei programmi, Java include una sintassi speciale per includere valori stringa nel codice sorgente.

```java
"Hello, world"
"'This' is a string!"
```
### Tipo intero

`byte`, `short`, `integer` e `long`

E' possiblile esprimere il valore anche in notazione ottale ( `0` - zero davanti) ed esadecimale `0x` o `0X`.

```java
0xff // Decimal 255, expressed in hexadecimal
0377 // The same number, expressed in octal (base 8)
0b0010_1111 // Decimal 47, expressed in binary
```

Per il tipo `long` il valore si esprime mettendo il carattere `l` o `L` alla fine del numero.

```java
1234 // An int value
1234L // A long value
0xffL // Another long value
```

*N.B*: Dividere un intero per `0` o eseguire l'operazione modulo `0` genera l'errore a runtime [ArithmeticException](https://docs.oracle.com/javase/7/docs/api/java/lang/ArithmeticException.html).

Ogni tipo intero ha la corrispondente classe wrapper di tipo `Byte`, `Short`, `Integer` e `Long`.

Ognuna di queste classi definisce le costanti `MIN_VALUE` e `MAX_VALUE` che descrivono il range (intervallo) del tipo. 

Inoltre queste classi wrapper includono dei metodi statici come [Byte.parseByte](https://docs.oracle.com/javase/7/docs/api/java/lang/Byte.html#parseByte(java.lang.String)) o [Integer.parseInt](https://docs.oracle.com/javase/7/docs/api/java/lang/Integer.html#parseInt(java.lang.String)) per convertire da stringa a tipo primitivo. 

**ESERCIZIO**: 
Utilizzo di alcune classi standard della JDK per convertire stringhe di input nei numeri corrispondenti come interi.

|INPUT STRING | TIPO INPUT| RETURN VALUE INTERO |
|-------------|-------|-------------|
|"495"        | decimale | 495          |
|"0X1EF"      | esadecimale | 495          |
|"0757"       | ottale | 495          |

Verificare cosa succede se do in input la stringa "pippo" che non corrisponse a nessun
numero.

### Tipi decimali (Floating-point types)

I valori dei numeri decimali sono di default di tipo `double`, per esprimeri come tipo  `float` aggiungere la lettera `f`o `F` a fine numero.

```java
float f = 6.76f;
double d = 6.76;
```
I numeri decimali possono anche essere espressi in notazione scintifica, con esponente, in cui il numero è seguito dalla lettera e o E (per esponente) e un altro numero. Quest'altro numero rappresenta l'esponente base 10 per il quale il primo numero è moltiplicato:

```java
1.2345E02 // 1.2345 * 10^2 or 123.45
1e-6 // 1 * 10^-6 or 0.000001
6.02e23 // Avogadro's Number: 6.02 * 10^23
```

Float e double in notazione scientifica:

```java
double d = 6.02E23;
float f = 6.02e23f;
```

## Reference Types

E' un tipo di dato che è basato su una classe, istanza di una classe, che sia tra quelle fornite dal JDK o che sia stata definita da un programmatore.

Altri tipi di reference type, oltre alle classi, sono gli array e i tipi enumerativi.

Definiamo una classe con alcuni semplici attributi.

```java
class DataOnly {
	int i;
	double d;
	boolean b;
}
```
questa classe non fa niente se non contenere dei dati. Se creiamo un oggeto da questa classe:

```java
DataOnly data = new DataOnly();
```

tramite la refernce data possiamo modificare l'oggetto:

```java
objectReference.member
```
Per esempio:
```java
data.i = 47;
data.d = 1.1;
data.b = false;
```
### Assegnamento dei tipi reference 

Esempio:

```java
int i1 = 5;
int i2 = 7;
Persona p1 = new Persona("Mario", "Rossi");
Persona p2 = new Persona("Mario", "Verdi");
```
![tipi-primitivi-oggetti](./tipi-primitivi-oggetti.png)

Fin qui sembra tutto semplice, andiamo avanti facendo un po’ di assegnazioni:

```java
i2 = i1;
p2 = p1;
```
![condivisione-di-memoria](./condivisione-di-memoria.png)

Adesso p1 e p2 puntano allo stesso oggetto: abbiamo una condivisione di memoria che può risultare pericolosa se non gestita adeguatamente. Infatti richiamando un metodo setter su uno dei due oggetti (per esempio `p1.setNome("Fabio")`) si modificherà l’oggetto condiviso dai due puntatori. Non è sicuramente un dramma (e a volte può essere una cosa utile da sfruttare) ma è comunque una cosa da tenere presente.

### Valori di default dei tipi primitivi

Quando un tipo primitivo è membro di una classe, se non inizializzato prende i seguenti valori:

| Primitive type | Default |
|----------------|---------|
| boolean        | false   |
| char           | ‘\u0000’ (null) |
| byte | (byte)0 |
| short | (short)0 |
| int   | 0 |
| long  |0L |
| float | 0.0f |
| double | 0.0d |

Questo non è garantito invece per le *variabili locali* che prendono un valore arbitrario (come in C e C++), è compito del programmatore inizializzarle prima dell'utilizzo altrimenti il compilatore dà errore di compilazione.

Es:

```java
int v;

// v non è stato ancora inizializzato --> errore di compilazione
myObject.print(v);

```

### Metodi, argomenti e valori di ritorno.

I metodi in java determinano il messaggio che un oggetto può ricevere.

```java
ReturnType methodName( /* Argument list */ ) {
/* Method body */
}
```
Esempio di chiamata di un metodo:
```java
objectName.methodName(arg1, arg2, arg3);
```
Esempio con parametro di ritorno:
```java
int x = a.f();
```
Il tipo del ritorno deve essere compatibile con il tipo di **x**. La chiamata di un metodo è spesso detto *inviare un messaggio all'oggetto*. Nell'esempio precedente, il messaggio è **f()** e l'oggetto è **a**. La programmazione ad oggetti è spesso sintetizzata con il concetto di 'spedire un messaggio a un oggetto'. 


## Costruzione del primo programma

```java

// HelloDate.java
import java.util.*;
public class HelloDate {
		public static void main(String[] args) {
				System.out.println("Hello, it’s: ");
				System.out.println(new Date());
		}
}
```

### Ugualianza per riferimento vs. Ugualianza per valore

Se utilizzo l'operatore `==` verifico l'**ugualianza per riferimento**.

La classe `Object` classe padre di tutte le classi ho il metodo `boolean equals(Object obj)` che può essere utilizzato, se reimplementato nelle nostre classi, per eseguire l'**ugualianza per valore**. Di default anche il metodo `equals` di `Object` esegue ugualianza per riferimento.

Vediamo esempio:

```java
package it.isisgallarate.test;

public class TestEqualsOnObjects {
	
	public static void main(String[] args) {
		
		Object o1 = new Object();
		Object o2 = new Object();
		
		if (o1 == o2) {
			System.out.println("SONO UGUALI PER REFERENCE - o1, o2");
		} else {
			System.out.println("SONO DIVERSI PER REFERENCE - o1, o2"); // PRINT THIS
		}
		
		if (o1.equals(o2)) {
			System.out.println("EQUALS TRUE - o1, o2");
		} else {
			System.out.println("EQUALS FALSE - o1, o2"); // PRINT THIS
		}
		
		// Oggetto o1 assegnato a o3
		
		Object o3 = o1;
		
		if (o1 == o3) {
			System.out.println("SONO UGUALI PER REFERENCE - o1, o3"); // PRINT THIS
		} else {
			System.out.println("SONO DIVERSI PER REFERENCE - o1, o3");
		}
		
		if (o1.equals(o3)) {
			System.out.println("EQUALS TRUE - o1, o3"); // PRINT THIS
		} else {
			System.out.println("EQUALS FALSE - o1, o3"); 
		}
				
	}
}

```

Qualsiasi classe da noi creata, in quanto implicitamente sottoclasse di `Object` erediterebbe lo stasso comportamento del metodo `equals`. E' quindi necessario per ottenere un confronto tra valori, reimplementere `equals` per restituire `true`, quando i valori sono uguali.

Esempio:

```java
package it.isisgallarate.equals;

public class Vino {
	
	private String nome;
	private int anno;
	private int prezzo;
		
	public Vino(String nome, int anno, int prezzo) {
		this.nome = nome;
		this.anno = anno;
		this.prezzo = prezzo;
	}
	
	public String getNome() {
		return nome;
	}

	public void setNome(String nome) {
		this.nome = nome;
	}

	public int getAnno() {
		return anno;
	}

	public void setAnno(int anno) {
		this.anno = anno;
	}
	
	public int getPrezzo() {
		return prezzo;
	}


	public void setPrezzo(int prezzo) {
		this.prezzo = prezzo;
	}


	@Override
	public int hashCode() {
		final int prime = 31;
		int result = 1;
		result = prime * result + anno;
		result = prime * result + ((nome == null) ? 0 : nome.hashCode());
		return result;
	}
	
	@Override
	public boolean equals(Object obj) {
		if (this == obj)
			return true;
		if (obj == null)
			return false;
		if (getClass() != obj.getClass())
			return false;
		Vino other = (Vino) obj;
		if (anno != other.anno)
			return false;
		if (nome == null) {
			if (other.nome != null)
				return false;
		} else if (!nome.equals(other.nome))
			return false;
		return true;
	}

	@Override
	public String toString() {
		return "Vino [nome=" + nome + ", prezzo=" + prezzo + "]";
	}
		
}

```

Vedi anche: https://codingjam.it/tutorial-java-il-metodo-equals-e-loperatore/ per ulteriore spiegazione.









