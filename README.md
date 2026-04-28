# Generator bezpiecznych haseł

![Python CI](https://github.com/Klxdak/K2D/actions/workflows/main.yml/badge.svg)

## Krótki opis
Projekt studencki w Pythonie z interfejsem graficznym (`customtkinter`), który generuje losowe hasła o konfigurowalnej długości i złożoności.

## Funkcje
- Generowanie hasła o długości od 4 do 32 znaków (domyślnie 12).
- Włączanie i wyłączanie dużych liter.
- Włączanie i wyłączanie cyfr.
- Włączanie i wyłączanie znaków specjalnych.
- Kopiowanie aktualnie wygenerowanego hasła do schowka.
- Ocena siły hasła (`Słabe`, `Średnie`, `Mocne`) z paskiem postępu.
- Historia ostatnich 15 haseł z możliwością kopiowania.
- Przełączanie trybu jasny/ciemny.

## Wymagania
- Python 3.12 (zgodnie z `Dockerfile` i workflow CI).
- `pip` do instalacji zależności.
- Środowisko graficzne systemu (aplikacja jest okienkowa, `customtkinter`/`tkinter`).

Zależności projektowe znajdują się w pliku `requirements.txt`:
- `customtkinter`
- `pytest`
- `flake8`

## Instalacja
1. Sklonuj repozytorium:
   ```bash
   git clone https://github.com/Klxdak/K2D.git
   ```
2. Przejdź do katalogu projektu:
   ```bash
   cd K2D
   ```
3. (Opcjonalnie) utwórz środowisko wirtualne:
   ```bash
   python -m venv .venv
   ```
4. (Opcjonalnie) aktywuj środowisko wirtualne:

   Windows:
   ```bash
   .venv\Scripts\activate
5. Zainstaluj zależności z `requirements.txt`:
   ```bash
   python -m pip install -r requirements.txt
   ```

## Jak uruchomić aplikację
```bash
python src/generator.py
```

W systemie Windows możesz również użyć:

```bash
py src/generator.py
```

## Jak korzystać z generatora
1. Ustaw długość hasła suwakiem.
2. Zaznacz, czy hasło ma zawierać duże litery, cyfry i symbole.
3. Kliknij `Generuj`.
4. Skopiuj hasło przyciskiem `Kopiuj`.
5. Sprawdź siłę hasła na pasku i etykiecie (`Słabe` / `Średnie` / `Mocne`).
6. Otwórz `Historia`, aby zobaczyć i skopiować wcześniej wygenerowane hasła.
7. Przełącz tryb jasny/ciemny przełącznikiem `Tryb`.

## Testowanie
Uruchamianie testów jednostkowych:

```bash
python -m pytest
```

Zakres testów w `tests/test_generator.py` obejmuje:
- długość domyślną hasła,
- długość zadaną przez parametr,
- generowanie wyłącznie liter (po wyłączeniu cyfr i znaków specjalnych),
- losowość kolejnych wygenerowanych haseł.

## Docker
Projekt zawiera `Dockerfile`, więc można uruchomić go w kontenerze.

1. Zbuduj obraz:
   ```bash
   docker build -t password-generator .
   ```
2. Uruchom kontener:
   ```bash
   docker run --rm password-generator
   ```

## Zrzuty ekranu

### Uruchomienie w Dockerze
![Uruchomienie w Dockerze](zdjecia/zdjęcie_Docker_run.png)

### Uruchomienie testów
![Uruchomienie testów](zdjecia/zdjecie_testu.png)

W kontenerze wykonywane są testy (`pytest`), a następnie uruchamiany jest `src/generator.py`.
W środowisku bez GUI aplikacja wypisze komunikat o braku środowiska graficznego.

Możesz też uruchomić obraz publikowany w Docker Hub:

```bash
docker run --rm kvbikk/password-generator:latest
```

## Struktura projektu
```text
K2D/
├── .github/workflows/main.yml
├── Dockerfile
├── README.md
├── requirements.txt
├── src/
│   ├── generator.py
│   └── logika.py
├── tests/
│   └── test_generator.py
└── zdjecia/
```

## CI/CD
Workflow GitHub Actions (`.github/workflows/main.yml`) uruchamia się dla `push` i `pull_request` na gałąź `main` i wykonuje:
- instalację zależności,
- linting (`flake8`),
- testy (`pytest`),
- logowanie do Docker Hub,
- budowanie i publikację obrazu Docker,
- próbę uruchomienia aplikacji.

## Autorzy / informacje o projekcie
- Projekt wykonany jako aplikacja studencka.
- Technologia: Python + customtkinter + pytest + Docker + GitHub Actions.
