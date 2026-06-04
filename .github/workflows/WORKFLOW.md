# Advanced CI/CD Workflow

## Struktura jobów

build → test → deploy (tylko main) → status (zawsze)

## Joby

### build
Instaluje Python, tworzy artefakt z informacjami o buildzie.
Artefakt zapisywany tylko dla gałęzi main.

### test
Uruchamia się po build. Wykonuje testy pytest.

### deploy
Uruchamia się TYLKO na gałęzi main.
Pobiera artefakt i symuluje wdrożenie.

### status
Uruchamia się zawsze. Wyświetla wyniki wszystkich jobów.

## Zmienne środowiskowe

| Zmienna        | Wartość    |
|----------------|------------|
| APP_NAME       | devops-app |
| PYTHON_VERSION | 3.11       |

## Warunki

- deploy działa tylko gdy: github.ref == 'refs/heads/main'
- Artefakt zapisywany tylko dla main
- status działa zawsze dzięki: if: always()
