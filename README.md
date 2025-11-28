# Weather ETL Pipeline

[![Airflow](https://img.shields.io/badge/Apache%20Airflow-2.10.0-blue?style=for-the-badge&logo=apache-airflow)](https://airflow.apache.org/)
[![Python](https://img.shields.io/badge/Python-3.10-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-15-336791?style=for-the-badge&logo=postgresql&logoColor=white)](https://www.postgresql.org/)
[![Docker](https://img.shields.io/badge/Docker-24.0.5-2496ED?style=for-the-badge&logo=docker&logoColor=white)](https://www.docker.com/)
[![Astro](https://img.shields.io/badge/Astro%20CLI-1.0-purple?style=for-the-badge)](https://www.astronomer.io/)

A robust ELT (Extract, Load, Transform) pipeline built with Apache Airflow on the Astro Runtime. This project extracts daily weather forecast data from the Open-Meteo API, transforms it, and loads it into a PostgreSQL database for analysis.

---

## Features

- **Automated Extraction**: Fetches daily weather data (temperature, wind speed, etc.) for specific coordinates.
- **Data Transformation**: Cleans and structures the raw API response.
- **Reliable Loading**: Inserts data into a PostgreSQL table (`weather_data`) with idempotency in mind.
- **Infrastructure as Code**: Fully containerized environment using Docker and Astro CLI.

## Tech Stack

- **Orchestration**: Apache Airflow
- **Language**: Python 3.10
- **Database**: PostgreSQL
- **API**: Open-Meteo
- **Deployment/Runtime**: Docker & Astro CLI

## Project Structure

```bash
.
├── dags/
│   ├── etl.py              # Main Weather ETL DAG
│   └── exampledag.py       # Example DAG (Reference)
├── include/                # SQL files and other assets
├── plugins/                # Custom Airflow plugins
├── tests/                  # Unit and integration tests
├── Dockerfile              # Astro Runtime configuration
├── packages.txt            # OS-level dependencies
├── requirements.txt        # Python dependencies
└── airflow_settings.yaml   # Local connections and variables
```

## Getting Started

### Prerequisites

- Docker Desktop
- Astro CLI

### Installation & Running

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/<your-username>/weather-etl.git
    cd weather-etl
    ```

2.  **Start the Airflow environment:**
    ```bash
    astro dev start
    ```
    *This will spin up the Airflow Webserver, Scheduler, Triggerer, and a local Postgres database.*

3.  **Access the UI:**
    - Open your browser to http://localhost:8080.
    - Log in with:
        - **Username**: `admin`
        - **Password**: `admin`

4.  **Trigger the DAG:**
    - Find `weather_etl_pipeline` in the DAGs list.
    - Toggle the switch to **ON**.
    - Click the **Play** button to trigger a manual run.
