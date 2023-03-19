sequenceDiagram
    participant browser
    participant server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server-->>browser: HTML document
    deactivate server

    Note right of selain: Selain lataa SPA käyttöliittymän

    browser->>browser: Käyttöliittymän renderöinti

    browser->>server: AJAX GET-pyyntö https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: muistiinpanodata JSON-muodossa
    deactivate server

    Note right of selain: Selain käyttää JavaScript-koodia muistiinpanojen lataamiseen ja renderöintiin

    selain->>selain: Muistiinpanojen renderöinti