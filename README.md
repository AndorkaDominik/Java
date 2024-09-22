# Java

## Feladat
> Írjon Java alkalmazást, ami a szabványos bemenetről beolvasott egész számról eldönti, hogy a szám tökéletes szám-e! A tökéletes számok olyan számok, amelyeknek a valódi osztóinak összege azonos a számmal. Pl. 6 osztói 1,2,3 és 6 = 1+2+3; 28 osztói 1,2,4,7,14 és 28=1+2+4+7+14; 10 osztói 1,2,5 és 10 != 1+2+5. Tehát 6 és 28 tökéletesek, 10 nem az.

```java 
import java.util.Scanner;

public class PerfectNumberChecker {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Bemenet beolvasása
        System.out.print("Adjon meg egy egész számot: ");
        int number = scanner.nextInt();

        // Tökéletes szám vizsgálata
        if (isPerfectNumber(number)) {
            System.out.println(number + " tökéletes szám.");
        } else {
            System.out.println(number + " nem tökéletes szám.");
        }

        scanner.close();
    }

    // Függvény a tökéletes szám ellenőrzéséhez
    public static boolean isPerfectNumber(int number) {
        if (number < 1) {
            return false; // Nincs értelme negatív vagy nulla számra vizsgálni
        }

        int sum = 0;

        // Osztók keresése és összegzése
        for (int i = 1; i <= number / 2; i++) {
            if (number % i == 0) {
                sum += i;
            }
        }

        // Ha az osztók összege megegyezik a számmal, akkor tökéletes
        return sum == number;
    }
}

```
<br /><br />
> Írjon Java alkalmazást, ami a szabványos bemenetről beolvas egy egész számot (n), és kiírja 1 és n között az összes tökéletes számot!

```java 
import java.util.Scanner;

public class PerfectNumbersInRange {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Bemenet beolvasása
        System.out.print("Adjon meg egy egész számot: ");
        int n = scanner.nextInt();

        // Tökéletes számok keresése és kiírása 1 és n között
        System.out.println("Tökéletes számok 1 és " + n + " között:");
        for (int i = 1; i <= n; i++) {
            if (isPerfectNumber(i)) {
                System.out.println(i);
            }
        }

        scanner.close();
    }

    // Függvény a tökéletes szám ellenőrzéséhez
    public static boolean isPerfectNumber(int number) {
        if (number < 1) {
            return false;
        }

        int sum = 0;

        // Osztók keresése és összegzése
        for (int i = 1; i <= number / 2; i++) {
            if (number % i == 0) {
                sum += i;
            }
        }

        return sum == number;
    }
}

```
<br /><br />
> Írjon Java alkalmazást, ami a szabványos bemenetről beolvasott két db. egész számról eldönti, hogy a számok barátságos számok-e! Két szám akkor barátságos, ha a valódi osztóik összege a másik számmal egyenlő. Pl: 220 és 284 barátságosak, mert 220 osztói 1, 2, 4, 5, 10, 11, 20, 22, 44, 55 és 110 (összeg 284); 284 osztói 1, 2, 4, 71 és 142 (összeg 220).

```java 
import java.util.Scanner;

public class FriendlyNumbers {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Bemenet beolvasása
        System.out.print("Adja meg az első számot: ");
        int num1 = scanner.nextInt();
        System.out.print("Adja meg a második számot: ");
        int num2 = scanner.nextInt();

        // Barátságos számok vizsgálata
        if (areFriendlyNumbers(num1, num2)) {
            System.out.println(num1 + " és " + num2 + " barátságos számok.");
        } else {
            System.out.println(num1 + " és " + num2 + " nem barátságos számok.");
        }

        scanner.close();
    }

    // Függvény a barátságos számok ellenőrzéséhez
    public static boolean areFriendlyNumbers(int num1, int num2) {
        // Osztók összegeinek kiszámítása
        int sumOfDivisors1 = sumOfDivisors(num1);
        int sumOfDivisors2 = sumOfDivisors(num2);

        // Ha az egyik szám osztóinak összege a másik szám, akkor barátságosak
        return sumOfDivisors1 == num2 && sumOfDivisors2 == num1;
    }

    // Függvény egy szám valódi osztóinak összegzéséhez
    public static int sumOfDivisors(int number) {
        int sum = 0;

        // Valódi osztók keresése és összegzése
        for (int i = 1; i <= number / 2; i++) {
            if (number % i == 0) {
                sum += i;
            }
        }

        return sum;
    }
}
```
<br /><br />
>  Írjon Java alkalmazást, ami a szabványos bemenetről beolvas egy egész számot (n), és kiírja 1 és n között az összes barátságos számpárt!

