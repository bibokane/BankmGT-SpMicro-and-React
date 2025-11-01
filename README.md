# BankmGT - Banking Management System

<div align="center">

![Java](https://img.shields.io/badge/Java-17-orange)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-2.7.12-brightgreen)
![Spring Cloud](https://img.shields.io/badge/Spring%20Cloud-2021.0.2-blue)
![React](https://img.shields.io/badge/React-18.2.0-61dafb)
![MySQL](https://img.shields.io/badge/MySQL-8.0-4479A1)

**Moderne Microservices-Architektur für Banking-Management**

[Architektur](#-architektur) • [Features](#-features) • [Installation](#-installation) • [Technologie-Stack](#-technologie-stack)

</div>

---

## 📖 Über das Projekt

**BankmGT** ist ein vollständiges Banking Management System, entwickelt mit modernen Software-Architektur-Patterns. Das Projekt demonstriert eine professionelle Microservices-Architektur mit Spring Boot Backend-Services und einer React-basierten Frontend-Anwendung.

### Projektziel

Dieses Projekt wurde entwickelt, um folgende moderne Software-Engineering-Konzepte zu demonstrieren:

- **Microservices-Architektur** - Modularer Aufbau mit unabhängigen Services
- **Service Discovery** - Automatische Service-Registrierung und -Ermittlung
- **API Gateway Pattern** - Zentralisierter Einstiegspunkt für alle Client-Anfragen
- **JWT-basierte Sicherheit** - Token-basierte Authentifizierung und Autorisierung
- **RESTful API Design** - Standardisierte, ressourcenorientierte APIs
- **React SPA** - Moderne Single Page Application mit Component-basiertem Design
- **Clean Architecture** - Klare Trennung von Verantwortlichkeiten (Controller, Service, Repository)

---

## 🏗️ Systemarchitektur

Das System implementiert eine vollständige Microservices-Architektur mit Service Discovery und API Gateway:

```
                    ┌─────────────────────────────┐
                    │   React Frontend (3000)     │
                    │   Material-UI Components    │
                    └────────────┬────────────────┘
                                 │
                    ┌────────────▼────────────┐
                    │   API Gateway (9999)    │
                    │   Spring Cloud Gateway  │
                    │   • Routing             │
                    │   • CORS Handling       │
                    │   • Load Balancing       │
                    └────────────┬────────────┘
                                 │
        ┌────────────────────────┼────────────────────────┐
        │                        │                        │
  ┌─────▼─────┐         ┌─────────▼──────────┐    ┌──────▼──────┐
  │  Eureka   │         │  Microservices     │    │    MySQL    │
  │  (8761)   │         │  (8081-8086)       │    │   (3306)   │
  │ Discovery │         │  • Login           │    │  Database   │
  │  Server   │         │  • Transaction     │    │             │
  └───────────┘         │  • Loan            │    └─────────────┘
                        │  • Locker          │
                        │  • Credit Card     │
                        │  • Gift Card       │
                        └─────────────────────┘
```

### Architekturkomponenten

#### 1. **Eureka Server (Port 8761)**
   - Service Discovery und Registry
   - Zentrale Verwaltung aller Microservice-Instanzen
   - Health Monitoring und Service-Statusüberwachung
   - Web-basiertes Dashboard zur Service-Übersicht

#### 2. **API Gateway (Port 9999)**
   - Einheitlicher Einstiegspunkt für alle Client-Anfragen
   - Intelligentes Routing zu den entsprechenden Microservices
   - CORS-Konfiguration für Frontend-Integration
   - Load Balancing zwischen Service-Instanzen

#### 3. **Microservices**

   **Login Service (Port 8081)**
   - Benutzerauthentifizierung mit JWT-Token-Generierung
   - Benutzerverwaltung (Kunden, Mitarbeiter, Administratoren)
   - Rollenbasierte Zugriffskontrolle (RBAC)
   - Account-Registrierung und -Verwaltung
   - Passwort-Reset-Funktionalität mit OTP-Verifizierung
   - Sicherheitsmaßnahmen (Login-Versuch-Tracking, Account-Blocking)

   **Transaction Service (Port 8082)**
   - Transaktionsverwaltung (Einzahlung, Abhebung, Überweisung)
   - Transaktionshistorie mit Filterfunktionen
   - PDF-Export für Transaktionsberichte
   - Datum-basierte Transaktionssuche
   - Konto-Saldo-Verwaltung

   **Loan Service (Port 8083)**
   - Darlehensantrags-Management
   - Automatische EMI-Berechnung
   - Darlehensrückzahlungsverwaltung
   - Darlehensstatus-Verwaltung (Pending, Active, Closed)
   - Darlehenstypen-Unterstützung

   **Locker Service (Port 8084)**
   - Schließfachantragsverwaltung
   - Flexible Preisberechnung basierend auf Typ und Größe
   - Schließfachgebührenverwaltung
   - Schließfachstatus-Tracking
   - Schließfach-Schließungsanträge

   **Credit Card Service (Port 8085)**
   - Kreditkartenantrags-Management
   - Kreditkartenzahlungen und EMI-Verwaltung
   - EMI-Rechner für Zinsberechnungen
   - Kreditlimit-Management
   - Kreditkartenstatus-Verwaltung

   **Gift Card Service (Port 8086)**
   - Geschenkkarten-Kauf und -Verwaltung
   - Empfänger-Verwaltung
   - Geschenkkarten-Historie

#### 4. **Frontend (Port 3000)**
   - Moderne React Single Page Application
   - Material-UI und Bootstrap für responsives Design
   - JWT-Token-basierte Authentifizierung
   - Protected Routes mit React Router
   - Formularvalidierung mit Formik und Yup
   - Toast-Benachrichtigungen für User Feedback
   - Responsive Design für Mobile und Desktop

---

## 💻 Technologie-Stack

### Backend Technologies

| Technologie | Version | Verwendung |
|------------|---------|------------|
| **Java** | 17 | Programmiersprache |
| **Spring Boot** | 2.7.12 | Framework für Microservices |
| **Spring Cloud** | 2021.0.2 | Cloud-native Features |
| **Spring Cloud Gateway** | - | API Gateway Implementation |
| **Netflix Eureka** | - | Service Discovery |
| **Spring Security** | - | Authentifizierung & Autorisierung |
| **Spring Data JPA** | - | Datenbankzugriff |
| **Hibernate** | 5.6.15 | ORM Framework |
| **JWT (JJWT)** | 0.9.1 | Token-basierte Authentifizierung |
| **MySQL Connector/J** | - | Datenbanktreiber |
| **Maven** | - | Build-Automatisierung |

### Frontend Technologies

| Technologie | Version | Verwendung |
|------------|---------|------------|
| **React** | 18.2.0 | UI Framework |
| **React Router DOM** | 6.12.1 | Client-seitiges Routing |
| **Axios** | 1.4.0 | HTTP Client für API-Kommunikation |
| **Material-UI (MUI)** | 5.13.5 | Komponentenbibliothek |
| **Bootstrap** | 5.3.0 | CSS Framework |
| **React Bootstrap** | 2.7.4 | Bootstrap React Components |
| **Formik** | 2.4.1 | Formularverwaltung |
| **Yup** | 1.2.0 | Schema-Validierung |
| **React Toastify** | 9.1.3 | Toast-Benachrichtigungen |
| **JWT Decode** | 3.1.2 | JWT-Token-Verarbeitung |

### Datenbank & Tools

- **MySQL 8.0+** - Relationale Datenbank
- **Maven Wrapper** - Konsistente Build-Umgebung
- **Spring DevTools** - Hot Reload für schnelle Entwicklung
- **Node.js & npm** - Frontend-Package-Management

---

## ✨ Hauptfeatures

### 🔐 Authentifizierung & Autorisierung

- **JWT-basierte Authentifizierung** - Sichere Token-basierte Session-Verwaltung
- **Rollenbasierte Zugriffskontrolle** - Separate Berechtigungen für Kunden, Mitarbeiter und Administratoren
- **Login-Versuch-Tracking** - Automatisches Account-Blocking nach fehlgeschlagenen Versuchen
- **Passwort-Reset** - OTP-basierte Passwort-Wiederherstellung per E-Mail
- **Protected Routes** - Frontend-Routen-Schutz basierend auf Benutzerrollen

### 💰 Transaktionsmanagement

- **Einzahlungen** - Einfache Geldeinzahlung auf Konten
- **Abhebungen** - Kontrollierte Geldabhebungen mit Saldo-Prüfung
- **Überweisungen** - Interne Banküberweisungen zwischen Konten
- **Transaktionshistorie** - Vollständige Historie mit Filteroptionen
- **PDF-Export** - Generierung von Transaktionsberichten im PDF-Format
- **Datum-Filterung** - Suche nach Transaktionen im Zeitraum

### 💳 Kreditkartenverwaltung

- **Kreditkartenanträge** - Einfache Antragstellung für neue Kreditkarten
- **Zahlungsmanagement** - Einzahlungen auf Kreditkartenkonten
- **EMI-Verwaltung** - Verwaltung und Zahlung von Equated Monthly Installments
- **EMI-Rechner** - Automatische Berechnung von monatlichen Raten
- **Kreditlimit-Tracking** - Überwachung von Verfügungsrahmen
- **Kreditkartenstatus** - Verwaltung von Pending, Active und Closed-Status

### 🏦 Darlehensverwaltung

- **Darlehensanträge** - Umfassendes Antragsmanagement
- **Automatische EMI-Berechnung** - Zinsberechnung basierend auf Darlehenstyp
- **Rückzahlungsverwaltung** - Tracking von Darlehensrückzahlungen
- **Darlehenstypen** - Unterstützung verschiedener Darlehensarten
- **Status-Management** - Workflow für Pending → Active → Closed

### 🔒 Schließfachverwaltung

- **Schließfachanträge** - Flexible Antragsstellung mit Typ- und Größenauswahl
- **Dynamische Preisberechnung** - Automatische Gebührenberechnung
- **Schließfachgebühren** - Verwaltung von monatlichen/jährlichen Gebühren
- **Schließfachstatus** - Statusverfolgung (Pending, Active, Closed)
- **Schließungsanträge** - Verwaltung von Schließfach-Schließungsanträgen

### 🎁 Geschenkkartenverwaltung

- **Geschenkkartenkauf** - Einfacher Kaufprozess
- **Empfänger-Verwaltung** - Verwaltung von Empfängerinformationen
- **Geschenkkarten-Historie** - Übersicht aller gekauften Geschenkkarten

### 👥 Benutzerverwaltung

#### Kundenfunktionen
- **Selbstregistrierung** - Benutzerfreundliche Registrierung
- **Profilverwaltung** - Vollständige Verwaltung eigener Profildaten
- **Kontoverwaltung** - Anzeige und Verwaltung von Kontoinformationen

#### Mitarbeiterfunktionen
- **Dashboard** - Übersichtliche Verwaltungsoberfläche
- **Kontoverwaltung** - Aktivierung von Pending-Konten
- **Antragsverwaltung** - Verwaltung aller Anträge (Darlehen, Kreditkarten, Schließfächer)
- **Transaktionsüberwachung** - Systemweite Transaktionsübersicht
- **Kundenliste** - Übersicht aller registrierten Kunden

#### Administratorfunktionen
- **Benutzerverwaltung** - Vollständige Verwaltung von Kunden und Mitarbeitern
- **Systemüberwachung** - Systemweite Verwaltung und Monitoring
- **Mitarbeiterregistrierung** - Erstellung neuer Mitarbeiterkonten

### 🎨 Frontend-Features

- **Responsive Design** - Optimiert für Desktop, Tablet und Mobile
- **Moderne UI/UX** - Material-UI und Bootstrap für professionelles Design
- **Formularvalidierung** - Client-seitige Validierung mit Yup
- **Toast-Benachrichtigungen** - Benutzerfreundliche Feedback-Nachrichten
- **Protected Routes** - Automatische Weiterleitung bei fehlender Authentifizierung
- **Component-basiert** - Wiederverwendbare React-Komponenten
- **State Management** - Effiziente State-Verwaltung mit React Hooks

### 🏛️ Architektur-Features

- **Microservices-Prinzip** - Unabhängige, skalierbare Services
- **Service Discovery** - Automatische Service-Registrierung mit Eureka
- **API Gateway** - Zentralisierter Routing und CORS-Handling
- **Separation of Concerns** - Klare Trennung: Controller → Service → Repository
- **Dependency Injection** - Spring Framework DI für lose Kopplung
- **RESTful API Design** - Standardisierte HTTP-Methoden und Ressourcen-Strukturen
- **Hot Reload** - Schnelle Entwicklung mit Spring DevTools und React HMR

---

## 🚀 Schnellstart

### Voraussetzungen

Stellen Sie sicher, dass folgende Software installiert ist:

- **Java JDK 17+**
- **Maven 3.6+** (oder Maven Wrapper)
- **Node.js 16+** und **npm 8+**
- **MySQL 8.0+** Server
- **Git** (optional)

### Installation

#### 1. Repository klonen

```bash
git clone https://github.com/bibokane/BankmGT-SpMicro-and-React.git
cd "BankmGT SpMicro and React"
```

#### 2. Datenbank einrichten

```sql
-- Datenbank erstellen
CREATE DATABASE IF NOT EXISTS onlinebankingportal;

-- Schema importieren
mysql -u root -p onlinebankingportal < Database/bankMgt.sql
```

#### 3. Datenbankkonfiguration anpassen

Bearbeiten Sie die `application.properties` Dateien in jedem Service:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/onlinebankingportal?useLegacyDatetimeCode=false&serverTimezone=GMT
spring.datasource.username=IhrBenutzername
spring.datasource.password=IhrPasswort
```

#### 4. Frontend-Dependencies installieren

```bash
cd Frontend
npm install
```

---

## 🏃 Services starten

**Wichtig**: Starten Sie die Services in der angegebenen Reihenfolge!

### Schritt 1: Eureka Server

```bash
cd "Backend/Eureka"
./mvnw.cmd spring-boot:run
```

Warten Sie bis zur vollständigen Initialisierung.  
**Eureka Dashboard**: http://localhost:8761

### Schritt 2: Microservices

Öffnen Sie separate Terminal-Fenster für jeden Service:

```bash
# Terminal 1: Login Service
cd "Backend/Login_Service"
./mvnw.cmd spring-boot:run

# Terminal 2: Transaction Service
cd "Backend/Transaction_Service"
./mvnw.cmd spring-boot:run

# Terminal 3: Loan Service
cd "Backend/Loan_Service"
./mvnw.cmd spring-boot:run

# Terminal 4: Locker Service
cd "Backend/Locker_Service"
./mvnw.cmd spring-boot:run

# Terminal 5: Credit Card Service
cd "Backend/Credit_Card_Service"
./mvnw.cmd spring-boot:run

# Terminal 6: Gift Card Service
cd "Backend/Gift_Card_Service"
./mvnw.cmd spring-boot:run
```

### Schritt 3: API Gateway

```bash
cd "Backend/ApiGateway"
./mvnw.cmd spring-boot:run
```

### Schritt 4: Frontend

```bash
cd Frontend
npm start
```

Die Anwendung öffnet sich automatisch unter **http://localhost:3000**

---

## 🔌 Service-Endpunkte

| Service | Port | Zugriff | Beschreibung |
|---------|------|---------|--------------|
| **Eureka Server** | 8761 | http://localhost:8761 | Service Discovery Dashboard |
| **Login Service** | 8081 | http://localhost:8081 | Authentifizierung & Benutzerverwaltung |
| **Transaction Service** | 8082 | http://localhost:8082 | Transaktionsmanagement |
| **Loan Service** | 8083 | http://localhost:8083 | Darlehensverwaltung |
| **Locker Service** | 8084 | http://localhost:8084 | Schließfachverwaltung |
| **Credit Card Service** | 8085 | http://localhost:8085 | Kreditkartenmanagement |
| **Gift Card Service** | 8086 | http://localhost:8086 | Geschenkkartenverwaltung |
| **API Gateway** | 9999 | http://localhost:9999 | Zentraler API-Einstiegspunkt |
| **React Frontend** | 3000 | http://localhost:3000 | Web-Anwendung |

---

## 📁 Projektstruktur

```
BankmGT-SpMicro-and-React/
│
├── Backend/                              # Spring Boot Microservices
│   │
│   ├── Eureka/                          # Service Discovery Server
│   │   ├── src/main/java/com/eureka/
│   │   └── src/main/resources/
│   │       └── application.properties
│   │
│   ├── Login_Service/                   # Authentifizierungs-Service
│   │   ├── src/main/java/com/axis/
│   │   │   ├── controller/             # REST Controllers
│   │   │   ├── service/                 # Business Logic
│   │   │   ├── repository/             # Data Access Layer
│   │   │   ├── entity/                  # JPA Entities
│   │   │   ├── config/                  # Security Configuration
│   │   │   ├── filter/                  # JWT Filter
│   │   │   └── util/                    # JWT Utilities
│   │   └── src/main/resources/
│   │       └── application.properties
│   │
│   ├── Transaction_Service/            # Transaktions-Service
│   ├── Loan_Service/                    # Darlehens-Service
│   ├── Locker_Service/                 # Schließfach-Service
│   ├── Credit_Card_Service/           # Kreditkarten-Service
│   ├── Gift_Card_Service/              # Geschenkkarten-Service
│   │
│   └── ApiGateway/                      # API Gateway
│       ├── src/main/java/com/axis/
│       └── src/main/resources/
│           └── application.yml         # Routing-Konfiguration
│
├── Frontend/                            # React-Anwendung
│   ├── public/                          # Statische Assets
│   ├── src/
│   │   ├── Components/                  # React-Komponenten
│   │   │   ├── AdminDashboard.jsx
│   │   │   ├── CustomerDashboard.jsx
│   │   │   ├── EmployeeDashboard.jsx
│   │   │   ├── Deposit.jsx
│   │   │   ├── Withdraw.jsx
│   │   │   ├── BankTransfer.jsx
│   │   │   └── ...                     # Weitere Komponenten
│   │   ├── pages/                       # Seiten-Komponenten
│   │   ├── utility/                     # Utilities
│   │   │   ├── auth.js                  # Authentication Context
│   │   │   └── RequireAuth.js           # Route Protection
│   │   ├── styles/                      # CSS-Dateien
│   │   ├── assets/                      # Bilder und Medien
│   │   ├── App.js                       # Haupt-App-Komponente
│   │   └── index.js                     # Entry Point
│   ├── package.json
│   └── package-lock.json
│
└── Database/                             # Datenbank-Skripte
    └── bankMgt.sql                      # MySQL-Datenbankschema
```

---

## 📡 API-Dokumentation

### API Gateway Endpoints

Alle API-Anfragen werden über das API Gateway (Port 9999) geroutet:

#### Authentifizierung

```http
POST http://localhost:9999/login/customer/authenticate
Content-Type: application/json

{
  "username": "customer",
  "password": "password"
}
```

**Response:**
```json
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
}
```

#### Transaktionen

```http
GET http://localhost:9999/transaction/customer/show-all-my-transactions
Authorization: Bearer <jwt-token>

POST http://localhost:9999/transaction/customer/deposit
Authorization: Bearer <jwt-token>
Content-Type: application/json

{
  "amount": 1000.00,
  "description": "Einzahlung"
}
```

#### Darlehen

```http
GET http://localhost:9999/loan/customer/my-loans
Authorization: Bearer <jwt-token>

POST http://localhost:9999/loan/customer/apply-loan
Authorization: Bearer <jwt-token>
Content-Type: application/json

{
  "loantype": "Personal Loan",
  "loanamount": 50000,
  "duration": 12
}
```

#### Kreditkarten

```http
GET http://localhost:9999/creditcard/customer/my-credit-cards
Authorization: Bearer <jwt-token>

POST http://localhost:9999/creditcard/customer/apply-credit-card
Authorization: Bearer <jwt-token>
Content-Type: application/json

{
  "creditcardname": "Platinum Card",
  "creditcardlimit": 100000
}
```

---

## 🗄️ Datenbank-Schema

Das System verwendet eine **MySQL 8.0+** Datenbank mit dem Namen `onlinebankingportal`.

### Kern-Tabellen

| Tabelle | Beschreibung |
|---------|--------------|
| `users` | Benutzerinformationen (Kunden, Mitarbeiter, Administratoren) |
| `account` | Bankkonten mit Saldo und Status |
| `transaction` | Vollständige Transaktionshistorie |
| `loan` | Darlehensinformationen mit EMI-Details |
| `locker` | Schließfachverwaltung mit Status |
| `creditcard` | Kreditkartendetails mit Limits |
| `giftcard` | Geschenkkarteninformationen |

### Datenbank-Import

```bash
# MySQL Command Line
mysql -u root -p onlinebankingportal < Database/bankMgt.sql

# Oder MySQL Workbench: Datei → SQL-Skript ausführen
```

---

## 🛠️ Entwicklung

### Backend-Entwicklung

```bash
# Projekt kompilieren
mvn clean install

# Tests ausführen
mvn test

# Service neu starten
cd Backend/[Service-Name]
./mvnw.cmd spring-boot:run
```

### Frontend-Entwicklung

```bash
cd Frontend

# Development Server (mit Hot Reload)
npm start

# Production Build
npm run build

# Tests
npm test
```

### Development Features

- **Spring Boot DevTools** - Automatisches Neuladen bei Backend-Änderungen
- **React Hot Module Replacement** - Sofortige Frontend-Updates ohne Page Reload
- **Maven Wrapper** - Konsistente Maven-Versionen ohne Installation

---

## 🏆 Technische Highlights

### Architektur-Patterns

✅ **Microservices-Architektur** - Jeder Service ist unabhängig deploybar und skalierbar  
✅ **Service Discovery** - Automatische Service-Registrierung und -Ermittlung mit Eureka  
✅ **API Gateway Pattern** - Zentrale Routing-Logik und Request-Handling  
✅ **Layered Architecture** - Klare Trennung: Controller → Service → Repository  
✅ **Dependency Injection** - Spring Framework für lose Kopplung und Testbarkeit  
✅ **RESTful Design** - Standardisierte HTTP-Methoden und URL-Strukturen  

### Sicherheitsfeatures

✅ **JWT-Authentifizierung** - Token-basierte, stateless Authentifizierung  
✅ **Spring Security** - Umfassende Sicherheitskonfiguration  
✅ **Rollenbasierte Autorisierung** - Separate Berechtigungen für verschiedene Rollen  
✅ **CORS-Konfiguration** - Sichere Cross-Origin-Anfragen  
✅ **Protected Endpoints** - JWT-Filter für geschützte Ressourcen  

### Code-Qualität

✅ **Konsistente Struktur** - Einheitliche Package-Organisation in allen Services  
✅ **Logging Framework** - SLF4J Logger für strukturierte Log-Ausgaben  
✅ **Exception Handling** - Konsistente Fehlerbehandlung über alle Services  
✅ **Component Reusability** - Wiederverwendbare React-Komponenten  
✅ **Form Validation** - Client- und Server-seitige Validierung  

### Frontend-Exzellenz

✅ **Material Design** - Professionelles UI mit Material-UI Komponenten  
✅ **Responsive Layout** - Optimiert für alle Bildschirmgrößen  
✅ **State Management** - Effiziente State-Verwaltung mit React Hooks  
✅ **Route Protection** - Automatische Authentifizierungsprüfung  
✅ **User Feedback** - Toast-Benachrichtigungen für bessere UX  

---

## 📊 Projektstatistiken

- **Microservices**: 7 Services
- **Backend-Code**: 50.000+ Zeilen Java
- **Frontend-Komponenten**: 60+ React-Komponenten
- **API-Endpoints**: 50+ REST-Endpunkte
- **Datenbank-Tabellen**: 7 Haupttabellen
- **Technologie-Stack**: 20+ moderne Technologien

---

## 🔐 Sicherheitsaspekte

- **JWT Token** - Sichere Token-Generierung und -Validierung
- **Password Hashing** - Passwortverschlüsselung (vorbereitet)
- **Account Protection** - Automatisches Blocking bei verdächtigen Aktivitäten
- **Session Management** - Token-basierte Session-Verwaltung
- **CORS Protection** - Konfigurierte Cross-Origin-Anfragen
- **Role-based Access** - Granulare Berechtigungsverwaltung

---

## 📝 Hinweis

Dieses Projekt wurde als Lern- und Studienbasis erworben und anschließend erweitert, lokal ausgeführt und dokumentiert, um Microservices-Architekturen besser zu verstehen.

---

## 📞 Kontakt

- **Repository**: https://github.com/bibokane/BankmGT-SpMicro-and-React
- **Projekt-Typ**: Lernprojekt / Educational Project

---

<div align="center">

**Entwickelt mit ❤️ für Lernzwecke**

*Letzte Aktualisierung: Oktober 2025*

</div>
