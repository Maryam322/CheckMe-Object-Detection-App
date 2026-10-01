# CheckMe — AI-Powered Object Detection App

**CheckMe** is an AI-powered mobile object detection application that allows users to capture an image using their camera or select one from their gallery and detect objects using the **YOLOv8 deep learning model**.

The project combines a **React Native mobile application** with a **Django REST API backend**. Images are uploaded to the backend, processed by YOLOv8, and returned with detected objects and an annotated image.

##  Features

*  Capture images using the device camera
*  Select images from the gallery
*  YOLOv8-powered object detection
*  Detect multiple objects in images
*  Display detected object names
*  Generate annotated images with bounding boxes
*  REST API communication
*  React Native mobile application
*  Django REST API backend
*  Docker & Docker Compose support
*  PostgreSQL support for production
*  Deployment support for Render/Railway
*  Android APK build using Expo EAS

##  Tech Stack

### Frontend

* React Native
* Expo
* JavaScript
* React
  
### Backend

* Python
* Django
* Django REST Framework
* django-cors-headers
* Gunicorn
* WhiteNoise

### AI / Computer Vision

* YOLOv8
* Ultralytics
* Image Processing
* Object Detection

### Database

* SQLite — Local Development
* PostgreSQL — Production

### Deployment

* Docker
* Docker Compose
* Render / Railway
* Expo EAS

### Detection Process

1. The user captures an image or selects one from the gallery.
2. The React Native application uploads the image to the Django API.
3. Django receives the image through the REST API.
4. YOLOv8 analyzes the image and detects objects.
5. The backend generates an annotated image.
6. Detection results and the processed image are returned to the mobile app.
7. The application displays the detected objects and annotated image.

##  Backend Setup

### 1. Clone the Repository

```bash
git clone https://github.com/Maryam322/CheckMe-Object-Detection-App.git
cd CheckMe-Object-Detection-App
```

### 2. Navigate to Backend

```bash
cd Backend/object_detection
```

### 3. Create Virtual Environment

**Windows:**

```bash
python -m venv venv
```

Activate it:

```bash
venv\Scripts\activate
```

### 4. Install Dependencies

```bash
pip install -r ../../requirements.txt
```

### 5. Configure Environment Variables

Create a `.env` file inside:

```text
Backend/object_detection/
```

Example:

```env
DEBUG=True
SECRET_KEY=your-secret-key
ALLOWED_HOSTS=127.0.0.1,localhost

DB_NAME=
DB_USER=
DB_PASSWORD=
DB_HOST=
DB_PORT=
```

SQLite can be used for local development.

### 6. Run Migrations

```bash
python manage.py migrate
```

### 7. Start Django Server

```bash
python manage.py runserver
```

Backend:

```text
http://127.0.0.1:8000/
```

## Frontend Setup

Open a new terminal and navigate to:

```bash
cd FrontEnd/ReactNative
```

### 1. Install Dependencies

```bash
npm install
```

### 2. Configure Backend URL

Create a `.env` file:

```env
EXPO_PUBLIC_SERVER_URL=http://YOUR-BACKEND-IP:8000/upload/
```

For a physical Android device, use your computer's local network IP instead of `localhost`.

Example:

```env
EXPO_PUBLIC_SERVER_URL=http://192.168.1.10:8000/upload/
```

### 3. Start Expo

```bash
npm start
```

or:

```bash
npx expo start
```

The application can be opened using:

* Expo Go
* Android Emulator
## API

### Upload Image

```http
POST /upload/
```

**Content-Type:**

```text
multipart/form-data
```

**Form Field:**

```text
image
```

Example:

```text
POST http://YOUR-BACKEND-URL/upload/
```

The API processes the uploaded image using YOLOv8 and returns detection results along with the annotated image.

## Docker

The backend includes Docker configuration.

From the Backend directory:

```bash
docker-compose up --build
```

This builds and starts the backend environment.

##  Deployment

The Django backend can be deployed to:

* Render
* Railway
* VPS / Cloud Server

For production:

1. Create a PostgreSQL database.
2. Deploy the Django backend.
3. Configure environment variables.
4. Set the production backend URL.
5. Update the React Native `.env`.
6. Build the Android application using Expo EAS.

### Android APK

Update the backend URL:

```env
EXPO_PUBLIC_SERVER_URL=https://YOUR-BACKEND-DOMAIN/upload/
```

Build the Android application:

```bash
eas build -p android --profile production
```

##  Environment Variables

Sensitive environment files are excluded from GitHub.

Use the provided example files:

```text
Backend/object_detection/.env.example
FrontEnd/ReactNative/.env.example
```
##  Project Goals

This project demonstrates practical experience with:

*  Mobile Application Development
*  REST API Development
*  Django Backend Architecture
*  Deep Learning
*  Computer Vision
*  YOLO Object Detection
*  Image Processing
*  Client-Server Communication
*  Database Integration
*  Docker Deployment

## Developer

**Maryam Fatima**

Computer Science Student | Full Stack Developer

GitHub: [Maryam322](https://github.com/Maryam322)

---
 If you find this project useful, consider giving it a star!
