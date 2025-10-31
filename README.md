# BankmGT - Banking Management System (Microservices & React)

<div align="center">

![Java](https://img.shields.io/badge/Java-17-orange)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-2.7.12-brightgreen)
![React](https://img.shields.io/badge/React-18.2.0-blue)
![MySQL](https://img.shields.io/badge/MySQL-8.0-blue)
![License](https://img.shields.io/badge/License-Private-red)

**Ein privates Lernprojekt zur Demonstration moderner Microservices-Architektur mit Spring Boot und React**

</div>

---

## 📋 Inhaltsverzeichnis

- [Projektübersicht](#-projektübersicht)
- [Architektur](#-architektur)
- [Technologie-Stack](#-technologie-stack)
- [Voraussetzungen](#-voraussetzungen)
- [Installation](#-installation)
- [Projektstart](#-projektstart)
- [Service-Ports](#-service-ports)
- [Projektstruktur](#-projektstruktur)
- [Features](#-features)
- [API-Dokumentation](#-api-dokumentation)
- [Datenbank](#-datenbank)
- [Entwicklung](#-entwicklung)
- [Lizenz & Hinweis](#-lizenz--hinweis)

---

## 📖 Projektübersicht

**BankmGT** ist eine umfassende Banking Management System-Anwendung, die als privates Lernprojekt entwickelt wurde, um moderne Software-Architektur-Patterns und Technologien zu demonstrieren. Das Projekt implementiert eine Microservices-Architektur mit Spring Boot im Backend und eine moderne React-basierte Single Page Application (SPA) im Frontend.

### Zielsetzung

Dieses Projekt dient ausschließlich **Lern- und Bildungszwecken** und veranschaulicht:

- Microservices-Architektur mit Service Discovery
- API Gateway Pattern
- JWT-basierte Authentifizierung und Autorisierung
- Reactive Frontend-Entwicklung mit React
- RESTful API Design
- Datenbank-Integration mit MySQL
- Spring Security für sichere Endpunkte

---

## 🏗️ Architektur

Das System folgt einer **Microservices-Architektur** mit den folgenden Komponenten:

```
┌─────────────────────────────────────────────────────────────┐
│                      React Frontend (3000)                   │
└────────────────────────────┬──────────────────────────────────┘
                             │
                    ┌────────▼────────┐
                    │  API Gateway    │
                    │    (9999)       │
                    └────────┬─────────┘
                             │
        ┌─────────────────────┼─────────────────────┐
        │                     │                     │
  ┌─────▼─────┐      ┌────────▼────────┐    ┌─────▼─────┐
  │  Eureka   │      │  Microservices  │    │   MySQL   │
  │  (8761)   │      │  (8081-8086)    │    │  (3306)   │
  └───────────┘      └─────────────────┘    └───────────┘
```

### Microservices-Übersicht

1. **Eureka Server** - Service Discovery & Registry
2. **Login Service** - Authentifizierung und Benutzerverwaltung
3. **Transaction Service** - Transaktionsmanagement
4. **Loan Service** - Darlehensverwaltung
5. **Locker Service** - Schließfachverwaltung
6. **Credit Card Service** - Kreditkartenmanagement
7. **Gift Card Service** - Geschenkkartenverwaltung
8. **API Gateway** - Zentraler Einstiegspunkt für alle Client-Anfragen

---

## 💻 Technologie-Stack

### Backend

- **Java** 17
- **Spring Boot** 2.7.12
- **Spring Cloud** 2021.0.2
  - Spring Cloud Gateway (API Gateway)
  - Netflix Eureka (Service Discovery)
- **Spring Security** - Authentifizierung & Autorisierung
- **Spring Data JPA** - Datenbank-Zugriff
- **Hibernate** - ORM Framework
- **MySQL Connector/J** - Datenbanktreiber
- **JWT (JSON Web Tokens)** - Token-basierte Authentifizierung
- **Maven** - Build-Tool und Dependency Management

### Frontend

- **React** 18.2.0
- **React Router DOM** 6.12.1 - Routing
- **Axios** 1.4.0 - HTTP Client
- **Bootstrap** 5.3.0 - UI Framework
- **Material-UI (MUI)** 5.13.5 - Komponentenbibliothek
- **React Bootstrap** 2.7.4 - Bootstrap-Integration
- **Formik** 2.4.1 - Formularverwaltung
- **Yup** 1.0.0 - Validierung
- **React Toastify** 9.1.3 - Benachrichtigungen
- **JWT Decode** 3.1.2 - JWT-Verarbeitung

### Datenbank

- **MySQL** 8.0+ - Relationale Datenbank

### Development Tools

- **Maven Wrapper** - Konsistente Maven-Versionen
- **Spring DevTools** - Hot Reload für Entwicklung
- **Node.js & npm** - Frontend-Package-Management

---

## ✅ Voraussetzungen

Bevor Sie das Projekt starten, stellen Sie sicher, dass folgende Software installiert ist:

- **Java JDK** 17 oder höher
- **Maven** 3.6+ (oder Maven Wrapper)
- **Node.js** 16+ und **npm** 8+
- **MySQL** 8.0+ Server
- **Git** (optional, für Versionskontrolle)
- Ein moderner Webbrowser (Chrome, Firefox, Edge)

### Systemanforderungen

- **Betriebssystem**: Windows, Linux oder macOS
- **RAM**: Mindestens 8GB empfohlen
- **Festplatte**: Mindestens 2GB freier Speicherplatz

---

## 🚀 Installation

### 1. Repository klonen oder herunterladen

```bash
git clone <repository-url>
cd "BankmGT SpMicro and React"
```

### 2. MySQL-Datenbank einrichten

1. Starten Sie Ihren MySQL-Server
2. Erstellen Sie eine neue Datenbank:

```sql
CREATE DATABASE IF NOT EXISTS onlinebankingportal;
```

3. Importieren Sie das Datenbankschema:

```bash
mysql -u root -p onlinebankingportal < Database/bankMgt.sql
```

Oder führen Sie die SQL-Datei direkt in MySQL Workbench aus.

### 3. Datenbankkonfiguration anpassen

Passen Sie in den `application.properties`-Dateien aller Microservices die Datenbankverbindung an:

**Pfad**: `Backend/[Service-Name]/src/main/resources/application.properties`

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/onlinebankingportal?useLegacyDatetimeCode=false&serverTimezone=GMT
spring.datasource.username=IhrBenutzername
spring.datasource.password=IhrPasswort
```

### 4. Frontend-Dependencies installieren

```bash
cd Frontend
npm install
```

---

## 🏃 Projektstart

**Wichtig**: Die Services müssen in der richtigen Reihenfolge gestartet werden!

### Schritt 1: Eureka Server starten

```bash
cd "Backend/Eureka"
./mvnw.cmd spring-boot:run
# Oder auf Linux/Mac:
./mvnw spring-boot:run
```

Warten Sie, bis Eureka vollständig gestartet ist (ca. 30-60 Sekunden).  
**Eureka Dashboard**: http://localhost:8761

### Schritt 2: Microservices starten

Öffnen Sie separate Terminal-Fenster/Tabs und starten Sie jeden Service:

```bash
# Login Service
cd "Backend/Login_Service"
./mvnw.cmd spring-boot:run

# Transaction Service
cd "Backend/Transaction_Service"
./mvnw.cmd spring-boot:run

# Loan Service
cd "Backend/Loan_Service"
./mvnw.cmd spring-boot:run
# Falls der Maven Wrapper fehlt (.mvn Ordner fehlt):
# - Kopieren Sie den .mvn Ordner von einem anderen Service (z.B. Eureka)
# - Oder verwenden Sie: mvn spring-boot:run (falls Maven installiert ist)

# Locker Service
cd "Backend/Locker_Service"
./mvnw.cmd spring-boot:run

# Credit Card Service
cd "Backend/Credit_Card_Service"
./mvnw.cmd spring-boot:run

# Gift Card Service
cd "Backend/Gift_Card_Service"
./mvnw.cmd spring-boot:run
```

**Wichtiger Hinweis für Loan_Service**: Falls beim Start des Loan Service ein Fehler auftritt (`maven-wrapper.properties kann nicht gefunden werden`), kopieren Sie den `.mvn`-Ordner von einem anderen Service (z.B. Eureka) in den Loan_Service Ordner, oder verwenden Sie `mvn spring-boot:run` direkt (falls Maven installiert ist).

### Schritt 3: API Gateway starten

```bash
cd "Backend/ApiGateway"
./mvnw.cmd spring-boot:run
```

### Schritt 4: Frontend starten

```bash
cd Frontend
npm start
```

Das Frontend wird automatisch im Browser unter **http://localhost:3000** geöffnet.

---

## 🔌 Service-Ports

| Service | Port | URL | Beschreibung |
|---------|------|-----|--------------|
| Eureka Server | 8761 | http://localhost:8761 | Service Discovery Dashboard |
| Login Service | 8081 | http://localhost:8081 | Authentifizierung |
| Transaction Service | 8082 | http://localhost:8082 | Transaktionen |
| Loan Service | 8083 | http://localhost:8083 | Darlehen |
| Locker Service | 8084 | http://localhost:8084 | Schließfächer |
| Credit Card Service | 8085 | http://localhost:8085 | Kreditkarten |
| Gift Card Service | 8086 | http://localhost:8086 | Geschenkkarten |
| API Gateway | 9999 | http://localhost:9999 | Zentraler API-Einstiegspunkt |
| React Frontend | 3000 | http://localhost:3000 | Web-Anwendung |

---

## 📁 Projektstruktur

```
BankmGT SpMicro and React/
│
├── Backend/                          # Spring Boot Microservices
│   ├── Eureka/                      # Service Discovery Server
│   │   ├── src/main/java/
│   │   └── src/main/resources/
│   │
│   ├── Login_Service/               # Authentifizierungs-Service
│   ├── Transaction_Service/          # Transaktions-Service
│   ├── Loan_Service/                 # Darlehens-Service
│   ├── Locker_Service/              # Schließfach-Service
│   ├── Credit_Card_Service/         # Kreditkarten-Service
│   ├── Gift_Card_Service/           # Geschenkkarten-Service
│   │
│   └── ApiGateway/                  # API Gateway
│       ├── src/main/java/
│       └── src/main/resources/
│           └── application.yml      # Gateway-Routing-Konfiguration
│
├── Frontend/                        # React-Anwendung
│   ├── public/                      # Öffentliche Assets
│   ├── src/
│   │   ├── Components/              # React-Komponenten
│   │   ├── pages/                   # Seiten-Komponenten
│   │   ├── utility/                 # Utilities (Auth, etc.)
│   │   ├── styles/                  # CSS-Dateien
│   │   ├── assets/                  # Bilder und Medien
│   │   ├── App.js                   # Haupt-App-Komponente
│   │   └── index.js                 # Entry Point
│   ├── package.json
│   └── package-lock.json
│
└── Database/                         # Datenbank-Skripte
    └── bankMgt.sql                  # MySQL-Datenbankschema
```

---

## ✨ Features

### Kundenfunktionen (Customer)

- ✅ **Registrierung und Login** - Sichere Benutzerauthentifizierung mit JWT
- ✅ **Profilverwaltung** - Eigene Profildaten anzeigen und bearbeiten
- ✅ **Kontoverwaltung** - Kontoinformationen anzeigen und verwalten
- ✅ **Transaktionen** 
  - Einzahlungen (Deposit)
  - Abhebungen (Withdraw)
  - Überweisungen (Bank Transfer)
  - Transaktionshistorie anzeigen
- ✅ **Darlehen (Loans)**
  - Darlehensanträge stellen
  - Alle eigenen Darlehen anzeigen
  - Darlehensrückzahlung (Loan Payment)
- ✅ **Kreditkarten (Credit Cards)**
  - Kreditkartenanträge stellen
  - Alle eigenen Kreditkarten anzeigen
  - Kreditkartenzahlungen (Make Payment)
  - EMI-Zahlungen (Pay EMI)
  - EMI-Rechner (EMI Calculator)
  - Kreditkarten schließen
- ✅ **Schließfächer (Locker)**
  - Schließfachanträge stellen
  - Eigene Schließfächer anzeigen
  - Schließfachgebühren bezahlen
  - Schließfach-Schließungsanträge stellen
- ✅ **Geschenkkarten (Gift Cards)**
  - Geschenkkarten kaufen
  - Alle gekauften Geschenkkarten anzeigen
- ✅ **Password Reset** - Passwort zurücksetzen bei Vergessen

### Mitarbeiterfunktionen (Employee)

- ✅ **Dashboard** - Übersichtliche Mitarbeiteroberfläche
- ✅ **Profilverwaltung** - Eigene Profildaten verwalten
- ✅ **Kundenverwaltung** - Kundenliste einsehen
- ✅ **Kontoverwaltung**
  - Alle Konten anzeigen
  - Pending Konten (Kontenanträge)
  - Konten aktivieren (Activate Account)
- ✅ **Transaktionsüberwachung** - Alle Transaktionen einsehen
- ✅ **Darlehensverwaltung (Loans)**
  - Pending Darlehensanträge anzeigen
  - Darlehen aktivieren (Activate Loans)
  - Darlehen schließen (Close Loans)
  - Alle Darlehen anzeigen
- ✅ **Schließfachverwaltung (Locker)**
  - Alle Schließfächer anzeigen
  - Pending Schließfachanträge (Pending Requests)
  - Schließfächer aktivieren
  - Schließfächer schließen
  - Schließfach-Schließungsanträge bearbeiten
- ✅ **Kreditkartenverwaltung (Credit Cards)**
  - Alle Kreditkarten anzeigen
  - Pending Kreditkartenanträge
  - Kreditkarten aktivieren
  - Kreditkarten schließen
  - Kreditkarten-Schließungsanträge bearbeiten
- ✅ **Password Reset** - Passwort zurücksetzen

### Administrationsfunktionen (Admin)

- ✅ **Dashboard** - Administrator-Dashboard
- ✅ **Profilverwaltung** - Admin-Profil verwalten
- ✅ **Benutzerverwaltung** - Kunden- und Mitarbeiterverwaltung
- ✅ **Systemüberwachung** - Systemweite Überwachung und Verwaltung

### Technische Features

- ✅ **Microservices-Architektur** - Modulare und skalierbare Struktur
- ✅ **Service Discovery** - Automatische Service-Registrierung mit Eureka
- ✅ **API Gateway** - Zentralisierte API-Verwaltung und Routing
- ✅ **JWT-Authentifizierung** - Sichere, token-basierte Authentifizierung
- ✅ **RESTful APIs** - Standardisierte API-Architektur
- ✅ **Responsive Design** - Mobile-freundliche Benutzeroberfläche
- ✅ **React Router** - Client-seitiges Routing

---

## 📡 API-Dokumentation

### API Gateway Endpoints

Alle API-Anfragen gehen über das API Gateway (Port 9999):

| Endpoint | Methode | Beschreibung | Service |
|----------|---------|--------------|---------|
| `/login/**` | POST | Benutzer-Login | Login Service |
| `/transaction/**` | GET, POST | Transaktionen verwalten | Transaction Service |
| `/loan/**` | GET, POST, PUT | Darlehen verwalten | Loan Service |
| `/locker/**` | GET, POST | Schließfächer verwalten | Locker Service |
| `/creditcard/**` | GET, POST | Kreditkarten verwalten | Credit Card Service |
| `/giftcard/**` | GET, POST | Geschenkkarten verwalten | Gift Card Service |

### Beispiel API-Aufruf

```javascript
// Login Request
POST http://localhost:9999/login/customer/authenticate
Content-Type: application/json

{
  "username": "customer",
  "password": "password"
}

// Response
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "username": "customer"
}
```

---

## 🗄️ Datenbank

Das System verwendet eine **MySQL 8.0+** Datenbank mit dem Namen `onlinebankingportal`.

### Haupttabellen

- `users` - Benutzerinformationen (Kunden, Mitarbeiter, Administratoren)
- `account` - Bankkonten
- `transaction` - Transaktionshistorie
- `loan` - Darlehensinformationen
- `locker` - Schließfachverwaltung
- `creditcard` - Kreditkartendetails
- `giftcard` - Geschenkkarteninformationen

### Datenbankimport

```bash
# Mit MySQL Command Line
mysql -u root -p onlinebankingportal < Database/bankMgt.sql

# Oder in MySQL Workbench:
# Datei → SQL-Skript ausführen → bankMgt.sql wählen
```

---

## 🛠️ Entwicklung

### Backend-Entwicklung

```bash
# Projekt kompilieren
mvn clean install

# Tests ausführen
mvn test

# Spezifischen Service neu starten
cd Backend/[Service-Name]
./mvnw.cmd spring-boot:run
```

### Frontend-Entwicklung

```bash
cd Frontend

# Development Server starten (mit Hot Reload)
npm start

# Production Build erstellen
npm run build

# Tests ausführen
npm test
```

### Hot Reload

Spring Boot DevTools ermöglicht automatisches Neuladen bei Code-Änderungen. React Development Server unterstützt Hot Module Replacement (HMR).

---

## 🔒 Sicherheitshinweise

⚠️ **WICHTIG**: Dies ist ein **Lernprojekt** und sollte **NICHT** in Produktionsumgebungen verwendet werden!

- Die Standard-Konfiguration ist nicht für Produktionsumgebungen geeignet
- Sensible Daten sollten niemals im Code hardcodiert werden
- Verwenden Sie Umgebungsvariablen für Passwörter und API-Keys
- Implementieren Sie zusätzliche Sicherheitsmaßnahmen für produktive Systeme

---

## 📊 Clean Code Analyse

### ⚠️ Status: **Teilweise entspricht Clean Code Prinzipien**

Dieses Projekt ist als **Lernprojekt** entwickelt und zeigt grundlegende Funktionalität, erfüllt jedoch **nicht vollständig** alle Clean Code Standards. Im Folgenden finden Sie eine Analyse der gefundenen Probleme und Verbesserungsmöglichkeiten.

### ✅ Positive Aspekte

- ✅ **Konsistente Struktur** - Klare Trennung zwischen Controller, Service und Repository Layer
- ✅ **Spring Framework Patterns** - Korrekte Verwendung von Dependency Injection
- ✅ **Logging Framework** - Verwendung von SLF4J Logger (in den meisten Controllern)
- ✅ **RESTful API Design** - Sinnvolle URL-Strukturen und HTTP-Methoden
- ✅ **Package-Struktur** - Logische Organisation nach Entitäten und Funktionen
- ✅ **Microservices-Prinzip** - Gute Separation of Concerns durch Services

### ❌ Gefundene Clean Code Verstöße

#### 🔴 **Kritische Sicherheitsprobleme**

1. **Hardcodierte Secrets und Passwörter**
   - ❌ JWT Secret `"javatechie"` hardcodiert in allen `JwtUtil` Klassen
   - ❌ Email-Passwort `"gpcuphxksiekrqrp"` hardcodiert in Controllern
   - ❌ Email-Adressen hardcodiert: `"dummyahealthcare22@gmail.com"`
   - 💡 **Empfehlung**: Umgebungsvariablen oder Spring Cloud Config verwenden

2. **Sensible Daten im Code**
   - ❌ Email-Konfiguration direkt im Controller
   - ❌ Keine externe Konfiguration für sensible Werte

#### 🟡 **Code-Qualität Probleme**

3. **System.out.println statt Logger**
   ```java
   // In UserDetailsServiceImpl.java
   System.out.println("Validating user...................."+username);
   ```
   - ❌ `System.out.println` in Produktionscode
   - 💡 **Empfehlung**: Durch Logger ersetzen

4. **Kurze, nicht-aussagekräftige Variablennamen**
   ```java
   @Autowired
   private UserRepository ur;  // ❌ Statt userRepository
   @Autowired
   private RoleRepository rr;   // ❌ Statt roleRepository
   @Autowired
   private AccountRepository ar; // ❌ Statt accountRepository
   ```
   - 💡 **Empfehlung**: Aussagekräftige Namen verwenden

5. **Magic Numbers**
   ```java
   if (vendor.getLoginAttempts() >= 3)  // ❌ Magic Number
   setExpiration(new Date(System.currentTimeMillis()+1000*60*60*10)) // ❌ 10 Stunden
   double interestRate = 13;  // ❌ Magic Number
   lockertypeamount = 30;    // ❌ Magic Number
   ```
   - 💡 **Empfehlung**: Konstanten mit aussagekräftigen Namen definieren

6. **Code-Duplikation**
   - ❌ `JwtUtil` Klasse identisch in jedem Microservice (DRY-Prinzip verletzt)
   - ❌ Email-Versand-Code mehrfach dupliziert
   - ❌ SMTP-Konfiguration mehrfach im Code
   - 💡 **Empfehlung**: Gemeinsame Library oder Shared Module erstellen

7. **Auskommentierter Code**
   ```java
   //@CrossOrigin(origins = "http://localhost:3000", allowCredentials = "true")
   //user.setPassword(passwordEncoder.encode(user.getPassword()));
   ```
   - ❌ Tote Code-Kommentare
   - 💡 **Empfehlung**: Entfernen oder mit Version Control verwalten

8. **Rechtschreibfehler**
   ```java
   throw new Exception("Cusotmer with username " + username + " not found."); // ❌ "Cusotmer"
   ```
   - 💡 **Empfehlung**: Code-Review und Rechtschreibprüfung

9. **Statische Datenhaltung im Memory**
   ```java
   private static final Map<String, String> otpMap = new ConcurrentHashMap<>();
   ```
   - ❌ OTP-Verwaltung in Memory statt Datenbank/Redis
   - ❌ Verliert OTPs bei Service-Neustart
   - 💡 **Empfehlung**: Redis oder Datenbank für persistente OTP-Verwaltung

10. **Lange Methoden und hohe Komplexität**
    ```java
    public double calculateLockerPrice(String lockertype, String lockersize) {
        // 14 if-Statements in einer Methode
    }
    ```
    - ❌ Methoden zu lang und komplex
    - 💡 **Empfehlung**: In kleinere Methoden aufteilen, Switch-Statements oder Strategy Pattern verwenden

11. **Fehlende Eingabevalidierung**
    - ❌ Keine explizite Validierung von Request-Parametern
    - ❌ Keine Null-Checks an kritischen Stellen
    - 💡 **Empfehlung**: Bean Validation (`@Valid`, `@NotNull`) verwenden

12. **Fehlende Konstanten**
    ```java
    // Statt Hardcoding:
    private static final int MAX_LOGIN_ATTEMPTS = 3;
    private static final long TOKEN_EXPIRATION_MS = 1000 * 60 * 60 * 10; // 10 Stunden
    private static final double DEFAULT_INTEREST_RATE = 13.0;
    ```

13. **Inkonsistente Fehlerbehandlung**
    ```java
    } catch (Exception ex) {
        LOGGER.error("Authentication failed");
        throw new Exception("Invalid username/password."); // ❌ Generische Exception
    }
    ```
    - ❌ Generische Exception statt spezifische Exceptions
    - 💡 **Empfehlung**: Custom Exceptions verwenden

14. **Frontend-Code-Duplikation**
    - ❌ Doppelte Error-Handling-Logik im Frontend
    - ❌ Wiederholte Toast-Nachrichten

15. **String-Konkatenation statt StringBuilder**
    ```java
    String messageBody = "Dear customer,\n\n" + "Thank you..." + ...; // ❌ Ineffizient
    ```
    - 💡 **Empfehlung**: StringBuilder oder String.format() für längere Strings

### 💡 Clean Code Verbesserungsempfehlungen

#### Priorität 1 (Kritisch - Sicherheit)

1. **Secrets auslagern**
   ```java
   // Statt:
   private String secret="javatechie";
   
   // Besser:
   @Value("${jwt.secret}")
   private String jwtSecret;
   ```

2. **Passwörter entfernen**
   ```java
   // Statt:
   String senderPassword = "gpcuphxksiekrqrp";
   
   // Besser:
   @Value("${mail.password}")
   private String mailPassword;
   ```

#### Priorität 2 (Code-Qualität)

3. **Konstanten definieren**
   ```java
   public class SecurityConstants {
       public static final int MAX_LOGIN_ATTEMPTS = 3;
       public static final long TOKEN_EXPIRATION_HOURS = 10;
   }
   ```

4. **Code-Duplikation eliminieren**
   - Gemeinsames `JwtUtil` in Shared Library
   - Email-Service als separater Service oder Utility-Klasse

5. **Aussagekräftige Namen**
   ```java
   // Statt: ur, rr, ar
   private UserRepository userRepository;
   private RoleRepository roleRepository;
   private AccountRepository accountRepository;
   ```

6. **Validierung hinzufügen**
   ```java
   @PostMapping("/register")
   public Users create(@Valid @RequestBody Users user) {
       // ...
   }
   ```

#### Priorität 3 (Verbesserung)

7. **Exception-Handling verbessern**
   ```java
   throw new UserNotFoundException("Customer with username not found");
   ```

8. **Komplexe Methoden aufteilen**
   - Strategy Pattern für Preisberechnung
   - Separate Methoden für verschiedene Locker-Typen

### 📝 Fazit

**Dieses Projekt erfüllt Clean Code Standards teilweise:**

- ✅ **Gut**: Architektur, Struktur, Framework-Nutzung
- ⚠️ **Verbesserungsbedarf**: Sicherheit, Code-Duplikation, Magic Numbers
- ❌ **Kritisch**: Hardcodierte Secrets und Passwörter (für Produktion ungeeignet)

**Als Lernprojekt ist der Code akzeptabel**, da er:
- Funktionalität demonstriert
- Konzepte veranschaulicht
- Lernzwecken dient

**Für Produktionsumgebungen wäre eine umfassende Refaktorierung erforderlich:**
- Alle Hardcoded Secrets entfernen
- Code-Duplikation eliminieren
- Validierung und Error-Handling verbessern
- Vollständige Test-Abdeckung

---

---

## 📝 Lizenz & Hinweis

### ⚠️ Wichtiger Hinweis

**Dieses Projekt ist ein privates Lernprojekt und dient ausschließlich Bildungszwecken.**

- ❌ **NICHT für Produktionsumgebungen** geeignet
- ❌ **KEIN kommerzieller Einsatz** vorgesehen
- ✅ **Lern- und Demonstrationszwecke** erlaubt
- ✅ **Code-Review und Studium** erwünscht

### Projektstatus

- **Status**: Lernprojekt / Educational Project
- **Version**: 0.1.0
- **Entwicklungsstand**: Funktional für Demonstration

### Verwendung

Dieses Projekt kann frei für:
- Lernzwecke
- Portfolio-Demonstrationen
- Code-Studien
- Educational Workshops

verwendet werden.

**Für kommerzielle oder produktive Zwecke ist eine vollständige Überarbeitung und Sicherheitsprüfung erforderlich.**

---

## 🤝 Beitrag leisten

Da dies ein privates Lernprojekt ist, sind Beiträge willkommen, aber bitte beachten Sie:

1. Öffnen Sie ein Issue für größere Änderungen
2. Stellen Sie sicher, dass Ihr Code dem bestehenden Stil entspricht
3. Testen Sie Ihre Änderungen gründlich
4. Dokumentieren Sie neue Features

---

## 📞 Kontakt & Support

Für Fragen oder Anregungen zu diesem Lernprojekt:

- Erstellen Sie ein Issue im Repository
- Kontaktieren Sie den Projektbetreuer (falls vorhanden)

---

## 🙏 Danksagung

Dieses Projekt wurde entwickelt, um moderne Software-Architektur-Patterns und Best Practices zu lernen und zu demonstrieren.

---

<div align="center">

**Entwickelt für Lernzwecke** 📚

*Letzte Aktualisierung: Oktober 2025*

</div>
