Smart City Traffic Monitoring System
Real-Time AQI, Noise, Humidity, Route Planning & Automated AWS Alerts
This project is an end-to-end Smart City Traffic Monitoring Dashboard that visualizes real-time sensor data (AQI, noise, humidity) across multiple junctions and determines vehicle movement and safe routes using intelligent algorithms.
The system integrates AWS S3, Lambda, API Gateway, and SNS to fetch and process live data, trigger alerts, and provide it to the frontend dashboard.

 Features
Interactive Frontend Dashboard
Built using HTML, CSS, and JavaScript, featuring:
Real-time junction signals (Green / Yellow / Red)
AQI, noise level & humidity visualization
Vehicle animation on SVG map
Automatic rerouting based on AQI levels
Optimal safe route calculation
Dynamic datasets loaded via API Gateway
AWS Cloud Integration
AWS S3
Stores real-time sensor dataset (dataset_2__partial_data.json)
Lambda fetches the dataset from S3
lambda code
AWS Lambda

Lambda function processes the S3 data and:
Reads AQI values per junction
Detects high AQI levels (>150)
Publishes alerts via SNS
Returns dataset response to API Gateway

IAM Role
Lambda execution role includes:
s3:GetObject access
sns:Publish permissions

CloudWatch logging permissions
AWS SNS
Sends SMS/Email alerts when AQI > 150 at any junction.

Message sample:
"Alert: High AQI detected at J3, J5"
API Gateway
Exposes REST API endpoint

Dashboard fetches live data using JavaScript fetch()
Endpoint example:
https://d3wui4o2xg.execute-api.ap-south-1.amazonaws.com/prod/process-data

Used in script:
script
Frontend Files (Included in Repo)
index.html
index
styles.css
styles
script.js
Fetching data from API

How to Run Locally
Clone the Repository
git clone https://github.com/your-username/smart-city-traffic.git
cd smart-city-traffic

Open the project
Just open index.html in any browser.

Ensure API Gateway URL is correct
Inside script.js, update:

const apiEndpoint = "YOUR_API_GATEWAY_URL";
AWS Setup Steps (Short)
Upload dataset to S3
Create bucket → Upload JSON file.
Create Lambda function
Add code from lambda code.txt
Attach IAM role with S3 + SNS permissions
Create SNS Topic
Subscribe via email or SMS.
Create API Gateway
Integrate with Lambda
Enable CORS
Deploy stage
Replace API URL in script.js

