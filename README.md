# FindingFood-Spots-Projekt

Vollständiges Webprojekt bestehend aus einem **Vue-Frontend**, einem **Spring Boot Backend** und einer lokalen **PostgreSQL-Datenbank**.

---

## 📋 Voraussetzungen

- **Node.js** (v18+)
- **Java 17** (z. B. Temurin JDK)
- **PostgreSQL** lokal oder Docker
- **Git**
- Optional: **Docker** für Container-basiertes Setup

---

## 🚀 Projekt lokal einrichten

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



