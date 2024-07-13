## Podstawowe wyrażenia regularne

## Zadanie 1: Znajdź wszystkie wystąpienia cyfry 5 w tekście.

grep -E '5' moja_lista_zadan.txt 

## Zadanie 2: Znajdź wszystkie wystąpienia liter a, b, lub c w tekście.

grep -E '[abc]' moja_lista_zadan.txt 

## Zadanie 3: Znajdź wszystkie słowa, które zaczynają się od litery b.

\b: Znacznik początku słowa.
b: Litera b.
\w*: Zero lub więcej znaków alfanumerycznych.

grep -E '\bb\w*' sample.txt

Znajdź wszystkie słowa zaczynające się od litery b i wyświetl je:
grep -oE '\bb\w*' sample.txt

## Zadanie 4: Znajdź wszystkie liczby trzycyfrowe w tekście.

grep -oE '\b[0-9]{3}\b' sample.txt

## Wyjaśnienie
grep -oE '\b[0-9]{3}\b' sample.txt: Flaga -o sprawia, że grep wyświetla tylko dopasowania, a nie całe linie. Flaga -E używa rozszerzonych wyrażeń regularnych.

\b: Granica słowa.
[0-9]{3}: Dokładnie trzy cyfry.

Znajdź wszystkie liczby trzycyfrowe przed znakiem : i wyświetl je:
grep -oE '\b[0-9]{3}:' sample.txt

Znajdź wszystkie liczby trzycyfrowe zaczynające się od 2 przed znakiem : i wyświetl je:
grep -oE '\b2[0-9]{2}:' sample.txt

## Zadanie 5: Znajdź wszystkie adresy e-mail w tekście.

Załóżmy, że masz plik sample.txt z następującą zawartością:

Kontakt: jan.kowalski@example.com
Proszę o przesłanie wiadomości na adres: anna.nowak@firma.pl
Możesz również skontaktować się z nami pod adresem: info@example.org
Nieprawidłowe adresy: john@com, @example.com, email@

grep -oE '[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}' sample.txt
Wyjaśnienie
grep -oE '[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}' sample.txt: Flaga -o sprawia, że grep wyświetla tylko dopasowania, a nie całe linie. Flaga -E używa rozszerzonych wyrażeń regularnych.
[a-zA-Z0-9._%+-]+: Część lokalna adresu e-mail (może zawierać litery, cyfry oraz znaki ., _, %, +, -).
@: Dosłowny znak @.
[a-zA-Z0-9.-]+: Część domeny (może zawierać litery, cyfry, kropki i myślniki).
\.[a-zA-Z]{2,}: Końcówka domeny (kropka i co najmniej dwa znaki).


## Średnio zaawansowane wyrażenia regularne

## Zadanie 6: Znajdź wszystkie słowa, które zaczynają się na a i kończą się na z.

grep -oE '\ba\w*z\b' sample.txt
Wyjaśnienie
grep -oE '\ba\w*z\b' sample.txt: Flaga -o sprawia, że grep wyświetla tylko dopasowania, a nie całe linie. Flaga -E używa rozszerzonych wyrażeń regularnych.
\b: Granica słowa.
a: Litera a (początek słowa).
\w*: Zero lub więcej znaków alfanumerycznych (dowolna liczba liter lub cyfr pomiędzy a i z).
z: Litera z (koniec słowa).
\b: Granica słowa.


## Zadanie 7: Znajdź wszystkie liczby dziesiętne w formacie 123.45.

Cena produktu wynosi 123.45 PLN.
Inny produkt kosztuje 67.89 PLN.
Podatek wynosi 0.99 PLN.
Niepoprawna liczba: 123.456, 123,45, 12345
Prawidłowy format to np. 10.01 lub 999.99.

grep -oE '[0-9]+\.[0-9]{2}' sample.txt
Wyjaśnienie
grep -oE '[0-9]+\.[0-9]{2}' sample.txt: Flaga -o sprawia, że grep wyświetla tylko dopasowania, a nie całe linie. Flaga -E używa rozszerzonych wyrażeń regularnych.
[0-9]+: Jedna lub więcej cyfr przed kropką.
\.: Dosłowna kropka.
[0-9]{2}: Dokładnie dwie cyfry po kropce.


## Zadanie 8: Znajdź wszystkie numery telefonów w formacie 123-456-7890.


