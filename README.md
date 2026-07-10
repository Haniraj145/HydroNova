🌱 HydroNova – Smart Farming Operating System
HydroNova is a full-stack SaaS platform combining IoT, AI, Cloud, and Real-time Dashboards to empower modern agriculture. Designed as a Smart Farming OS, it supports hydroponics today and scales to soil, aquaponics, and vertical farming tomorrow.

🚀 Vision
Mission: Real-time insights, automation, and AI-driven recommendations for farmers.

Target Users: Hydroponic farmers, greenhouse operators, agri-tech enterprises, researchers.

Future: Expand into all IoT-enabled agriculture verticals.

📋 Documentation Structure
All detailed docs live in /docs/:

Code
00_PROJECT_OVERVIEW.md
01_BUSINESS_REQUIREMENTS.md
02_SOFTWARE_REQUIREMENTS_SPECIFICATION.md
03_SYSTEM_ARCHITECTURE.md
04_DATABASE_DESIGN.md
05_BACKEND_ARCHITECTURE.md
06_FRONTEND_ARCHITECTURE.md
07_AI_ARCHITECTURE.md
08_IOT_ARCHITECTURE.md
09_CAMERA_STREAMING.md
10_SECURITY.md
11_API_DOCUMENTATION.md
12_FOLDER_STRUCTURE.md
13_DEPLOYMENT.md
14_DEVOPS.md
15_UI_COMPONENTS.md
16_USER_FLOW.md
17_ADMIN_PANEL.md
18_AI_MODELS.md
19_SENSOR_DOCUMENTATION.md
20_CODING_STANDARDS.md
21_TESTING.md
22_ROADMAP.md
⚙️ Features
Auth: Registration, Login, 2FA, Roles, Permissions, Audit Logs

Farm: Create/Delete Farms, Invite Users, Crop & Sensor Management

Dashboard: Real-time charts, alerts, AI recommendations, weather, reports

Camera: Live streaming, snapshots, motion detection, timelapse

AI: Disease detection, growth tracking, yield estimation, treatment suggestions

IoT: ESP32 devices, MQTT, OTA updates, offline buffer, device health

Notifications: Email, SMS, WhatsApp, Push, Slack, Webhooks

Admin: Users, payments, logs, analytics, devices, AI usage monitoring

🖥️ Tech Stack
Frontend: React + TypeScript (Vercel + Cloudflare)

Backend: Node.js + Express + TypeScript (AWS App Runner)

Database: PostgreSQL (Supabase → TimescaleDB → AWS RDS)

AI Service: Python FastAPI + YOLOv11 (EC2 GPU)

IoT: ESP32 + AWS IoT Core (MQTT)

Camera Streaming: MediaMTX (RTSP → HLS/WebRTC)

Storage: Amazon S3

Queue: Redis + BullMQ

CI/CD: GitHub Actions + Docker Compose

Monitoring: Sentry + CloudWatch

🔒 Security
JWT, OAuth, RBAC

HTTPS, Encryption, AWS IAM

OWASP Top 10 compliance

Rate limiting, CSRF/XSS/SQLi protection

📂 Folder Structure
Code
backend/
  src/
    controllers/
    routes/
    middleware/
    services/
    repositories/
    validators/
    config/
    jobs/
    events/
    cache/
    utils/
    prisma/
    tests/
frontend/
  src/
    components/
    pages/
    hooks/
    services/
    store/
    utils/
docs/
docker/
🛠️ Development Standards
Clean Architecture

TypeScript everywhere

Prisma ORM

OpenAPI docs updated with every feature

Tests required for new modules

Git branching & commit conventions

📈 Roadmap (MVP → Production)
Week 1: Backend foundation

Week 2: Authentication

Week 3: Farm module

Week 4: Sensors

Week 5: Real-time (Socket.IO + MQTT)

Week 6: Camera streaming

Week 7: AI (YOLO integration)

Week 8: Notifications

Week 9+: Admin, Billing, Deployment

🤖 AI Prompt Guide
See HOW_TO_WORK_ON_HYDRONOVA_WITH_AI.md for rules when using LLMs:

Never change folder structure

Always use TypeScript + Prisma

No business logic in controllers

Update OpenAPI docs consistently

Maintain backward compatibility

📜 License
Proprietary – HydroNova Technologies.




🌱 Hydroponic farm monitoring
📡 Live sensor data
📷 Live camera
🤖 AI disease detection
📊 Dashboard
🔔 Alerts
👨‍🌾 Multiple farms and users

  Main backend architecture

                 React Frontend (Already Done)
                          │
                    REST API + WebSocket
                          │
                Node.js + Express Backend
                          │
     ┌──────────────┬───────────────┬─────────────┐
     │              │               │             │
 Authentication   Sensor API     Camera API    AI API
     │              │               │             │
     └──────────────┴──────┬────────┴─────────────┘
                            │
                     PostgreSQL Database
                            │
                     Redis Cache (Optional)
                            │
                MQTT Broker / AWS IoT Core
                            │
                     ESP32 + Sensors
                            │
                    Farm Hydroponic System
