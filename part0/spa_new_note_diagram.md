```mermaid
sequenceDiagram
    participant browser
    participant server

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    Note right of browser: The post request contains the new note as JSON data, along with content-type in the header
    activate server
    Note right of server: The server receives the POST request and handles the event to add the note to the HTML list
    server-->>browser: updated HTML document
    deactivate server
