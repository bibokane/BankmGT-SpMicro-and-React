# BankmGT - Banking Management System

<div align="center">

![Java](https://img.shields.io/badge/Java-17-orange)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-2.7.12-brightgreen)
![Spring Cloud](https://img.shields.io/badge/Spring%20Cloud-2021.0.2-blue)
![React](https://img.shields.io/badge/React-18.2.0-61dafb)
![MySQL](https://img.shields.io/badge/MySQL-8.0-4479A1)

**Moderne Microservices-Architektur für Banking-Management**

</div>

---

## 📖 Über das Projekt

**BankmGT** ist ein vollständiges Banking Management System mit Microservices-Architektur. Das Projekt wurde zum Lernzwecken erworben und kontinuierlich erweitert, um moderne Software-Engineering-Konzepte zu demonstrieren und praktische Erfahrungen mit professionellen Architektur-Patterns zu sammeln.

### Technische Highlights

- **Microservices-Architektur** mit 7 unabhängigen Spring Boot Services
- **Service Discovery** via Netflix Eureka
- **API Gateway** Pattern mit Spring Cloud Gateway
- **JWT-basierte Authentifizierung** mit Spring Security
- **React SPA** Frontend mit Material-UI
- **RESTful API Design** mit standardisierten Endpunkten

---

## 🏗️ Systemarchitektur

```
┌─────────────┐     ┌──────────────┐     ┌──────────────┐
│   React     │────▶│ API Gateway  │────▶│ Microservices│
│  Frontend   │     │   (9999)     │     │  (8081-8086) │
│   (3000)    │     └──────────────┘     └──────────────┘
└─────────────┘            │                     │
                    ┌──────▼──────┐              │
                    │   Eureka    │◀─────────────┘
                    │   (8761)    │
                    └──────┬──────┘
                           │
                    ┌──────▼──────┐
                    │    MySQL    │
                    │   (3306)    │
                    └─────────────┘
```

---

## 💻 Technologie-Stack

### Backend
- **Java 17** • **Spring Boot 2.7.12** • **Spring Cloud 2021.0.2**
- **Spring Cloud Gateway** • **Netflix Eureka** • **Spring Security**
- **Spring Data JPA** • **Hibernate** • **JWT (JJWT)**
- **MySQL 8.0+** • **Maven**

### Frontend
- **React 18.2.0** • **React Router DOM 6.12.1** • **Axios 1.4.0**
- **Material-UI 5.13.5** • **Bootstrap 5.3.0**
- **Formik** • **Yup** • **React Toastify**

---

## ✨ Hauptfeatures

### 🔐 Authentifizierung & Benutzerverwaltung
- JWT-basierte Authentifizierung mit rollenbasierter Zugriffskontrolle (Customer, Employee, Admin)
- Benutzerregistrierung mit automatischer Kontogenerierung
- Passwort-Reset mit OTP-Verifizierung per E-Mail

### 💰 Transaktionsmanagement
- Einzahlungen, Abhebungen und Überweisungen
- Transaktionshistorie mit Datum-Filterung und PDF-Export
- Echtzeit-Saldo-Verwaltung

### 💳 Banking-Services
- **Darlehensverwaltung** - Anträge, EMI-Berechnung, Rückzahlungsverwaltung
- **Kreditkartenverwaltung** - Anträge, Zahlungen, EMI-Management, Limit-Tracking
- **Schließfachverwaltung** - Anträge, Preisberechnung, Gebührenverwaltung
- **Geschenkkartenverwaltung** - Kauf und Verwaltung von Geschenkkarten

### 👥 Rollenspezifische Funktionen
- **Kunden**: Selbstregistrierung, Profilverwaltung, eigene Banking-Services
- **Mitarbeiter**: Dashboard, Kontoverwaltung, Antragsverwaltung, Transaktionsüberwachung
- **Administratoren**: Vollständige Benutzerverwaltung, Systemüberwachung

---

## 🚀 Schnellstart

### Voraussetzungen
- Java JDK 17+
- Maven 3.6+ (oder Maven Wrapper)
- Node.js 16+ und npm 8+
- MySQL 8.0+ Server

### Installation

1. **Repository klonen**
```bash
git clone https://github.com/bibokane/BankmGT-SpMicro-and-React.git
cd BankmGT-SpMicro-and-React
```

2. **Datenbank einrichten**
```sql
CREATE DATABASE IF NOT EXISTS onlinebankingportal;
mysql -u root -p onlinebankingportal < Database/bankMgt.sql
```

3. **Datenbankkonfiguration anpassen**

Bearbeiten Sie die `application.properties` Dateien in jedem Service:
```properties
spring.datasource.url=jdbc:mysql://localhost:3306/onlinebankingportal?useLegacyDatetimeCode=false&serverTimezone=GMT
spring.datasource.username=IhrBenutzername
spring.datasource.password=IhrPasswort
```

4. **Frontend-Dependencies installieren**
```bash
cd Frontend
npm install
```

### Services starten

**Wichtig**: Starten Sie die Services in dieser Reihenfolge!

```bash
# 1. Eureka Server
cd Backend/Eureka
./mvnw.cmd spring-boot:run

# 2. Microservices (in separaten Terminals)
cd Backend/Login_Service && ./mvnw.cmd spring-boot:run
cd Backend/Transaction_Service && ./mvnw.cmd spring-boot:run
cd Backend/Loan_Service && ./mvnw.cmd spring-boot:run
cd Backend/Locker_Service && ./mvnw.cmd spring-boot:run
cd Backend/Credit_Card_Service && ./mvnw.cmd spring-boot:run
cd Backend/Gift_Card_Service && ./mvnw.cmd spring-boot:run

# 3. API Gateway
cd Backend/ApiGateway
./mvnw.cmd spring-boot:run

# 4. Frontend
cd Frontend
npm start
```

**Alternative**: Für IntelliJ IDEA Ultimate Setup siehe [INTELLIJ_SETUP.md](INTELLIJ_SETUP.md)

---

## 🔌 Service-Endpunkte

| Service | Port | Beschreibung |
|---------|------|--------------|
| **Eureka Server** | 8761 | http://localhost:8761 - Service Discovery Dashboard |
| **Login Service** | 8081 | Authentifizierung & Benutzerverwaltung |
| **Transaction Service** | 8082 | Transaktionsmanagement |
| **Loan Service** | 8083 | Darlehensverwaltung |
| **Locker Service** | 8084 | Schließfachverwaltung |
| **Credit Card Service** | 8085 | Kreditkartenmanagement |
| **Gift Card Service** | 8086 | Geschenkkartenverwaltung |
| **API Gateway** | 9999 | Zentraler API-Einstiegspunkt |
| **React Frontend** | 3000 | http://localhost:3000 - Web-Anwendung |

---

## 📡 API-Beispiele

### Authentifizierung
```http
POST http://localhost:9999/login/customer/authenticate
Content-Type: application/json

{
  "username": "customer",
  "password": "password"
}
```

### Transaktionen
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

---

## 📁 Projektstruktur

```
BankmGT-SpMicro-and-React/
├── Backend/                    # Spring Boot Microservices
│   ├── Eureka/                # Service Discovery (8761)
│   ├── Login_Service/         # Authentifizierung (8081)
│   ├── Transaction_Service/   # Transaktionen (8082)
│   ├── Loan_Service/          # Darlehen (8083)
│   ├── Locker_Service/        # Schließfächer (8084)
│   ├── Credit_Card_Service/   # Kreditkarten (8085)
│   ├── Gift_Card_Service/     # Geschenkkarten (8086)
│   └── ApiGateway/            # API Gateway (9999)
├── Frontend/                   # React SPA
│   ├── src/
│   │   ├── Components/        # React-Komponenten
│   │   ├── pages/             # Seiten-Komponenten
│   │   └── utility/           # Utilities & Auth
│   └── package.json
└── Database/                   # Datenbank-Skripte
    └── bankMgt.sql
```

---

## 🏆 Architektur-Patterns

✅ **Microservices-Architektur** - Unabhängige, skalierbare Services  
✅ **Service Discovery** - Automatische Service-Registrierung mit Eureka  
✅ **API Gateway Pattern** - Zentrale Routing-Logik und Request-Handling  
✅ **Layered Architecture** - Controller → Service → Repository Trennung  
✅ **JWT-Authentifizierung** - Token-basierte, stateless Authentifizierung  
✅ **RESTful API Design** - Standardisierte HTTP-Methoden und Ressourcen-Strukturen  

---

## 📝 Hinweis

**Dieses Projekt wurde zum Lernzwecken erworben und kontinuierlich erweitert.** Es dient als praktische Lernressource zur Veranschaulichung moderner Microservices-Architektur, Spring Boot Entwicklung und React Frontend-Entwicklung.

Das Projekt zeigt eine vollständige Implementierung einer Microservices-Architektur und kann als Referenz für ähnliche Projekte dienen.

---

## 📞 Repository

- **GitHub**: https://github.com/bibokane/BankmGT-SpMicro-and-React
- **Entwickler**: Habib Kane
- **Projekt-Typ**: Lernprojekt / Educational Project

---

<div align="center">

**Entwickelt mit ❤️ für Lernzwecke**

*Letzte Aktualisierung: Oktober 2025*

</div>