Skontaktuj się z nami pod numerem 123-456-7890.
Alternatywny numer to 987-654-3210.
Niepoprawny format: 1234567890, 123-45-67890, 12-3456-7890.
Kolejny poprawny numer: 555-555-5555.

grep -oE '[0-9]{3}-[0-9]{3}-[0-9]{4}' sample.txt

Wyjaśnienie
grep -oE '[0-9]{3}-[0-9]{3}-[0-9]{4}' sample.txt: Flaga -o sprawia, że grep wyświetla tylko dopasowania, a nie całe linie. Flaga -E używa rozszerzonych wyrażeń regularnych.

[0-9]{3}: Dokładnie trzy cyfry.
-: Dosłowny myślnik.
[0-9]{3}: Dokładnie trzy cyfry.
-: Dosłowny myślnik.
[0-9]{4}: Dokładnie cztery cyfry.


## Zadanie 9: Znajdź wszystkie słowa, które zawierają co najmniej jedną cyfrę.

grep -oE '\b\w*[0-9]\w*\b' sample.txt

Wyjaśnienie
grep -oE '\b\w*[0-9]\w*\b' sample.txt: Flaga -o sprawia, że grep wyświetla tylko dopasowania, a nie całe linie. Flaga -E używa rozszerzonych wyrażeń regularnych.
\b: Granica słowa.
\w*: Zero lub więcej znaków alfanumerycznych przed cyfrą.
[0-9]: Dowolna cyfra.
\w*: Zero lub więcej znaków alfanumerycznych po cyfrze.
\b: Granica słowa.

## Zadanie 10: Znajdź wszystkie daty w formacie dd/mm/yyyy.

Wydarzenie odbędzie się 01/12/2023.
Kolejne spotkanie jest zaplanowane na 15/08/2021.
Niepoprawny format daty: 1/1/2020, 32/13/2020, 12-12-2020.
Poprawne daty: 05/11/2020, 30/09/1999.

grep -oE '\b[0-3][0-9]/[0-1][0-9]/[0-9]{4}\b' sample.txt

Wyjaśnienie
grep -oE '\b[0-3][0-9]/[0-1][0-9]/[0-9]{4}\b' sample.txt: Flaga -o sprawia, że grep wyświetla tylko dopasowania, a nie całe linie. Flaga -E używa rozszerzonych wyrażeń regularnych.
\b: Granica słowa.
[0-3][0-9]: Dzień (00-39, choć poprawne dni to 01-31).
/: Dosłowny znak ukośnika.
[0-1][0-9]: Miesiąc (00-19, choć poprawne miesiące to 01-12).
/: Dosłowny znak ukośnika.
[0-9]{4}: Rok składający się z czterech cyfr.
\b: Granica słowa.


Oczywiście! Poniżej znajduje się pełny przykład użycia `grep` z wyrażeniem regularnym, aby znaleźć wszystkie daty w formacie `dd/mm/yyyy`, wraz z oznaczeniem wyników znacznikami Markdown.

### Przykład użycia `grep` z wyrażeniem regularnym

Załóżmy, że masz plik `sample.txt` z następującą zawartością:

```
Wydarzenie odbędzie się 01/12/2023.
Kolejne spotkanie jest zaplanowane na 15/08/2021.
Niepoprawny format daty: 1/1/2020, 32/13/2020, 12-12-2020.
Poprawne daty: 05/11/2020, 30/09/1999.
```

### Komenda w terminalu

1. **Użyj `grep` z wyrażeniem regularnym, aby znaleźć wszystkie daty w formacie `dd/mm/yyyy`**:

```sh
grep -oE '\b[0-3][0-9]/[0-1][0-9]/[0-9]{4}\b' sample.txt
```

