sequenceDiagram
    participant browser
    participant server

    Note over browser: Użytkownik wpisuje tekst i klika przycisk "Save"
    Note right of browser: Kod JS blokuje domyślne przeładowanie strony,<br/>dodaje notatkę do lokalnej listy i od razu ją przerysowuje (DOM)

    browser->>server: POST https://helsinki.fi
    activate server
    Note over browser: Dane wysyłane jako JSON: { "content": "...", "date": "..." }
    Note over server: Serwer zapisuje otrzymaną notatkę w tablicy
    server-->>browser: HTTP 201 Created (Potwierdzenie zapisu)
    deactivate server
    
    Note right of browser: Brak dodatkowych zapytań i brak przeładowania strony
