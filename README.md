```mermaid
sequenceDiagram
  

  Käyttäjä->Selain: Kirjoittaa muistiinpanon ja painaa "Save"
  Selain->Serveri: POST https://studies.cs.helsinki.fi/exampleapp/new_note
  Serveri-->>Selain: Status 302 Found(redirect pyyntö)
  Selain->Serveri: GET https://studies.cs.helsinki.fi/exampleapp/notes
  Serveri-->>Selain: status 304 Not Modified(HTML)
  Selain->Serveri: GET https://studies.cs.helsinki.fi/exampleapp/main.css
  Serveri-->>Selain: status 304 Not Modified(main.css)
  Selain->Serveri: GET https://studies.cs.helsinki.fi/exampleapp/main.js
  Serveri-->>Selain: status 304 Not Modified(main.js)
  Selain->Serveri: GET https://studies.cs.helsinki.fi/exampleapp/data.json
  Serveri-->>Selain: status 200 OK(data.json)
  Selain->Käyttäjä: selain näyttää käyttäjälle kirjoitetun muistiinpanon
```
```mermaid
sequenceDiagram
  participant Käyttäjä
  participant Selain
  participant Serveri

  Käyttäjä-->>Selain: käyttäjä menee sivulle https://studies.cs.helsinki.fi/exampleapp/spa
  Selain-->>Serveri: GET https://studies.cs.helsinki.fi/exampleapp/spa
  Serveri-->>Selain: status 200 OK (HTML)
  Selain-->>Serveri: GET https://studies.cs.helsinki.fi/exampleapp/main.css
  Serveri-->>Selain: status 200 OK (main.css)
  Selain-->>Serveri: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
  Serveri-->>Selain: status 200 OK (main.js)
  Selain-->>Serveri: GET https://studies.cs.helsinki.fi/exampleapp/data.json
  Serveri-->>Selain: status 200 OK (data.json)
  Selain-->>Serveri: GET https://studies.cs.helsinki.fi/favicon.ico
  Serveri-->>Selain: status 404 Not Found (favicon.ico)
  Selain-->>Käyttäjä: selain näyttää käyttäjälle muistiinpano sivun
```
```mermaid
sequenceDiagram
  participant Käyttäjä
  participant Selain
  participant Serveri

  Käyttäjä-->>Selain: käyttäjä kirjoittaa muistiinpanon ja painaa "save"
  Selain-->>Serveri: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa

  note over Selain:
  type: json
  content	"test"
  date	"2025-05-27T02:05:17.987Z"
  message	"note created"
  end note

  Serveri-->>Selain: status 201 Created
  Selain-->>Käyttäjä: selain näyttää kirjoitetun muistiinpanon ilman että sivu lataa uudelleen
```
