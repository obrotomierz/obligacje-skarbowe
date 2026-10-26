# Obligacje oszczędnościowe Skarbu Państwa: emisje i oprocentowanie

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.23208023.svg)](https://doi.org/10.5281/zenodo.23208023)

Wersja 2026-10-26 · licencja CC BY 4.0 · DOI wszystkich wersji [10.5281/zenodo.23208023](https://doi.org/10.5281/zenodo.23208023), tej wersji [10.5281/zenodo.23676266](https://doi.org/10.5281/zenodo.23676266)

Strona zbioru: https://obrotomierz.pl/dane/obligacje/

Emisje 10 rodzin obligacji oszczędnościowych Skarbu Państwa sprzedawanych co miesiąc, od 1999-06-01 do 2026-11-01:
1 505 emisji, oprocentowanie w 7 295 okresach odsetkowych, marże, opłaty za wcześniejszy wykup,
sprzedaż i numery list emisyjnych.

## Pliki

- `emisje.csv`: jedna emisja w wierszu, 19 kolumn (słownik niżej).
- `oprocentowanie.csv`: oprocentowanie każdej emisji w każdym okresie odsetkowym, który zaczął się do 2026-09-30.
  Kolumny: `seria`, `okres` (numer okresu), `jednostka_okresu` (miesiąc, rok, półrocze albo cały okres), `oprocentowanie_pct`.

Kodowanie UTF-8 ze znacznikiem BOM, przecinek jako separator kolumn, kropka w liczbach. W Excelu kolumnę
`lista_emisyjna` ustaw jako tekst (numer „5/2007” Excel zamienia w datę). W Pythonie: `encoding="utf-8-sig"`.

## Słownik pól (emisje.csv)

| Kolumna | Znaczenie | Źródło |
|---|---|---|
| `seria` | nazwa skrócona emisji, np. EDO1036 (rodzina, miesiąc i rok wykupu) | MF i list |
| `rodzina` | OTS, ROR, DOR, TOS, COI, EDO, ROS, ROD oraz wycofane DOS i TOZ | MF i list |
| `isin` | kod ISIN serii; pusty dla emisji z ostatniego miesiąca, której MF jeszcze nie opublikował | MF |
| `sprzedaz_od` | pierwszy dzień sprzedaży serii | MF i list |
| `sprzedaz_do` | ostatni dzień sprzedaży serii | MF |
| `miesiace_do_wykupu` | czas od zakupu do wykupu w miesiącach | wyliczone |
| `okres_odsetkowy` | miesięczny, półroczny, roczny albo jednorazowo przy wykupie | list emisyjny |
| `podstawa_oprocentowania` | stałe, inflacja, stopa referencyjna NBP albo WIBOR 6M | list emisyjny |
| `kapitalizacja` | czy odsetki dopisuje się do kapitału co roku (true) czy wypłaca (false) | list emisyjny |
| `oprocentowanie_1_okres_pct` | stopa w pierwszym okresie odsetkowym, % w skali roku | MF i list |
| `marza_pct` | marża ponad inflację albo stopę NBP od drugiego okresu, % | MF i list |
| `marza_1_okres_pct` | marża pierwszego okresu w starszych emisjach, w których pierwszy rok też był indeksowany, % | list emisyjny |
| `oplata_wykup_zl` | opłata za wcześniejszy wykup jednej obligacji o nominale 100 zł, kwota z listu | list emisyjny |
| `oplata_wykup_rodzaj` | „kwota z listu” albo „bez odsetek” (OTS: przy wcześniejszym wykupie odsetki nie przysługują) | list emisyjny |
| `cena_zamiany_zl` | cena jednej obligacji przy zamianie (rolowaniu) starszej serii | MF |
| `sprzedaz_mln_zl` | sprzedaż łączna serii razem z zamianą, mln zł | MF |
| `w_tym_zamiana_mln_zl` | część sprzedaży kupiona w drodze zamiany, mln zł | MF |
| `lista_emisyjna` | numer listu emisyjnego ministra, np. 99/2026 | list emisyjny |
| `zrodlo` | „MF + list”, „MF” (bez odczytu listu) albo „list” (emisja jeszcze bez danych MF) | wyliczone |

## Wersje

Pliki w repozytorium to zawsze wersja najnowsza; każda wersja ma tag `vRRRR-MM-DD` i własny DOI w Zenodo.
Kopie z datą w nazwie leżą też na https://obrotomierz.pl/dane/obligacje/ i się nie zmieniają.

## Źródła i metoda

1. Ministerstwo Finansów, „Podstawowe informacje na temat obligacji detalicznych”, dane.gov.pl, zbiór 805
   (licencja CC BY 4.0), stan na 2026-09-30: serie, ISIN, daty, sprzedaż, oprocentowanie w okresach, marża.
2. Listy emisyjne ministra (dokumenty urzędowe ustalające warunki każdej emisji), odczytane przez nas: opłata za
   wcześniejszy wykup, podstawa oprocentowania, kapitalizacja, marża pierwszego okresu w starszych emisjach,
   numer listu. Emisje nowsze niż dane MF dopisane wprost z list.

Kontrola: stopa pierwszego okresu porównana między źródłami w 1 370 emisjach, marża
w 890; rozbieżności: 0. Każda z 1 296 opłat
sprawdzona drugim, niezależnym odczytem tekstu listu (zgodnych: 1 296). Kod serii i numer
listu pochodzą z nagłówka listu.

Poza zbiorem: jednorazowe emisje promocyjne KOS (4) i POS (3) oraz detaliczne
obligacje nieoszczędnościowe (TZ, SP, IR, RS). 99 emisji ma tylko dane MF, bez odczytu listu.
Brak stawek przyszłych okresów (zależą od inflacji i stóp). Zbiór opisuje warunki emisji; nie jest poradą inwestycyjną.

## Jak cytować

Błażewski, R. (2026). Obligacje oszczędnościowe Skarbu Państwa: emisje i oprocentowanie (wersja 2026-10-26) [Zbiór danych]. obrotomierz.pl. Zenodo. https://doi.org/10.5281/zenodo.23676266
Na podstawie danych Ministerstwa Finansów (dane.gov.pl, CC BY 4.0) i list emisyjnych.

## English summary

Dataset of Polish retail treasury savings bonds (obligacje oszczędnościowe Skarbu Państwa) issued monthly
since 1999: 1 505 issues across 10 bond families, first-period rates and margins, interest rate
for every interest period (7 295 rows), early redemption fees read from the official issue letters (not
present in the Ministry of Finance data), sales and issue letter numbers. Built from the Ministry of Finance open data
(dane.gov.pl, CC BY 4.0) cross-checked against the issue letters (0 discrepancies). Updated monthly.
Field names and documentation are in Polish. License: CC BY 4.0.

Błędy w danych: https://obrotomierz.pl/kontakt/
