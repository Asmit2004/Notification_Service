# Notification Service – Internship Assignment

## Objective:
To design and implement a notification service that can send notifications to users based on their preferences and the type.

## Project description:
A Node.js microservice to send and retrieve user notifications via Email, SMS, or In-App, using a queue for processing.

## Tech used:
- Node.js
- Express
- RabbitMQ (via amqplib)
- In-memory storage
- Retry logic

##  API Endpoints

### 1. Send Notification
`POST /notifications`

**Request Body:**
```json
{
  "userId": "123",
  "type": "email", 
  "message": "Hello user!"
}
```

### 2. Get User Notifications
`GET /users/{id}/notifications`

**Response:**
```json
[
  {
    "id": "...",
    "userId": "123",
    "type": "email",
    "message": "Hello user!",
    "timestamp": "2025-05-18T10:00:00Z"
  }
]
```

##  Features:
-  Async processing with RabbitMQ
-  Retry for failed notifications (2-second delay, 1 retry max)
-  Console logging for Email/SMS
-  In-memory store for In-App

## Setup Instructions

1. Clone the repo
```bash
 Open terminal or code editor 
 cd notification_service_node

2. Start RabbitMQ (Docker)
```bash
docker run -d --hostname rabbit --name rabbitmq -p 5672:5672 -p 15672:15672 rabbitmq:3-management
```

3. Install dependencies and run the server
```bash
npm install express body-parser amqplib uuid
node server.js
```

4. Use Postman or curl to test API endpoints

## Assumptions
- Notifications are logged, not sent to real email/SMS gateways.
- In-memory storage is used for simplicity.
