# Vervolg Docker

Tip: `docker exec -it NAAM_CONTAINER bash`
---

### Opfrissing: docker image maken
- Download "voorbeeldapplicatie Express"
- Maak een nieuwe Dockerfile op basis van <code>node:20</code>
- Kopieer de nodige bestanden naar een map <code>/app</code> in de image. 
- Zorg dat de nodige packages geïnstalleerd worden in de image (`npm ci`).
- Zorg dat de applicatie wordt opgestart wanneer de container start.
- Zorg ook dat hij naar de gebruikte poort luistert.
- Bouw en start de container.

---

Opslaan als `Dockerfile` naast bestanden

```dockerfile
FROM node:20

# maakt ook meteen deze directory indien deze niet bestaat
WORKDIR /app
# Kopieer de inhoud van de huidige directory van host naar de WORKDIR in de image
COPY . .
# Installeer dependencies (nodejs)
RUN npm ci
# Exporteer poort 3000
EXPOSE 3000

# Wanneer de container start: voer dit commando uit
CMD [ "nodejs", "hello.js" ]
```

---

Hoe uitvoeren:
1. cd `<directory>`	
2. `docker build . -t <tagname>`
3. `docker run -p 3000:3000 <tagname>`
4. Bezoek [localhost:3000](https://localhost:3000) - hierop zou je express-app te zien moeten zijn

---

# Data opslaan

Hoe zorgen we ervoor dat data behouden blijft als we een container verwijderen?

---

# Bind mounts

`docker run -v /path/on/host:/path/in/container <imagename>`

Gedeelde map tussen host en container

Nadeel: wat als user `docker` geen (schrijf)-toegang heeft tot `/path/on/host`?

note:
- bind mount = gewoon map ergens "aansluiten" op container
- makkelijk om snel iets mee op te zetten; lastig voor permissies en management
- gespecifieerd als pad op de lokale machine

---

# Volumes

1. `docker volume create my-volume`
2. `docker run -v my-volume:/path/in/container`

Docker maakt een map aan en beheert zelf de permissies

note:
- gespecifieerd via naam

---

## Volume management

- `docker volume create VOLUMENAAM`
- `docker volume rm VOLUMENAAM`
- `docker volume ls`

---

### Volume exporteren

```bash
docker run --rm \
-v db-volume:/db:ro \
-v $(pwd):/backup \
debian \
tar cvf /backup/backup.tar /db
```

Ofwel:

`docker volume inspect <volume-name>` toont fysieke pad

Bestanden zichtbaar mits root-privileges

note:
- keuze distributie is arbitrair
- we mounten zowel het volume als de huidige map (via bind mount)
- we archiveren de inhoud van het volume in de bind mount (dus komt in huidige map terecht)
- niet uit het hoofd te kennen, hou gewoon ergens bij
---

Demonstratie: Express applicatie uitbreiden

note:
- Express applicatie gastenboek staat al in onderdeel Docker Compose op DigitAP
- "in memory" tot en met "in folder"
---

1. Maak een volume, `db-volume`
2. Maak een `mysql` container, waarvan de data bijgehouden wordt in dit volume
    1. Check eerst "where to store data" op de Docker Hub pagina!
    2. Het wachtwoord van `root` is `DitIsGoed`
    3. Er is een gewone user `dbUser`
    4. Het wachtwoord van deze user is `DitIsGoed`
    5. De database heet `Cloudsystemen`
3. Maak een tabel naar keuze aan met minstens één rij aan data
4. Verwijder de container
5. Maak een nieuwe container, log daar op in en controleer of je de data terugvindt

note:
https://hub.docker.com/_/mysql voor documentatie
`docker create volume cloudsystemen-db` om volume te maken
`docker run --name Cloudsystemen -v cloudsystemen-db:/var/lib/mysql -e MYSQL_DATABASE=Cloudsystemen -e MYSQL_ROOT_PASSWORD=DitIsGoed mysql`
Noot: mogelijks is `3306` al in gebruik, dan kan je een andere poort gebruiken met `-p <poortnummer>:3306`

Beheren met: 
`mysql -h 127.0.0.1 -P 3306 --user=root --password Cloudsystemen` opstarten, volume koppelen (-v), via environment variabelen (-e) mysql instrueren

Dan kom je in een SQL-interpreter, daar kan je dan commando's uitvoeren, bv:

TODO: user maken
`CREATE TABLE persoon(id int, name VARCHAR(255));`
`INSERT INTO persoon VALUES (0, "pietervdvn");`
`SELECT * FROM Persoon;`

Controleer of de data in je volume staat

`docker volume inspect cloudsystemen-db`, dan gegeven pad bekijken

`docker stop Cloudsystemen`
`docker rm Cloudsystemen`

Als je dan herstart met eerste commando, heb je dezelfde data terug!



---
Container networking

note:
- start twee containers op, één Apache server, de andere één die beschikt over `curl`
- probeer de Apache aan te spreken via naam
- dit werkt niet: containers zijn standaard geïsoleerd van elkaar
- via IP-adres werkt het wel: zitten op een impliciet netwerk met beperkte mogelijkheden
---
Demonstratie: Express applicatie uitbreiden

note:
- "met manuele MySQL"
---
- `docker network create NETWERKNAAM`
- `docker network rm NETWERKNAAM`
- `docker network ls`
- `docker run --network NETWERKNAAM ...`
- `docker network connect NETWERKNAAM CONTAINERNAAM`


---

### DNS-resolutie in Docker

note:
- namen van containers als hostnamen gebruiken (intern DNS-systeem)
- dit werkt alleen op expliciet aangemaakte netwerken, niet op het automatisch aangemaakte `bridge` netwerk!
---
Opdracht: uitbreiden met Mailhog

note:
- download de code voor het guest book met Mailhog
- configureer de containers zodat de volledige applicatie werkt
