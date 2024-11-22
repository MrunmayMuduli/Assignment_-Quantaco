# Assignment_-Quantaco

# README Instructions

# README.md Content

# Weather Data API

## Overview
This API allows users to fetch hourly weather data for a given venue and insert it into a database. It uses Open Meteo's API to gather weather data.

## Prerequisites
- Python 3.8+
- PostgreSQL Database
- AWS RDS or any cloud database instance
- Docker (optional for deployment)
- GitHub Actions or Jenkins for CI/CD pipeline

## Setup Instructions

### 1. Clone the Repository
```sh
git clone <repository-url>
cd <repository-folder>
```

### 2. Install Dependencies
```sh
pip install -r requirements.txt
```

### 3. Set Environment Variables
Create a `.env` file in the root directory with the following variables:
```sh
DB_USER=your_db_user
DB_PASSWORD=your_db_password
DB_HOST=your_db_host
DB_PORT=your_db_port
DB_NAME=your_db_name
```
Load environment variables using:
```sh
export $(cat .env | xargs)
```

### 4. Run the API
```sh
python app.py
```

### 5. Test the API with Postman or Curl
- **Postman**: Create a POST request to `http://localhost:5000/fetch_weather` with a JSON body:
  ```json
  {
      "venue_id": "1",
      "start_date": "2024-11-01",
      "end_date": "2024-11-02"
  }
  ```
- **Curl**:
  ```sh
  curl -X POST http://localhost:5000/fetch_weather -H "Content-Type: application/json" -d '{"venue_id": "1", "start_date": "2024-11-01", "end_date": "2024-11-02"}'
  ```

### 6. Deploy the API to AWS
- **Elastic Beanstalk** or **EC2**: Create an instance and deploy the code.
- Ensure security groups and VPC settings allow access to your database.


### 7. Apply QA Checks in SQL
- To ensure consistent data, create SQL checks to validate data quality.
- Example:
  ```sql
  -- Check for NULL values in critical columns
  SELECT * FROM Weather WHERE temperature IS NULL;

  -- Ensure datetime values are within expected range
  SELECT * FROM Weather WHERE datetime < '2024-11-01' OR datetime > '2024-11-02';
  ```