```markdown
# Znajdowanie dat w formacie `dd/mm/yyyy` za pomocą `grep` i wyrażeń regularnych

Załóżmy, że masz plik `sample.txt` z następującą zawartością:

```
Wydarzenie odbędzie się 01/12/2023.
Kolejne spotkanie jest zaplanowane na 15/08/2021.
Niepoprawny format daty: 1/1/2020, 32/13/2020, 12-12-2020.
Poprawne daty: 05/11/2020, 30/09/1999.
```

## Komenda w terminalu

1. **Użyj `grep` z wyrażeniem regularnym, aby znaleźć wszystkie daty w formacie `dd/mm/yyyy`**:

```sh
grep -oE '\b[0-3][0-9]/[0-1][0-9]/[0-9]{4}\b' sample.txt
```

## Wyjaśnienie

- `grep -oE '\b[0-3][0-9]/[0-1][0-9]/[0-9]{4}\b' sample.txt`: Flaga `-o` sprawia, że `grep` wyświetla tylko dopasowania, a nie całe linie. Flaga `-E` używa rozszerzonych wyrażeń regularnych.
- `\b`: Granica słowa.
- `[0-3][0-9]`: Dzień (00-39, choć poprawne dni to 01-31).
- `/`: Dosłowny znak ukośnika.
- `[0-1][0-9]`: Miesiąc (00-19, choć poprawne miesiące to 01-12).
- `/`: Dosłowny znak ukośnika.
- `[0-9]{4}`: Rok składający się z czterech cyfr.
- `\b`: Granica słowa.

## Pełny przykład:

1. **Utwórz plik `sample.txt` z podanym tekstem**:

```sh
echo -e "Wydarzenie odbędzie się 01/12/2023.\nKolejne spotkanie jest zaplanowane na 15/08/2021.\nNiepoprawny format daty: 1/1/2020, 32/13/2020, 12-12-2020.\nPoprawne daty: 05/11/2020, 30/09/1999." > sample.txt
```

2. **Znajdź wszystkie daty w formacie `dd/mm/yyyy` i wyświetl je**:

```sh
grep -oE '\b[0-3][0-9]/[0-1][0-9]/[0-9]{4}\b' sample.txt
```

## Wynik

Komenda wyświetli wszystkie daty w formacie `dd/mm/yyyy` z pliku `sample.txt`, czyli:

```
01/12/2023
15/08/2021
05/11/2020
30/09/1999
```

Te komendy pozwolą Ci znaleźć i wyświetlić wszystkie daty w formacie `dd/mm/yyyy` w podanym pliku tekstowym, używając `grep` i wyrażeń regularnych.
```


### Zaawansowane wyrażenia regularne

## Zadanie 11: Znajdź wszystkie słowa zaczynające się od wielkiej litery.

Oczywiście! Oto jak możesz znaleźć wszystkie słowa zaczynające się od wielkiej litery za pomocą `grep` i wyrażeń regularnych, wraz z oznaczeniem wyników znacznikami Markdown.

### Przykład użycia `grep` z wyrażeniem regularnym

Załóżmy, że masz plik `sample.txt` z następującą zawartością:

```
Ala ma kota.
Barbara lubi psy.
Cecylia hoduje papugi.
Dzieci bawią się w parku.
```

### Komenda w terminalu

1. **Użyj `grep` z wyrażeniem regularnym, aby znaleźć wszystkie słowa zaczynające się od wielkiej litery**:

```sh
grep -oE '\b[A-Z][a-z]*\b' sample.txt
```

```markdown
# Znajdowanie słów zaczynających się od wielkiej litery za pomocą `grep` i wyrażeń regularnych

Załóżmy, że masz plik `sample.txt` z następującą zawartością:

```
Ala ma kota.
Barbara lubi psy.
Cecylia hoduje papugi.
Dzieci bawią się w parku.
```

## Komenda w terminalu

1. **Użyj `grep` z wyrażeniem regularnym, aby znaleźć wszystkie słowa zaczynające się od wielkiej litery**:

```sh
grep -oE '\b[A-Z][a-z]*\b' sample.txt
```

## Wyjaśnienie

- `grep -oE '\b[A-Z][a-z]*\b' sample.txt`: Flaga `-o` sprawia, że `grep` wyświetla tylko dopasowania, a nie całe linie. Flaga `-E` używa rozszerzonych wyrażeń regularnych.
- `\b`: Granica słowa.
- `[A-Z]`: Wielka litera (od A do Z).
- `[a-z]*`: Zero lub więcej małych liter (od a do z).
- `\b`: Granica słowa.

## Pełny przykład:

1. **Utwórz plik `sample.txt` z podanym tekstem**:

```sh
echo -e "Ala ma kota.\nBarbara lubi psy.\nCecylia hoduje papugi.\nDzieci bawią się w parku." > sample.txt
```

2. **Znajdź wszystkie słowa zaczynające się od wielkiej litery i wyświetl je**:

```sh
grep -oE '\b[A-Z][a-z]*\b' sample.txt
```

## Wynik

Komenda wyświetli wszystkie słowa zaczynające się od wielkiej litery z pliku `sample.txt`, czyli:

```
Ala
Barbara
Cecylia
Dzieci
```

Te komendy pozwolą Ci znaleźć i wyświetlić wszystkie słowa w podanym pliku tekstowym, które zaczynają się od wielkiej litery, używając `grep` i wyrażeń regularnych.
```

