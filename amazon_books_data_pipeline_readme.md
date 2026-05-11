# Data Pipeline for Amazon Books

## Overview

This project is an end-to-end ETL (Extract, Transform, Load) data pipeline designed for processing Amazon Books data using modern Data Engineering tools and practices.

The pipeline extracts book-related data from Amazon sources, transforms and cleans the data using Python and SQL, and loads the processed information into PostgreSQL for analytics and downstream applications.

The entire workflow is orchestrated using Apache Airflow and containerized with Docker for reproducibility and scalability.

---

## Architecture

![Pipeline Architecture](image.png)

### Pipeline Flow

1. **Extract**
   - Collect Amazon Books data from source systems/APIs/web scraping.
   - Raw data can include:
     - Book titles
     - Authors
     - Ratings
     - Reviews
     - Categories
     - Prices

2. **Transform**
   - Clean and normalize data using Python.
   - Apply SQL transformations.
   - Handle missing values and duplicates.
   - Convert raw data into structured analytical datasets.

3. **Load**
   - Store transformed data into PostgreSQL.
   - Make data available for analytics, dashboards, and machine learning workflows.

4. **Orchestration**
   - Apache Airflow manages scheduling and monitoring of ETL tasks.

5. **Containerization**
   - Docker ensures reproducible execution environments.

---

## Technologies Used

| Technology | Purpose |
|---|---|
| Python | Data extraction and transformation |
| SQL | Data querying and transformations |
| PostgreSQL | Data warehouse/storage |
| Apache Airflow | Workflow orchestration |
| Docker | Containerization |

---

## Project Structure

```text
Data-Pipeline-for-Amazon-Books/
│
├── dags/
│   └── etl_pipeline.py
│
├── scripts/
│   ├── extract.py
│   ├── transform.py
│   └── load.py
│
├── data/
│   ├── raw/
│   └── processed/
│
├── sql/
│   └── schema.sql
│
├── docker/
│
├── requirements.txt
├── docker-compose.yml
├── Dockerfile
├── .gitignore
├── README.md
└── LICENSE
```

---

## Features

- Automated ETL workflow
- Data extraction from Amazon Books source
- Data cleaning and preprocessing
- PostgreSQL integration
- Apache Airflow orchestration
- Dockerized environment
- Scalable and modular architecture

---

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/Data-Pipeline-for-Amazon-Books.git
cd Data-Pipeline-for-Amazon-Books
```

---

### 2. Create Virtual Environment

```bash
python -m venv venv
```

Activate environment:

#### Windows

```bash
venv\Scripts\activate
```

#### Linux / macOS

```bash
source venv/bin/activate
```

---

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

---

## Running with Docker

### Build Containers

```bash
docker-compose build
```

### Start Services

```bash
docker-compose up
```

---

## Airflow Setup

### Initialize Airflow Database

```bash
airflow db init
```

### Create Admin User

```bash
airflow users create \
    --username admin \
    --firstname Admin \
    --lastname User \
    --role Admin \
    --email admin@example.com
```

### Start Airflow Scheduler

```bash
airflow scheduler
```

### Start Airflow Webserver

```bash
airflow webserver --port 8080
```

Open:

```text
http://localhost:8080
```

---

## PostgreSQL Configuration

Example connection settings:

```env
POSTGRES_USER=postgres
POSTGRES_PASSWORD=password
POSTGRES_DB=amazon_books
POSTGRES_HOST=localhost
POSTGRES_PORT=5432
```

---

## Example ETL Workflow

### Extract

```python
# Example extraction step
import pandas as pd

books = pd.read_csv('books.csv')
```

### Transform

```python
# Example transformation
books.drop_duplicates(inplace=True)
books.fillna('Unknown', inplace=True)
```

### Load

```python
# Example load into PostgreSQL
from sqlalchemy import create_engine

engine = create_engine('postgresql://postgres:password@localhost:5432/amazon_books')
books.to_sql('books', engine, if_exists='replace')
```

---

## Future Improvements

- Real-time streaming pipeline
- AWS deployment
- Data quality monitoring
- Automated testing
- Dashboard integration
- Machine learning recommendation system
- Kafka integration
- Data lake support

---

## Use Cases

- Book recommendation systems
- Market analysis
- Customer review analytics
- Pricing analysis
- Sales forecasting
- NLP on customer reviews

---

## Screenshots

Add screenshots of:

- Airflow DAG execution
- PostgreSQL tables
- ETL logs
- Docker containers

---

## Contributing

Contributions are welcome.

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to your branch
5. Open a Pull Request

---

## License

This project is licensed under the MIT License.

---

## Author

Developed as a Data Engineering project focused on modern ETL pipeline architecture and scalable data processing.

