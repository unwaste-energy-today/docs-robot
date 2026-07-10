# Instrukcja Instalacji

Polska wersja instrukcji instalacji addonu Unwaste w Home Assistant. Angielski odpowiednik: [Local installation](Installation/Local%20installation.md).


---

## Dodanie repozytorium Unwaste

1. Wejdź w Home Assistant → **Settings** → **Add-ons** → **Add-on Store**.
2. W lewym górnym rogu otwórz menu → **Repositories**.
3. Wprowadź adres repozytorium i kliknij **Add**:

**https://gitlab.com/unwaste/public/unwaste-haos-repository-production**

4. Zamknij okno. Z tego samego menu wybierz **Check for updates**.
5. **Odśwież stronę przeglądarki** — bez tego addon Unwaste może nie pojawić się na liście.


---

## Instalacja addonu

1. Znajdź **Unwaste** na liście addonów.
2. Kliknij **Install** i poczekaj na zakończenie instalacji.


---

## Konfiguracja addonu

Na karcie **Configuration**:

* **Use external database** — wyłączone = wbudowana baza (domyślnie).
* Gdy **Use external database** jest włączone, uzupełnij adres serwera, port, użytkownika, hasło, nazwę bazy i SSL.

Gdy **Use external database** jest wyłączone, pola połączenia z bazą zostaw puste.

Szczegóły: [Robot settings](../Configuration/Robot%20settings.md).


---

## Uruchomienie

Na karcie **Info** włącz:

* **Start on boot**
* **Watchdog** (zalecane)
* **Show in sidebar** (zalecane)

Kliknij **Start**. Otwórz panel Unwaste z paska bocznego i przejdź do [Initial configuration](Initial%20configuration.md).