```java
 import java.util.Scanner;

public class FriendlyNumbersInRange {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Bemenet beolvasása
        System.out.print("Adjon meg egy egész számot: ");
        int n = scanner.nextInt();

        System.out.println("Barátságos számpárok 1 és " + n + " között:");
        for (int i = 1; i <= n; i++) {
            for (int j = i + 1; j <= n; j++) {  // Az i < j feltétel miatt csak egyszer vizsgálunk egy párt
                if (areFriendlyNumbers(i, j)) {
                    System.out.println(i + " és " + j + " barátságos számpár.");
                }
            }
        }

        scanner.close();
    }

    // Függvény a barátságos számok ellenőrzéséhez
    public static boolean areFriendlyNumbers(int num1, int num2) {
        // Osztók összegeinek kiszámítása
        int sumOfDivisors1 = sumOfDivisors(num1);
        int sumOfDivisors2 = sumOfDivisors(num2);

        // Ha az egyik szám osztóinak összege a másik szám, akkor barátságosak
        return sumOfDivisors1 == num2 && sumOfDivisors2 == num1;
    }

    // Függvény egy szám valódi osztóinak összegzéséhez
    public static int sumOfDivisors(int number) {
        int sum = 0;

        // Valódi osztók keresése és összegzése
        for (int i = 1; i <= number / 2; i++) {
            if (number % i == 0) {
                sum += i;
            }
        }

        return sum;
    }
}

```
<br /><br />
> Írjon Java alkalmazást, amely a szabványos bementről olvas egy stringet és egy egész számot (n), és kiírja a stringben ábrázolt szám decimális értékét, ha a számrendszer alapja n. Pl: "123" és 8 esetén a kimenet 83; "1110" és 2 esetén a kimenet 14; "f3" és 16 esetén a kimenet 243.

```java
import java.util.Scanner;

public class BaseToDecimalConverter {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Bemenet beolvasása
        System.out.print("Adja meg a számot (string formátumban): ");
        String number = scanner.nextLine();
        System.out.print("Adja meg a számrendszer alapját (egész szám): ");
        int base = scanner.nextInt();

        // A string átalakítása decimális értékké
        try {
            int decimalValue = Integer.parseInt(number, base);
            System.out.println("A " + number + " decimális értéke a " + base + "-es számrendszerben: " + decimalValue);
        } catch (NumberFormatException e) {
            System.out.println("Hiba: A megadott szám nem érvényes a " + base + "-es számrendszerben.");
        }

        scanner.close();
    }
}

```
<br /><br />
> Írjon Java alkalmazást, amely sorokat olvas a szabványos bemenetről amíg üres sort nem kap, és kiírja a sorokat a szóközök nélkül.

```java
import java.util.Scanner;

public class RemoveSpaces {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.println("Adjon meg sorokat (nyomjon Entert üres sorhoz a befejezéshez):");

        while (true) {
            // Bemeneti sor beolvasása
            String line = scanner.nextLine();

            // Üres sor esetén kilép a ciklusból
            if (line.isEmpty()) {
                break;
            }

            // Szóközök eltávolítása a sorból
            String lineWithoutSpaces = line.replaceAll(" ", "");

            // Sor kiírása szóközök nélkül
            System.out.println(lineWithoutSpaces);
        }

        scanner.close();
    }
}

```
<br /><br />
> Írjon Java alkalmazást, amely a szabványos bemenetről beolvas két egész számot (x és n), és kiírja x értékét az n alapú számrendszerben. Tipp: Javaban érvényes a char+String és a String+char művelet, ami Stringet ad vissza. 

```java
import java.util.Scanner;

public class DecimalToBaseConverter {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Bemenet beolvasása
        System.out.print("Adja meg a decimális számot (x): ");
        int x = scanner.nextInt();
        System.out.print("Adja meg a számrendszer alapját (n): ");
        int base = scanner.nextInt();

        // Szám átalakítása a megadott számrendszerbe
        String result = convertToBase(x, base);
        System.out.println("A " + x + " értéke a " + base + "-es számrendszerben: " + result);

        scanner.close();
    }

    // Függvény a szám átalakítására a megadott számrendszerbe
    public static String convertToBase(int number, int base) {
        if (base < 2 || base > 36) {
            throw new IllegalArgumentException("A számrendszer alapja 2 és 36 között kell legyen.");
        }

        // Speciális eset: 0 decimális érték mindig "0" bármilyen számrendszerben
        if (number == 0) {
            return "0";
        }

        String result = "";
        int absNumber = Math.abs(number);

        // Szám átalakítása az n alapú számrendszerbe
        while (absNumber > 0) {
            int remainder = absNumber % base;

            // Maradékot karakterré alakítjuk (0-9, A-Z)
            char digit = (char) (remainder < 10 ? '0' + remainder : 'A' + (remainder - 10));
            result = digit + result; // Új számjegy hozzáfűzése a stringhez

            absNumber /= base;
        }

        // Ha a szám negatív volt, előre rakjuk a mínusz jelet
        if (number < 0) {
            result = "-" + result;
        }

        return result;
    }
}

```

> üres

```java

```




<br /><br />

# 2. labor
<br /><br />

> Írjon programot, amely az alábbi fájlt (neptun.txt) bementként megkapva kiírja a neptunkódokat (a zárójelben levő 6 karakteres stringeket). <br />
> <br />
> ----8<-----8<-----<br />
> Gipsz Jakab (A1B2C3)<br />
> Szőke Barna (B4RN41)<br />
> Karácsonyi Ajándék Sugárka (123456)<br />
> Sándor József Benedek (QWERTZ)<br />
> ----8<-----8<-----<br />

```java 
import java.io.*;
import java.util.regex.*;

public class NeptunCodeExtractor {
    public static void main(String[] args) {
        String fileName = "neptun.txt";

        try (BufferedReader br = new BufferedReader(new FileReader(fileName))) {
            String line;
            // A regex a zárójelben levő 6 karakteres stringek megtalálásához
            Pattern pattern = Pattern.compile("\\((\\w{6})\\)");

            while ((line = br.readLine()) != null) {
                Matcher matcher = pattern.matcher(line);
                if (matcher.find()) {
                    System.out.println(matcher.group(1)); // A megtalált Neptun kód kiírása
                }
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}

```