Backend Folder Structure
backend/

src/

   config/
      db.js
      mqtt.js
      cloudinary.js

   controllers/
      auth.controller.js
      sensor.controller.js
      disease.controller.js
      farm.controller.js
      camera.controller.js
      notification.controller.js

   middleware/
      auth.js
      upload.js

   models/
      User.js
      Farm.js
      SensorData.js
      DiseaseHistory.js
      Camera.js

   routes/
      auth.routes.js
      sensor.routes.js
      farm.routes.js
      camera.routes.js
      disease.routes.js

   services/
      mqtt.service.js
      yolo.service.js
      websocket.service.js

   sockets/
      sensor.socket.js

   utils/

server.js
Database Design
Users
id
name
email
password
role
Farms
farm_id
user_id
farm_name
location
Sensors
sensor_id
farm_id
temperature
humidity
ph
ec
water_level
light
timestamp
Disease History
image_url

prediction

confidence

date
Camera
camera_id

farm_id

rtsp_url

status
APIs
Authentication
POST /register

POST /login

GET /profile
Sensor
GET /sensor/latest

GET /sensor/history

POST /sensor/update

ESP32 har 5 second me data bhejega

{
"temperature":27,
"humidity":70,
"ph":6.2,
"ec":1.8,
"water":95
}

Backend store karega.

Frontend automatically update karega.

Live Sensor Data

Iske liye polling mat use karna.

Use

Socket.IO

Ya

WebSocket

Flow

ESP32

↓

MQTT

↓

Backend

↓

Socket.IO

↓

React Dashboard

Dashboard refresh nahi hoga.

Needle aur graphs automatically move honge.

Camera

Do option hain.

Option 1

ESP32-CAM

MJPEG stream

http://camera-ip:81/stream

Frontend

<img src="stream">

Simple

Option 2 (Recommended)

IP Camera

RTSP

↓

MediaMTX

↓

HLS

↓

Website

Isme

Live Video
Recording
Multiple cameras

sab possible hai.

Photo Upload

User photo upload kare

↓

Backend

↓

YOLO

↓

Prediction

↓

Frontend

Automatic Detection

Camera

↓

Every 10 minutes image capture

↓

YOLO

↓

Prediction

↓

Database

↓

Alert

↓

Frontend

AI Service

Main AI ko backend ke andar directly nahi rakhunga.

Separate service banaunga.

Node Backend

↓

Python FastAPI

↓

YOLO

↓

Prediction

Isse AI independently scale ho sakta hai.

AI Models

Main recommendation ye hai:

Disease Detection

✅ YOLOv11 (Ultralytics)

ya

YOLOv8

Dono bahut fast hain.

Disease Classification

Agar sirf disease identify karni hai

EfficientNet B3

ya

ConvNeXt Tiny

Accuracy kaafi achchi hoti hai.

Agar multiple disease detect karni hain

YOLOv11

SAM2 (Segment Anything)

Plant ke infected area ko highlight bhi kar dega.

Future

Google Gemini Vision

ya GPT-4.1 Vision jaise VLM ko disease explanation aur treatment recommendation ke liye use kar sakte ho.

Notifications

Agar

Temperature > 35

↓

Send Notification

High Temperature

Agar

PH <5.5

↓

Alert

Tech Stack

Frontend

React
TypeScript
Tailwind

Backend

Node.js
Express
Socket.IO
JWT
Prisma ORM

Database

PostgreSQL
TimescaleDB (sensor time-series data ke liye bahut accha)

AI

Python
FastAPI
YOLOv11
OpenCV
PyTorch

IoT

ESP32
MQTT
AWS IoT Core (production) ya Mosquitto (development)

Cloud

AWS App Runner (Node backend)
EC2 ya GPU instance (AI inference agar load zyada ho)
Amazon S3 (images/videos)
PostgreSQL (Supabase ya AWS RDS)
Startup-level Data Flow
ESP32 Sensors
      │
      ▼
 MQTT / AWS IoT Core
      │
      ▼
Node.js Backend
      │
      ├── PostgreSQL (sensor history)
      ├── Socket.IO (real-time dashboard)
      ├── S3 (images/videos)
      └── FastAPI AI Service
              │
         YOLOv11 + OpenCV
              │
      Disease Prediction
              │
      Database + Alerts
              │
      React Dashboard
