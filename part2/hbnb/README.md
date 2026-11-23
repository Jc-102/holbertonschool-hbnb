# HBnB Evolution — Part 2: Business Logic and API

## Description

This part implements the Presentation and Business Logic layers of HBnB using Python, Flask and flask-restx. Data is stored in memory for now; a database will replace it in Part 3.

## Project Structure

```
hbnb/
├── app/
│   ├── api/v1/        # Presentation layer: API endpoints (users, places, reviews, amenities)
│   ├── models/        # Business logic layer: User, Place, Review, Amenity classes
│   ├── services/      # Facade: single entry point between the API and the business logic
│   └── persistence/   # Persistence layer: in-memory repository (database in Part 3)
├── run.py             # Starts the application
├── config.py          # App settings
└── requirements.txt   # Python packages needed
```

## Installation

```
pip install -r requirements.txt
```

## Run

```
python run.py
```

The API documentation is available at http://127.0.0.1:5000/api/v1/