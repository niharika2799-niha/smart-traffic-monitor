Smart City Traffic Monitoring System
Overview
The Smart City Traffic Monitoring System is a web-based interactive dashboard designed to visualize real-time traffic conditions using live environmental data such as AQI, noise levels, humidity, and vehicle movement. The application integrates AWS services including S3, Lambda, API Gateway, IAM Roles, and SNS to process and deliver real-time data, as well as send alerts for hazardous conditions. The frontend, built using HTML, CSS, and JavaScript, provides an interactive map-based interface for monitoring junctions and finding optimal routes.

Features
Live Traffic Metrics: Displays AQI, noise, humidity, and signal status at different junctions.
Safe Route Detection: Computes optimal routes between two junctions based on current signal and AQI conditions.
Vehicle Simulation: Visual representation of vehicles moving across junctions.
AWS-Powered Backend: Lambda fetches data from S3, triggers SNS alerts, and delivers processed data via API Gateway.
Automatic Alerts: Sends notifications when AQI exceeds safe threshold values.

Table of Contents
Installation
Configuration
Usage
Project Structure
Contributing

Installation
1. Clone the Repository
git clone https://github.com/yourusername/smart-city-traffic.git
cd smart-city-traffic

2. Set Up AWS Services
You must configure:
S3 bucket for JSON dataset
Lambda function
SNS topic
API Gateway

3. Update API Endpoint
In script.js, replace the placeholder with your API Gateway URL:
const apiEndpoint = "https://your-api-url.amazonaws.com/prod/process-data";

4. Run the Application
Open index.html in any browser.

Configuration
Main Dataset (Stored in S3)
The file stored in your S3 bucket should be named (example):
dataset_2__partial_data.json

Example dataset:

[
  { "id": "J1", "aqi": 60, "noiseLevel": 50, "humidity": 70 },
  { "id": "J2", "aqi": 170, "noiseLevel": 65, "humidity": 55 }
]

AWS Lambda Function (lambda-code.txt)
Lambda fetches this file from S3, checks AQI values, sends alerts via SNS, and returns JSON output to the frontend.

Usage
Launch the Dashboard

Simply open:
index.html

The interface will automatically:
Fetch live data every few seconds
Update signal colors
Display environmental metrics
Show safe route results
Animate vehicle movement
Computed Features
Signal Assignment
Based on AQI thresholds:
AQI < 100 → Green
100–200 → Yellow
200 → Red
Safe Route Finder
Uses BFS algorithm to avoid:
Red signals
AQI > 200
Vehicle Movement
Vehicles move dynamically between safe junctions.

Project Structure
smart-city-traffic/
├── index.html                # Main dashboard UI
├── styles.css                # Styling and layout
├── script.js                 # Frontend logic, map rendering, API calls
├── lambda-code.txt           # AWS Lambda backend function
├── README.md                 # Documentation
└── assets/                   # Optional images or icons

AWS Architecture

S3: Stores sensor dataset
Lambda: Reads S3 file, checks AQI, sends SNS alerts
SNS: Sends notifications if AQI > 150
API Gateway: Exposes Lambda as HTTP endpoint
IAM Roles: Grants Lambda access to S3 and SNS

Contributing
Contributions are welcome. To contribute:
Fork the repository
Create a new feature branch
Commit your changes
Open a pull request describing your update

