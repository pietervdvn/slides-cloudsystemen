# Container orchestration

---
![Docker Compose](./afbeeldingen/docker-compose.webp)
note:
- kan command line argumenten bijhouden in file
- kan meerdere containers samen opstarten, meteen in netwerk, met volumes
- gebruikt YAML syntax
- intro tot YAML en YAML converter gelinkt
---

Mijn webservice bestaat uit 10 containers...

Hoe onderhoud ik dit?
Wat als één component crashed?
Wat als één component update?


---

```dockerfile
docker run service_db ...
docker run service_frontend -p 443:1234 ...
docker run service_backend -p 1222:351
docker run caddy ....
```

note:
dit wordt een soepje

---

#### docker-compose.yml

```yaml
version: '3.8'  # Version of the Docker Compose file format
services:  # The services (containers) that are part of the application
  web:
    image: nginx:latest  # Docker image to use
    ports:
      - "8080:80"  # Map port 80 of the container to port 8080 on the host
    networks:
      - my_network  # Specify networks for the service to join

  db:
    image: postgres:latest  # Docker image for the database
    environment:
      POSTGRES_PASSWORD: example  # Set environment variables
    networks:
      - my_network  # Join the same network as the web service
    volumes:
      - db_data:/var/lib/postgresql/data  # Bind volume for persistent data
    restart: unless-stopped # other options: always, never

networks:  # Define custom networks
  my_network:
    driver: bridge  # Use Docker's default bridge network

volumes:  # Define named volumes for persistent storage
  db_data:

```


note:
Moet vaste name hebben
- Zie ook https://dev.to/abhay_yt_52a8e72b213be229/understanding-docker-compose-file-format-structure-options-and-best-practices-3nob

---

### Intermezzo: YAML?

WTF is die rare JSON?

https://spacelift.io/blog/yaml

---

Alles in één keer aanzetten (of afzetten):

(De working directory moet het mapje zijn dat de `docker-compose.yml` bevat)

- `docker compose build`
- `docker compose up`
- `docker compose down`
---

## Aandachtspunten
---
- netwerken: impliciet vs. expliciet
- volumes definiëren, mounted folders niet
- ports: host:guest, niet omgekeerd
- `depends_on`: container is **gestart**, niet altijd **klaar**
    - voeg bijvoorbeeld script toe
- `environment`: omgevingsvariabelen voor configuratie en secrets

---

1. Download op digitap het mysql-gebaseerde gastenboek
2. Maak hier een docker-image voor
3. Maak een docker-compose met die je gastenboek en de mySQL-databank opstart
   - Je mag in de code het wachtwoord en IP-adres aanpassen om te testen
   - Probeer om met een env-variable het IP-adres van de server door te geven aan de app
   - Probeer om met een docker-secret het wachtwoord door te geven aan de app
4. Zorg ervoor dat deze samenwerken, test