Mam nadzieję, że to pomoże! Jeśli masz więcej pytań lub potrzebujesz dalszej pomocy, daj znać!


## Zadanie 12: Znajdź wszystkie kody pocztowe w formacie XX-XXX.

# Znajdowanie kodów pocztowych w formacie XX-XXX

Aby znaleźć wszystkie kody pocztowe w formacie `XX-XXX` w pliku tekstowym, użyj poniższego polecenia `grep` wraz z odpowiednim wyrażeniem regularnym:

```sh
grep -Eo '\<[0-9]{2}-[0-9]{3}\>' filename.txt
```

Możesz to zrobić używając poniższego polecenia w terminalu:

```sh
cat <<EOT > testfile.txt
Here are some postal codes:
00-001
12-345
98-765
Some invalid codes:
12345
12-3456
123-45
Mixed with text:
My address is 12-345, some random text here.
Another one is 34-567. Here is 23-456.
And some more codes like 78-910, 56-789, and 12-123.
End of the list.
EOT
```

## Zadanie 13: Znajdź wszystkie adresy IP w tekście.

### Przygotuj plik `testfile.txt`:

używając poniższego polecenia w terminalu:

```sh
cat <<EOT > testfile.txt
Here are some IP addresses:
192.168.0.1
255.255.255.255
8.8.8.8
10.11.12.14
127.0.0.1
Invalid IPs:
256.256.256.256
192.168.0.999
Just some text with no IP addresses.
Another valid IP is 10.0.0.1 and also 172.16.254.1.
EOT
```

# Znajdowanie adresów IP w tekście

Aby znaleźć wszystkie adresy IP w tekście w pliku, użyj poniższego polecenia `grep` wraz z odpowiednim wyrażeniem regularnym:

```sh
grep -Eo '\b((25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.){3}(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\b' filename.txt



Wyrażenie regularne:
\b - Granica słowa.
((25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.){3} - Trzy grupy liczb od 0 do 255, każda zakończona kropką.
25[0-5] - Liczby od 250 do 255.
2[0-4][0-9] - Liczby od 200 do 249.
[01]?[0-9][0-9]? - Liczby od 0 do 199.
(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?) - Ostatnia grupa liczb od 0 do 255.
\b - Granica słowa.
```

## Zadanie 14: Znajdź wszystkie tagi HTML w tekście.

```sh
grep -E '<([a-zA-Z]|/[a-zA-Z])+>' moja_lista_zadan.md 

Wyjaśnienie polecenia
-E: Używa rozszerzonych wyrażeń regularnych (Extended Regular Expressions).
-o: Wypisuje tylko pasujące fragmenty.
<: Znak otwarcia tagu.
[^>]+: Jeden lub więcej znaków, które nie są znakiem >.
>: Znak zamknięcia tagu.
filename.txt: Nazwa pliku, w którym szukamy.

cat <<EOT > testfile.txt
<html>
  <head>
    <title>Example Title</title>
  </head>
  <body>
    <h1>This is a heading</h1>
    <p>This is a paragraph.</p>
    <a href="http://example.com">This is a link</a>
    <img src="image.jpg" alt="Example Image">
  </body>
</html>
EOT
```

### Zadanie 15: Znajdź wszystkie zdania kończące się znakiem zapytania ?.

```sh

Wyrażenie regularne do znalezienia zdań kończących się znakiem zapytania:

regex
Skopiuj kod
[^.!?]*\?
[^.!?]* - Dowolny ciąg znaków, który nie zawiera kropek, wykrzykników ani znaków zapytania.
\? - Znak zapytania, który kończy zdanie.


### Zapisz zawartość do pliku `testfile.txt`:

Możesz zapisać powyższą zawartość do pliku `testfile.txt` używając poniższego polecenia w terminalu:

cat <<EOT > testfile.txt
Czy wiesz, gdzie jest najbliższa kawiarnia?
To jest zdanie oznajmujące.
Może chcesz pójść na spacer?
To nie jest pytanie!
Dlaczego jest tak gorąco?
Znowu jest piękna pogoda.
Czy mogę zadać pytanie?
EOT


grep -Eo '[^.!?]*\?' testfile.txt
```


# Bardziej złożone wyrażenia regularne

## Zadanie 16: Znajdź wszystkie słowa, które mają dokładnie pięć liter.

