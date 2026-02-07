# Instrukcja: Wrzucenie dokumentacji do GitLab

Ten przewodnik krok po kroku pokazuje jak wrzucić dokumentację GitBook do GitLab i skonfigurować synchronizację.

## Krok 1: Przygotowanie lokalnego repozytorium Git

### 1.1. Inicjalizacja repozytorium Git

Otwórz terminal w katalogu projektu i wykonaj:

```bash
cd "/Users/msuchon/Documents/Unwaste Documentation 2"
git init
```

### 1.2. Dodanie wszystkich plików do repozytorium

```bash
# Dodaj wszystkie pliki (oprócz tych w .gitignore)
git add .

# Sprawdź co zostanie dodane
git status
```

### 1.3. Utworzenie pierwszego commita

```bash
git commit -m "Initial commit: GitBook documentation structure"
```

## Krok 2: Utworzenie repozytorium w GitLab

### 2.1. Zaloguj się do GitLab

1. Otwórz przeglądarkę i przejdź do [GitLab.com](https://gitlab.com) (lub Twojego instancji GitLab)
2. Zaloguj się na swoje konto

### 2.2. Utwórz nowe repozytorium

1. Kliknij przycisk **"New project"** lub **"+"** w prawym górnym rogu
2. Wybierz **"Create blank project"**
3. Wypełnij formularz:
   - **Project name**: `unwaste-documentation` (lub dowolna nazwa)
   - **Project slug**: zostanie wygenerowany automatycznie
   - **Visibility Level**: wybierz **Private** (prywatne) lub **Public** (publiczne)
   - **Initialize repository with a README**: **NIE zaznaczaj** (mamy już pliki lokalnie)
4. Kliknij **"Create project"**

### 2.3. Skopiuj URL repozytorium

Po utworzeniu projektu, GitLab pokaże Ci URL repozytorium. Będzie wyglądał mniej więcej tak:
- HTTPS: `https://gitlab.com/twoja-nazwa-uzytkownika/unwaste-documentation.git`
- SSH: `git@gitlab.com:twoja-nazwa-uzytkownika/unwaste-documentation.git`

**Skopiuj URL HTTPS** - będziesz go potrzebować w następnym kroku.

## Krok 3: Połączenie lokalnego repozytorium z GitLab

### 3.1. Dodaj remote (zdalne repozytorium)

W terminalu wykonaj (zamień URL na swój):

```bash
git remote add origin https://gitlab.com/twoja-nazwa-uzytkownika/unwaste-documentation.git
```

### 3.2. Sprawdź czy remote został dodany poprawnie

```bash
git remote -v
```

Powinieneś zobaczyć:
```
origin  https://gitlab.com/twoja-nazwa-uzytkownika/unwaste-documentation.git (fetch)
origin  https://gitlab.com/twoja-nazwa-uzytkownika/unwaste-documentation.git (push)
```

### 3.3. Zmień nazwę głównej gałęzi na `main` (jeśli potrzeba)

```bash
git branch -M main
```

## Krok 4: Wysłanie plików do GitLab

### 4.1. Push do GitLab

```bash
git push -u origin main
```

**Uwaga**: Jeśli GitLab wymaga uwierzytelniania:
- Może poprosić Cię o login i hasło
- Dla bezpieczeństwa użyj **Personal Access Token** zamiast hasła (patrz Krok 5)

### 4.2. Sprawdź w GitLab

Po udanym pushu, odśwież stronę projektu w GitLab. Powinieneś zobaczyć wszystkie pliki dokumentacji.

## Krok 5: Konfiguracja Personal Access Token (opcjonalne, zalecane)

Zamiast używać hasła, GitLab zaleca używanie Personal Access Token.

### 5.1. Utwórz Token w GitLab

1. W GitLab przejdź do **User Settings** → **Access Tokens**
2. Wypełnij formularz:
   - **Token name**: `git-push-documentation`
   - **Expiration date**: wybierz datę wygaśnięcia (lub zostaw puste)
   - **Select scopes**: zaznacz **`write_repository`**
3. Kliknij **"Create personal access token"**
4. **WAŻNE**: Skopiuj token natychmiast - nie będziesz mógł go zobaczyć ponownie!

### 5.2. Użyj Token zamiast hasła

Przy następnym `git push`, gdy GitLab poprosi o hasło:
- **Username**: Twoja nazwa użytkownika GitLab
- **Password**: Wklej **Personal Access Token** (nie hasło!)

## Krok 6: Konfiguracja Git Sync w GitBook

### 6.1. Otwórz GitBook

1. Przejdź do [GitBook.com](https://www.gitbook.com)
2. Zaloguj się na swoje konto
3. Utwórz nowy Space (lub użyj istniejącego)

### 6.2. Włącz Git Sync

1. W ustawieniach Space znajdź sekcję **"Git Sync"** lub **"Integrations"**
2. Kliknij **"Connect Git repository"** lub **"Enable Git Sync"**
3. Wybierz **GitLab** jako provider
4. Autoryzuj GitBook do dostępu do Twojego GitLab

### 6.3. Skonfiguruj synchronizację

1. **Repository**: Wybierz `unwaste-documentation` z listy
2. **Branch**: Wybierz `main`
3. **Project directory**: Zostaw puste (lub `/` jeśli GitBook tego wymaga)
4. **Root path**: Zostaw puste (GitBook użyje `.gitbook.yaml`)

### 6.4. Zapisz i synchronizuj

1. Kliknij **"Save"** lub **"Sync"**
2. GitBook pobierze pliki z GitLab
3. Dokumentacja powinna pojawić się w GitBook!

## Krok 7: Weryfikacja

### 7.1. Sprawdź w GitBook

- Otwórz swój Space w GitBook
- Sprawdź czy wszystkie strony są widoczne w nawigacji
- Sprawdź czy obrazy się wyświetlają poprawnie

### 7.2. Sprawdź strukturę

- Otwórz kilka stron i sprawdź czy linki działają
- Sprawdź czy obrazy są widoczne
- Sprawdź czy SUMMARY.md odpowiada strukturze nawigacji

## Krok 8: Dalsza praca (workflow)

### 8.1. Edycja dokumentacji lokalnie

```bash
# Edytuj pliki w edytorze
# Następnie:
git add .
git commit -m "Opis zmian"
git push
```

### 8.2. GitBook automatycznie zsynchronizuje zmiany

- Po `git push`, GitBook automatycznie pobierze zmiany
- Może to zająć kilka minut
- Sprawdź status synchronizacji w ustawieniach Git Sync

## Rozwiązywanie problemów

### Problem: "Permission denied" przy push

**Rozwiązanie**: 
- Sprawdź czy masz dostęp do repozytorium w GitLab
- Użyj Personal Access Token zamiast hasła
- Sprawdź czy URL remote jest poprawny: `git remote -v`

### Problem: Obrazy nie wyświetlają się w GitBook

**Rozwiązanie**:
- Sprawdź czy wszystkie obrazy są w `.gitbook/assets/`
- Sprawdź czy ścieżki w plikach markdown są poprawne: `../.gitbook/assets/nazwa-pliku.png`
- Upewnij się że obrazy zostały dodane do Git: `git add .gitbook/assets/`

### Problem: Struktura nawigacji nie odpowiada SUMMARY.md

**Rozwiązanie**:
- Sprawdź czy `SUMMARY.md` jest w katalogu głównym
- Sprawdź czy `.gitbook.yaml` wskazuje na właściwy plik SUMMARY
- W GitBook przejdź do ustawień i wymuś ponowną synchronizację

### Problem: Konflikty przy synchronizacji

**Rozwiązanie**:
- Jeśli edytowałeś w GitBook i lokalnie, mogą wystąpić konflikty
- Rozwiąż konflikty w GitLab lub lokalnie
- GitBook automatycznie zsynchronizuje rozwiązane konflikty

## Przydatne komendy Git

```bash
# Sprawdź status
git status

# Zobacz historię commitów
git log --oneline

# Zobacz różnice
git diff

# Pobierz zmiany z GitLab
git pull

# Wyślij zmiany do GitLab
git push

# Sprawdź remote
git remote -v

# Zmień URL remote (jeśli potrzeba)
git remote set-url origin NOWY_URL
```

## Podsumowanie

Po wykonaniu wszystkich kroków:
- ✅ Dokumentacja jest w GitLab
- ✅ GitBook synchronizuje się z GitLab
- ✅ Możesz edytować lokalnie i pushować zmiany
- ✅ GitBook automatycznie aktualizuje dokumentację

**Gotowe!** Twoja dokumentacja jest teraz zsynchronizowana między GitLab a GitBook.
