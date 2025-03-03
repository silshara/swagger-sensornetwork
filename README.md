# Sensor Network API

## Overview

The **Sensor Network API** provides a standardized interface for managing **buildings** and their associated **sensors** within a sensor network. It supports a range of operations, allowing systems to:

- Create and manage buildings
- Add, update, and monitor sensors within buildings
- Track sensor states in real-time (online, offline, error)

This API is designed for **IoT platforms**, **smart building management systems**, and **facility monitoring tools**. It uses **OpenAPI 3.1** for its definition, ensuring compatibility with modern tooling and documentation platforms.

---

## 🌐 Base URL

`https://api.example.com/v1`

---

## 📋 Endpoints Summary

### Building Management
| Method | Endpoint                       | Description                              |
|-------|--------------------------------|----------------------------------|
| GET   | `/buildings`                    | Retrieve a list of all buildings |
| POST  | `/buildings`                    | Create a new building |
| GET   | `/buildings/{buildingId}`       | Retrieve details of a specific building |
| PUT   | `/buildings/{buildingId}`       | Update a building's details |

---

### Sensor Management
| Method | Endpoint                                    | Description                              |
|-------|--------------------------------|----------------------------------|
| GET   | `/buildings/{buildingId}/sensors` | List all sensors in a specific building |
| POST  | `/sensors`                             | Add or replace a sensor |
| GET   | `/sensors?state={state}`        | Retrieve sensors by state (online, offline, error) |
| PATCH | `/sensors/{sensorId}`         | Update a sensor's state |
| DELETE| `/sensors/{sensorId}`         | Delete a sensor |

---

## 📊 Data Models

### Building
```json
{
    "id": 1,
    "name": "Building A",
    "address": {
        "streetAddress": "123 Main St",
        "postNumber": 12345
    }
}
```

### Sensor
```json
{
    "id": "123e4567-e89b-12d3-a456-426614174000",
    "name": "Temperature Sensor",
    "value": 22.5,
    "state": "online"
}
```

---

## ⚠️ Important Notes

- Each **sensor** is automatically linked to its **corresponding building** in the backend database.
- When adding or replacing a sensor via `POST /sensors`, you are not required to specify the `buildingId`, as the backend already knows this relationship.
- Sensors can be **retrieved by building** (`/buildings/{buildingId}/sensors`) or **by state** (`/sensors?state=online`).

---

## 🛠️ Error Responses
| Status Code | Meaning |
|----|----|
| 400 | Invalid input data |
| 404 | Building or sensor not found |
| 201 | Resource created successfully |
| 204 | Resource deleted successfully |

---

## 📚 Example Use Case

You are managing a **campus with multiple buildings**, each equipped with **temperature, humidity, and air quality sensors**. Using this API, you can:
- Add new buildings and sensors.
- Continuously monitor sensor states.
- Trigger alerts when sensors report an **error** state.
- Perform maintenance by updating sensor data or replacing faulty sensors.

---

## 🚀 Technologies
- OpenAPI 3.1
- RESTful principles
- Supports JSON payloads

---

