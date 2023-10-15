```mermaid
sequenceDiagram
    participant Browser
    participant Server
    
    note right of Browser: Browser sends HTTP GET request to server
    Browser->>Server: GET https://fullstack-exampleapp.herokuapp.com/notes
    Server-->>Browser: HTML-code 200,HTML-code
    Browser->>Server: GET https://fullstack-exampleapp.herokuapp.com/main.css
    Server-->>Browser: main.css
    Browser->>Server: GET https://fullstack-exampleapp.herokuapp.com/main.js
    Server-->>Browser: main.js
    note right of Browser: Browser starts executing main.js that requests JSON data from server
    Browser->>Server: HTTP GET https://fullstack-exampleapp.herokuapp.com/data.json
    Server-->>Browser: JSON-data
    note right of Browser: Browser executes the event handler that renders notes to display
    note right of Browser: user fills the form and clicks submit
    Browser->>Server: POST https://fullstack-exampleapp.herokuapp.com/new_note
    note left of Server: Server creates new object with content req.body.note and  date: new Date(),then new object is pushed to array notes
    Server-->>Browser: HTML-code 302,URL redirect to /notes
    Browser->>Server:HTTP GET https://fullstack-exampleapp.herokuapp.com/notes
    Server-->>Browser: HTML-code 200,HTML-code 
    Browser->>Server: GET https://fullstack-exampleapp.herokuapp.com/main.css
    Server-->>Browser: main.css
    Browser->>Server: GET https://fullstack-exampleapp.herokuapp.com/main.js
    Server-->>Browser: main.js
    note right of Browser: Browser starts executing main.js that requests JSON data from server
    Browser->>Server: HTTP GET https://fullstack-exampleapp.herokuapp.com/data.json
    Server-->>Browser: JSON-data
    note right of Browser: Browser executes the event handler that renders notes to display
    
```