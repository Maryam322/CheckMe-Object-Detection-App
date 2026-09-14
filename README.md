 CheckMe — AI-Powered Object Detection App

CheckMe is an AI-powered object detection application that allows users to capture an image using their mobile camera or select an image from their gallery and detect objects using a YOLOv8 deep learning model.

The application combines a React Native mobile frontend with a Django REST API backend, where uploaded images are processed by the YOLOv8 model and the detection results are returned to the mobile application.

 Features
 Capture images using the device camera
 Select images from the device gallery
 AI-powered object detection using YOLOv8
 Detect multiple objects in an image
Display detected object names
Return an annotated image with detection results
REST API communication between mobile app and backend
Django-based backend
React Native mobile application
 Docker configuration for backend deployment
 PostgreSQL support for production deployment

 Tech Stack
Frontend
React Native
Expo
JavaScript
React Navigation
Axios
Expo Camera
Expo Image Picker
Expo Media Library
Backend
Python
Django
Django REST Framework
django-cors-headers
Gunicorn
WhiteNoise
AI / Computer Vision
YOLOv8
Ultralytics
Image processing
Object detection
Database
SQLite for local development
PostgreSQL for production
DevOps / Deployment
Docker
Docker Compose
Render / Railway
Expo EAS

 How It Works
1. Image Selection

The user can either:

Take a photo using the camera
Select an existing image from the gallery
2. Image Upload

The React Native application sends the selected image to the Django backend through a REST API request.

Mobile App
    ↓
POST /upload/
    ↓
Django REST API
3. Object Detection

The Django backend receives the image and passes it to the YOLOv8 model.

YOLOv8 analyzes the image and identifies objects present in it.

4. Result Generation

The backend generates an annotated image containing detection boxes and labels.

The API returns information including:

Annotated image URL
Detected objects
Detection results
5. Results Display

The React Native application receives the response and displays the detection results to the user.

 Backend Setup
1. Clone the repository
git clone https://github.com/Maryam322/CheckMe-Object-Detection-App.git
cd CheckMe-Object-Detection-App
2. Open the Backend directory
cd Backend/object_detection
3. Create a virtual environment

Windows:

python -m venv venv

Activate it:

venv\Scripts\activate
4. Install dependencies
pip install -r ../../requirements.txt
5. Create environment variables

Create:

.env

inside:

Backend/object_detection/

Example:

DEBUG=True
SECRET_KEY=your-secret-key
ALLOWED_HOSTS=127.0.0.1,localhost

DB_NAME=
DB_USER=
DB_PASSWORD=
DB_HOST=
DB_PORT=

For local development, the application can use SQLite.

6. Run migrations
python manage.py migrate
7. Start the Django server
python manage.py runserver

The backend will normally run at:

http://127.0.0.1:8000/
Open a new terminal.

Navigate to:

cd FrontEnd/ReactNative
1. Install dependencies
npm install
2. Create environment file
Create:

.env

Add your backend URL:

EXPO_PUBLIC_SERVER_URL=http://YOUR-BACKEND-IP:8000/upload/

For a physical Android phone, use the computer's local network IP instead of localhost.

Example:

EXPO_PUBLIC_SERVER_URL=http://192.168.1.10:8000/upload/
3. Start Expo
npm start

or:

npx expo start

Then open the application using:

Expo Go
Android emulator
Development build
 API Endpoint
Upload Image
POST /upload/
Request
Content-Type: multipart/form-data

Form field:

image
Example
POST http://YOUR-BACKEND-URL/upload/

The image is sent as a multipart file.

Response

The backend returns detection information including the processed image and detected objects.

 Docker Setup

The backend includes Docker configuration.

From the Backend directory:

docker-compose up --build

This builds and starts the backend environment.

 Deployment

The backend can be deployed using platforms such as:
Render
Railway
VPS / Cloud server
For production deployment:

Create a PostgreSQL database.
Deploy the Django backend.
Configure environment variables.
Set the production backend URL.
Update the React Native .env.
Build the Android application using Expo EAS.
 Android APK

After deploying the backend, update:

EXPO_PUBLIC_SERVER_URL=https://YOUR-BACKEND-DOMAIN/upload/

Then build the Android application using EAS:

eas build -p android --profile production

The generated APK can then be installed on an Android device.

 Environment Variables

Sensitive environment files are intentionally excluded from GitHub.

Use the provided example files:

Backend/object_detection/.env.example
FrontEnd/ReactNative/.env.example

Create your own .env files locally.

Never commit passwords, API keys, secret keys or private credentials to GitHub.

 Project Goals

The project was developed to demonstrate the integration of:
Mobile application development
REST API development
Django backend architecture
Deep learning
Computer vision
YOLO object detection
Image processing
Client-server communication
