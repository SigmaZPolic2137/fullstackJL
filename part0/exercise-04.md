sequenceDiagram
    participant browser
    participant server

    Note over browser: Użytkownik wpisuje tekst i klika przycisk "Save"

    browser->>server: POST https://helsinki.fi
    activate server
    Note over server: Serwer zapisuje nową notatkę w tablicy
    server-->>browser: HTTP 302 (Przekierowanie do /notes)
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: Dokument HTML
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: Plik CSS
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: Plik JavaScript
    deactivate server

    Note right of browser: Przeglądarka uruchamia kod JS pobierający dane JSON

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: Zaktualizowana lista notatek w formacie JSON
    deactivate server

    Note right of browser: Wywołanie funkcji zwrotnej (callback) i wyrenderowanie notatek wraz z nowym wpisem
