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


## Zaawansowane wyrażenia regularne

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







Zadanie 13: Znajdź wszystkie adresy IP w tekście.
Zadanie 14: Znajdź wszystkie tagi HTML w tekście.
Zadanie 15: Znajdź wszystkie zdania kończące się znakiem zapytania ?.
Bardziej złożone wyrażenia regularne
Zadanie 16: Znajdź wszystkie słowa, które mają dokładnie pięć liter.
Zadanie 17: Znajdź wszystkie pliki o rozszerzeniu .txt, .jpg lub .png.
Zadanie 18: Znajdź wszystkie linie tekstu, które zaczynają się od cyfry.
Zadanie 19: Znajdź wszystkie zmienne w kodzie w stylu camelCase.
Zadanie 20: Znajdź wszystkie fragmenty tekstu w cudzysłowach.
Bardzo zaawansowane wyrażenia regularne
Zadanie 21: Znajdź wszystkie linki URL w tekście.
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