```sh

grep -Eo '\b[a-zA-Z]{5}\b' testfile.txt

Wyjaśnienie polecenia
-E: Używa rozszerzonych wyrażeń regularnych (Extended Regular Expressions).
-o: Wypisuje tylko pasujące fragmenty.
\b: Granica słowa.
[a-zA-Z]{5}: Dokładnie pięć liter (zarówno małych, jak i wielkich).
\b: Granica słowa.
filename.txt: Nazwa pliku, w którym szukamy.


Możesz to zrobić używając poniższego polecenia w terminalu:


cat <<EOT > testfile.txt
Hello world! This is a simple test file.
There are some five-letter words here.
Which words will match the regex?
Maybe these: apple, grape, mango, peach.
But not these: four, sixes, seven, longerword.
EOT

## Oczekiwany wynik

Hello
world
simple
There
apple
grape
mango
peach
sixes
seven
```


## Zadanie 17: Znajdź wszystkie pliki o rozszerzeniu .txt, .jpg lub .png.

### Znajdowanie plików o rozszerzeniu .txt, .jpg lub .png

Aby znaleźć wszystkie pliki o rozszerzeniu `.txt`, `.jpg` lub `.png` w tekście w pliku, użyj poniższego polecenia `grep` wraz z odpowiednim wyrażeniem regularnym:

```sh
grep -Eo '\b\w+\.(txt|jpg|png)\b' filename.txt


### Przykład pliku testowego `testfile.txt`:


### Zapisz zawartość do pliku `testfile.txt`:

Możesz zapisać powyższą zawartość do pliku `testfile.txt` używając poniższego polecenia w terminalu:

```sh
cat <<EOT > testfile.txt
Here are some filenames:
document.txt
image.jpg
picture.png
archive.zip
report.doc
photo.JPG
notes.Txt
file.jpeg
another_image.PNG
example.txt
EOT

grep -Eo '\b\w+\.(txt|jpg|png)\b' testfile.txt

Oczekiwany wynik:

document.txt
image.jpg
picture.png
example.txt

Wyjaśnienie polecenia
-E: Używa rozszerzonych wyrażeń regularnych (Extended Regular Expressions).
-o: Wypisuje tylko pasujące fragmenty.
\b: Granica słowa.
\w+: Dowolna liczba znaków alfanumerycznych i podkreśleń.
\.: Kropka.
(txt|jpg|png): Jeden z trzech rozszerzeń: txt, jpg lub png.
\b: Granica słowa.
filename.txt: Nazwa pliku, w którym szukamy.
```

## Zadanie 18: Znajdź wszystkie linie tekstu, które zaczynają się od cyfry.

```sh

Polecenie grep:

grep -E '^[0-9]' filename.txt


Wyjaśnienie polecenia
-E: Używa rozszerzonych wyrażeń regularnych (Extended Regular Expressions).
^: Początek linii.
[0-9]: Dowolna cyfra.
filename.txt: Nazwa pliku, w którym szukamy.

### Zapisz zawartość do pliku `testfile.txt`:

Możesz zapisać powyższą zawartość do pliku `testfile.txt` używając poniższego polecenia w terminalu:


cat <<EOT > testfile.txt
123 Main Street
This line does not start with a number.
42 is the answer to everything.
Another line without a number.
98 bottles of beer on the wall.
Just another text line.
7 days in a week.
EOT

Oczekiwany wynik:
css
Skopiuj kod
123 Main Street
42 is the answer to everything.
98 bottles of beer on the wall.
7 days in a week.
```

## Zadanie 19: Znajdź wszystkie zmienne w kodzie w stylu camelCase.

```sh

Zmienne w stylu camelCase zaczynają się małą literą, a kolejne słowa rozpoczynają się wielką literą.

Wyrażenie regularne do znalezienia zmiennych w stylu camelCase:

\b[a-z]+[A-Z][a-zA-Z]*\b
\b - Granica słowa.
[a-z]+ - Jedna lub więcej małych liter.
[A-Z] - Wielka litera.
[a-zA-Z]* - Zero lub więcej liter (zarówno małych, jak i wielkich).
\b - Granica słowa.

Polecenie grep:

grep -Eo '\b[a-z]+[A-Z][a-zA-Z]*\b' filename.txt

zawartość pliku testfile.txt:

