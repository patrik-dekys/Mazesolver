# IZP Projekt 2 – Bludisko

Implementácia riešenia trojuholníkového bludiska podľa pravidla ľavej/​pravej ruky v jazyku C (C11). Program načíta popis bludiska, skontroluje jeho správnosť a vie vypísať trasu zvoleným pravidlom.

## Formát vstupu
- Textový súbor, prvý riadok: `R C` (počet riadkov a stĺpcov trojuholníkov).
- Nasleduje `R` riadkov po `C` čísel z intervalu **0–7**.
- Bity čísla určujú steny trojuholníka: `1` = ľavá, `2` = pravá, `4` = horná/spodná podľa orientácie bunky.

## Preklad
Použite ľubovoľný C11 kompilátor. Príklady:
```bash
gcc -std=c11 -Wall -Wextra -pedantic -o maze maze.c
```
alebo pomocou CMake:
```bash
cmake -S . -B cmake-build
cmake --build cmake-build
```
Binárka má názov `maze` (pri CMake podľa konfigurácie).

## Spustenie
```
./maze --help
./maze --test file.txt
./maze --rpath R C file.txt   # pravá ruka, začiatok na riadku R, stĺpci C
./maze --lpath R C file.txt   # ľavá ruka, začiatok na riadku R, stĺpci C
```
- `--test` vypíše `Valid` / `Invalid` podľa konzistencie vstupu.
- `--rpath` / `--lpath` tlačia navštívené súradnice `riadok,stĺpec` po jednom na riadok, kým sa nenájde východ.

## Príklady
```bash
./maze --test file.txt
./maze --rpath 1 1 file.txt
./maze --lpath 3 4 file.txt
```

## Testovacie súbory
V priečinku `test/` sú ukážkové mapy a skripty:
- `test/1/maze` – vstupný súbor, `test/1/maze-test.sh`
- `test/2/maze` – vstupný súbor, `test/2/test_maze.sh`

## Návratové kódy
- `0` úspech (validácia prešla alebo trasa nájdená/ukončená).
- `1` chyba vstupu alebo nesprávne argumenty.

## Poznámky
- Vstupný bod musí ležať na okraji bludiska a mať aspoň jednu otvorenú stenu, inak program skončí s hlásením „Not possible to enter maze“.
- Program nevyužíva žiadne externé knižnice okrem štandardnej knižnice C.
