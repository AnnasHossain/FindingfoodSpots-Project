# FindingFood-Spots-Projekt

Full-Stack Webprojekt mit allen CRUD-Operatoren bestehend aus einem **Vue-Frontend**, einem **Spring Boot Backend** und einer **PostgreSQL-Datenbank**.


**Note:** Manchmal geht mein Backend - Server in den Sleep Modus, weshalb es dann nötig ist den Browser zu wechseln oder 5 min zu warten (Ein guter Hinweis ist wenn folgende rote Rückmeldung direkt unter dem Login Button erscheint nachdem darauf geklickt wurde: "The user does not exist. Please register." dann ist sicher dass das Backend aus dem sleep modus raus ist und es kann mit dem user "Ralf" eingeloggt werden).

Der Login User lautet: Ralf

---

## 🚀 Projekt lokal einrichten


### 📋 Voraussetzungen

- **Node.js** (v18+)
- **Java 17** (z. B. Temurin JDK)
- **PostgreSQL** 
- **Git**
- **Docker** für Container-basiertes Backend + Datenbank Start

### 1. Projekt klonen
```bash
# Frontend
git clone https://github.com/AnnasHossain/FindingfoodSpots-Project.git

# Backend
git clone https://github.com/AnnasHossain/spring-demo1.git

```
### 2. Frontend (Vue.js) Installation
```bash
npm install
```
```bash
# Frontend starten
npm run serve
```

### 3. Backend (Spring Boot) Intallation und Start (Docker)
```bash
./gradlew build
docker-compose up --build
```
```bash
# Container stoppen
docker-compose down
```
## 📌 Wichtige API-Endpunkte

| Methode | URL               | Beschreibung             |
|---------|-------------------|--------------------------|
| GET     | `/Foodspots`      | Alle Foodspots anzeigen  |
| POST    | `/Foodspots`      | Foodspot erstellen       |
| PUT     | `/Foodspots/{id}` | Foodspot aktualisieren   |
| DELETE  | `/Foodspots/{id}` | Foodspot löschen         |
| GET     | `/Nutzers`        | Alle Nutzer anzeigen     |
| POST    | `/Nutzers`        | Nutzer erstellen         |

---

## 👤 Test-Nutzer

Ein initialer Nutzer ist bereits vordefiniert:
- **Name:** `Ralf`

Mit diesem Benutzer kannst du dich direkt einloggen.

---

## 🧭 UI-Hinweise

- **Neuen Datensatz hinzufügen (nach login):** Über den kleinen **blauen Button unten rechts**.
- **Bearbeiten/Löschen:** Einfach auf eine Spalte klicken – es erscheinen dann entsprechende Optionen.


## Troubleshooting und wichtige Hinweise

- Da sämtliche beanspruchte Dienste kostenlos sind, kann es zu Verzögerungen kommen.
- Render hat bspw. einen Sleep Modus für das Backend Deployment weshalb es beim ersten mal vielleicht nicht auf Anhieb klappt und es ein paar Aktualisierungen und das leeren des Browser caches bedarf
