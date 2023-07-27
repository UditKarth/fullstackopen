```mermaid
sequenceDiagram
    participant browser
    participant server
    
    browser -> server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    server -->> browser: HTNL Header
    Note right of server: The server sends the redirect request back to the browser, sending it to the location in the header
    
    browser -> server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    server -->> browser: HTML document
    deactivate server

    browser -> server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    server -->> browser: the css file
    deactivate server

    browser -> server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    server -->> browser: the JavaScript file
    deactivate server

    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server

    browser -> server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    server -->> browser: [{ "content": "HTML is easy", "date": "2023-1-1" }, ... ]
    deactivate server

    Note right of browser: The browser executes the callback function that renders the notes
