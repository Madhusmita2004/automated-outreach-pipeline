# Automated Outreach Pipeline

## Overview

Automated Outreach Pipeline is a Spring Boot application that automates the B2B outreach process by:

1. Finding similar companies based on a seed domain.
2. Discovering decision-makers from those companies.
3. Fetching work email addresses.
4. Generating personalized outreach emails.
5. Sending emails through an email service.
6. Storing outreach activities in a PostgreSQL database.

This project demonstrates API integration, database management, logging, retry mechanisms, and automated email workflows.

---

## Features

- Company discovery using Ocean API integration
- Decision-maker extraction using Prospeo API integration
- Work email discovery using EazyReach API integration
- Automated email generation
- Email sending through Brevo
- PostgreSQL database persistence
- Retry mechanism for external API failures
- Logging and outreach tracking
- RESTful API endpoints
- Swagger/OpenAPI documentation

---

## Technology Stack

### Backend
- Java 17
- Spring Boot 3
- Spring Data JPA
- Spring Web
- OpenFeign

### Database
- PostgreSQL

### Documentation
- Swagger / OpenAPI

### Build Tool
- Maven

### Utilities
- Lombok
- SLF4J Logging

---

## Project Structure

```text
src/main/java/com/vocallabs/outreach

├── client
│   ├── OceanClient
│   ├── ProspeoClient
│   ├── EazyReachClient
│   └── BrevoClient
│
├── controller
│   ├── HealthController
│   └── OutreachController
│
├── service
│   ├── OceanService
│   ├── ProspeoService
│   ├── EazyReachService
│   ├── BrevoService
│   └── PipelineService
│
├── repository
├── entity
├── dto
├── util
└── config
```

---

## Workflow

### Step 1
User submits a company domain.

Example:

```json
{
  "domain": "amazon.com"
}
```

### Step 2
Ocean Service finds similar companies.

### Step 3
Prospeo Service finds decision-makers.

### Step 4
EazyReach Service fetches work email addresses.

### Step 5
System asks for confirmation before sending emails.

### Step 6
Personalized email content is generated.

### Step 7
Brevo sends outreach emails.

### Step 8
Outreach logs are stored in PostgreSQL.

---

## API Endpoints

### Health Check

```http
GET /api/health
```

Response:

```text
Pipeline Service is Running
```

---

### Run Outreach Pipeline

```http
POST /api/run
```

Request Body:

```json
{
  "domain": "amazon.com"
}
```

Response:

```text
Pipeline Completed
```

---

## Database Entities

### Company

Stores discovered companies.

Fields:
- id
- companyName
- companyDomain
- seedDomain

### Contact

Stores decision-makers.

Fields:
- id
- name
- designation
- linkedinUrl

### Email

Stores verified email addresses.

Fields:
- id
- email
- verified

### OutreachLog

Stores email sending history.

Fields:
- id
- subject
- status
- sentAt

---

## Installation

### Clone Repository

```bash
git clone https://github.com/Madhusmita2004/automated-outreach-pipeline.git
```

### Move to Project Directory

```bash
cd automated-outreach-pipeline
```

### Configure Database

Update:

```properties
src/main/resources/application.properties
```

Example:

```properties
spring.datasource.url=jdbc:postgresql://localhost:5432/outreach_db
spring.datasource.username=postgres
spring.datasource.password=password
```

### Build Project

```bash
mvn clean install
```

### Run Application

```bash
mvn spring-boot:run
```
---

## Swagger Documentation

After starting the application:

```text
http://localhost:8080/swagger-ui.html
```

## Logging

The application logs:

- Company discovery
- Contact discovery
- Email extraction
- Email sending status
- Pipeline summary



## Future Improvements

- Real API integrations
- Email templates
- Scheduler support
- Bulk campaign management
- Analytics dashboard
- Docker deployment
- Kubernetes deployment
- Authentication & Authorization

---

## Author

MadhuSmita panda

Java Full Stack Developer

Skills:
- Java
- Spring Boot
- Hibernate
- SQL
- HTML
- CSS
- JavaScript
- REST APIs

---
