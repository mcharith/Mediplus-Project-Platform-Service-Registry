# Service-Registry

---

A centralized **service discovery server** built using **Netflix Eureka**.  
All microservices register themselves here on startup, allowing the API Gateway and other services to dynamically discover and communicate using service names instead of hardcoded URLs.

---

## 📖 About

The Service-Registry is a core component of the microservices architecture, enabling dynamic service discovery and communication.  
Instead of relying on fixed IP addresses or URLs, each service registers itself with the registry at startup and periodically sends heartbeats to maintain its availability status.

This approach improves system flexibility, scalability, and fault tolerance. The API Gateway and other services can query the registry to locate services using logical names (e.g., `PATIENT-SERVICE`), enabling load balancing and seamless service-to-service communication.

The registry integrates with **Spring Cloud Eureka Server** and fetches its configuration from the Config-Server, ensuring centralized configuration management across the system.

---

## 🛠️ Tech Stack

| Technology                           | Details                          |
|--------------------------------------|----------------------------------|
| Java                                 | 25                               |
| Spring Boot                          | 4.0.3                            |
| Spring Cloud                         | 2025.1.0                         |
| Spring Cloud Netflix Eureka Server   | Service discovery                |
| Spring Boot Actuator                 | Health & management endpoints    |

---

## ⚙️ Service Details

| Property       | Value                 |
|----------------|-----------------------|
| Port           | 9001                  |
| Artifact ID    | Service-Registry      |
| Group ID       | lk.ijse.eca           |
| Config Source  | http://localhost:9100 |

---

## ⚡ How It Works

- Each microservice registers with the Service-Registry on startup
- Services send periodic heartbeats to indicate they are alive
- The registry maintains an updated list of all available services
- API Gateway and other services query the registry to locate services dynamically
- Supports load-balanced communication using URIs like:(lb://PATIENT-SERVICE)

---

## 🚀 Getting Started

### ⚠️ Important

Config-Server must be running before starting the Service-Registry, as it fetches its configuration from the Config-Server during startup.

---

### 🔄 Startup Order

1. Config-Server (9100)
2. Service-Registry (9001)
3. Other Services

---

### ▶️ Run the Service

```bash
./mvnw spring-boot:run
```

---

### 🌐 Access Eureka Dashboard

```
http://localhost:9001
```
