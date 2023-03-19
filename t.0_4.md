sequenceDiagram
    participant browser
    participant server
    participant database

    Note right of browser: Selain lähettää POST-pyynnön osoitteeseen https://studies.cs.helsinki.fi/exampleapp/new_note, 

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    server->>database: INSERT new note into JSON-database
    activate database
    database->>server: returns "success" message
    deactivate database
    server-->>browser: redirect to https://studies.cs.helsinki.fi/exampleapp/notes

    Note right of browser: palvelin lähettää uudelleenohjauspyynnön selaimelle osoitteeeen notes

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML document
    deactivate server
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the css file
    deactivate server
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server
    
    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "", "date": "2023-1-1" }, ... ]
    deactivate server    

    Note right of browser: The browser executes the callback function that renders the notes 