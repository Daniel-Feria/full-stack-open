// Ejercicios 0.1.-0.6.
sequenceDiagram
    participant User
    participant Browser
    participant Server

    User->>Browser: Escribe una nota y hace clic en "Save"
    
    Note right of Browser: La nota es leída desde el campo de entrada y se genera un objeto JSON

    Browser->>Server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate Server
    Note right of Server: El servidor recibe la nueva nota y la almacena
    Server-->>Browser: Respuesta HTTP 201 Created
    deactivate Server

    Note right of Browser: El navegador vuelve a cargar la lista de notas

    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate Server
    Server-->>Browser: JSON con la lista actualizada de notas
    deactivate Server

    Note right of Browser: Se ejecuta la función de callback para renderizar la nota en la página