cat <<EOT > testfile.txt
int main() {
    int userAge = 25;
    float accountBalance = 1024.50;
    std::string userName = "JohnDoe";
    bool isLoggedIn = true;
    double maxSpeed = 150.75;
    char firstInitial = 'J';

    int notCamelcase = 5;
    int another_variable = 10;
    int camelCaseVariable = 15;
    int anotherCamelCase = 20;
    return 0;
}
EOT
```


## Zadanie 20: Znajdź wszystkie fragmenty tekstu w cudzysłowach.

```sh

Zakładamy, że tekst w cudzysłowach jest otoczony podwójnymi cudzysłowami.


Wyrażenie regularne do znalezienia fragmentów tekstu w cudzysłowach:

"[^"]*"


Wyjaśnienie polecenia
-E: Używa rozszerzonych wyrażeń regularnych (Extended Regular Expressions).
-o: Wypisuje tylko pasujące fragmenty.
"[^"]*": Dopasowuje tekst otoczony podwójnymi cudzysłowami.
": Otwierający cudzysłów.
[^"]*: Dowolna liczba znaków, które nie są cudzysłowami.
": Zamykający cudzysłów.
filename.txt: Nazwa pliku, w którym szukamy.

Polecenie grep:

grep -Eo '"[^"]*"' filename.txt



### Zapisz zawartość do pliku `testfile.txt`:

Możesz zapisać powyższą zawartość do pliku `testfile.txt` używając poniższego polecenia w terminalu:

```sh
cat <<EOT > testfile.txt
She said, "Hello, how are you?"
He replied, "I'm fine, thank you."
"This is a test file," she noted.
He added, "Let's see if it works."
EOT

Oczekiwany wynik:

"Hello, how are you?"
"I'm fine, thank you."
"This is a test file,"
"Let's see if it works."
```

# Bardzo zaawansowane wyrażenia regularne

## Zadanie 21: Znajdź wszystkie linki URL w tekście.

```sh

Zakładamy, że linki URL zaczynają się od http:// lub https:// i mogą zawierać różne znaki, które są typowe dla adresów URL.

Wyrażenie regularne do znalezienia linków URL:

https?://[a-zA-Z0-9./?=_-]+

Polecenie grep:

grep -Eo 'https?://[a-zA-Z0-9./?=_-]+' filename.txt

Wyjaśnienie polecenia

-E: Używa rozszerzonych wyrażeń regularnych (Extended Regular Expressions).
-o: Wypisuje tylko pasujące fragmenty.
https?://: Dopasowuje http:// lub https://.
[a-zA-Z0-9./?=_-]+ - Jeden lub więcej znaków, które mogą występować w adresie URL (litery, cyfry, kropki, ukośniki, znaki zapytania, znaki równości, podkreślenia, myślniki).


### Zapisz zawartość do pliku `testfile.txt`:

Możesz zapisać powyższą zawartość do pliku `testfile.txt` używając poniższego polecenia w terminalu:

cat <<EOT > testfile.txt
Visit our website at http://example.com for more information.
Secure site: https://secure.example.com/login.
Find us at https://www.example.org.
Check out http://www.test.com for more details.
Some random text without a URL.
EOT


Oczekiwany wynik:

http://example.com
https://secure.example.com/login
https://www.example.org
http://www.test.com
```



Zadanie 22: Znajdź wszystkie akronimy składające się z wielkich liter (np. NASA, FBI).
Zadanie 23: Znajdź wszystkie adresy MAC w tekście.
Zadanie 24: Znajdź wszystkie liczby w notacji naukowej (np. 1.23e10).
Zadanie 25: Znajdź wszystkie słowa zaczynające się i kończące się tą samą literą.
Bardzo złożone wyrażenia regularne
Zadanie 26: Znajdź wszystkie fragmenty kodu w bloku if w danym języku programowania.
Zadanie 27: Znajdź wszystkie imiona i nazwiska w formacie Imię Nazwisko.
Zadanie 28: Znajdź wszystkie numery kart kredytowych.
Zadanie 29: Znajdź wszystkie daty w formacie YYYY-MM-DD.
Zadanie 30: Znajdź wszystkie wartości RGB w formacie rgb(255, 255, 255).
Eksperckie wyrażenia regularne
Zadanie 31: Znajdź wszystkie słowa, które są palindromami.
Zadanie 32: Znajdź wszystkie komentarze w kodzie w języku programowania C.
Zadanie 33: Znajdź wszystkie zmienne w stylu snake_case w kodzie.
Zadanie 34: Znajdź wszystkie zdania zawierające dokładnie pięć słów.
