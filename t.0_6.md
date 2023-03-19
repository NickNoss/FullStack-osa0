sequenceDiagram
    participant browser
    participant server

    browser->>browser: Käyttöliittymän renderöinti

    Note right of selain: Kirjoitetaan uusi muistiinpano

    browser->>server: AJAX POST-pyyntö osoitteeseen https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate server
    server-->>browser: vastaus JSON-muodossa
    deactivate server

    Note right of selain: Selain aloittaa JavaScript koodin toteutusta muistiinpanon tallentamiseksi palvelimelle

    browser->>browser: Lisätään muistiinpano käyttöliittymään

    Note right of selain: Käyttöliittymän päivityksen myötä käyttäjä näkee uuden muistiinpanon
