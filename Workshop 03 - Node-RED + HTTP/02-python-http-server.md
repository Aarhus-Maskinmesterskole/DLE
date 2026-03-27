# Python HTTP server
I denne øvelse skal du oprette en simpel HTTP-server i Python, der kan håndtere GET-forespørgsler og returnere en HTML-side med en besked og det aktuelle tidspunkt.

## Hvad er en HTTP-server?
<!-- kan du lave det som bullets? -->
- En HTTP-server er en softwareapplikation, der håndterer HTTP-forespørgsler fra klienter (f.eks. webbrowsere).
- Den kan sende HTML-sider, billeder, JSON-data eller andre ressourcer som svar.
- HTTP-serveren lytter på en bestemt port og venter på indkommende forespørgsler.
- Når en forespørgsel modtages, behandler serveren den og sender et svar tilbage til klienten.

## Opgave
1. Opret en Python-fil, fx `http_server.py`.
2. Kopiér og indsæt følgende kode i filen:
```python
from http.server import HTTPServer, BaseHTTPRequestHandler
import time

class MyServer(BaseHTTPRequestHandler):
    # Håndterer GET-forespørgsler
    def do_GET(self):
        self.send_response(200) # OK status
        self.send_header("Content-type", "text/html")
        self.end_headers()
        
        # Indholdet der sendes til browseren
        self.wfile.write(bytes("<html><head><title>Min Python Server</title></head>", "utf-8"))
        self.wfile.write(bytes("<body>", "utf-8"))
        self.wfile.write(bytes(f"<p>Request modtaget kl: {time.strftime('%H:%M:%S')}</p>", "utf-8"))
        self.wfile.write(bytes("<h1>Hej fra din egen Python server!</h1>", "utf-8"))
        self.wfile.write(bytes("</body></html>", "utf-8"))

# Konfiguration
hostName = "localhost"
serverPort = 8080

if __name__ == "__main__":        
    webServer = HTTPServer((hostName, serverPort), MyServer)
    print(f"Server startede på http://{hostName}:{serverPort}")

    try:
        webServer.serve_forever()
    except KeyboardInterrupt:
        pass

    webServer.server_close()
    print("Server stoppet.")
```
3. Kør Python-filen i terminalen:
```bash
python http_server.py

OUTPUT -> Server startede på http://localhost:8080
```
4. Åbn en webbrowser og indtast `http://localhost:8080` i adresselinjen.
5. Du skulle nu se en HTML-side med beskeden "Hej fra din egen Python server!" og det aktuelle tidspunkt for, hvornår forespørgslen blev modtaget.

## Forklaring af koden
- Vi importerer nødvendige moduler: `HTTPServer` og `BaseHTTPRequestHandler` fra `http.server` og `time` for at få det aktuelle tidspunkt.
- Vi definerer en klasse `MyServer`, der arver fra `BaseHTTPRequestHandler`. Denne klasse håndterer HTTP-forespørgsler.
- `do_GET`-metoden håndterer GET-forespørgsler ved at sende en 200 OK status, angive indholdstypen som HTML og skrive HTML-indholdet til klienten.
- Vi konfigurerer serveren til at lytte på `localhost` og port `8080`.
- Serveren startes, og den vil fortsætte med at køre, indtil den stoppes manuelt (fx ved at trykke Ctrl+C i terminalen).
- Når serveren modtager en GET-forespørgsel, vil den returnere en HTML-side med en besked og det aktuelle tidspunkt.