# HBnB Evolution

A simplified AirBnB-like application built step by step at Holberton School.

## About

HBnB Evolution lets users:
- **Manage users:** register, update their profile, and be regular users or admins
- **Manage places:** list properties with a title, description, price and location
- **Manage reviews:** rate and comment on places
- **Manage amenities:** add features (like Wi-Fi or a pool) to places

## Architecture

The app uses a **three-layer architecture**:
- **Presentation Layer:** the API that users interact with
- **Business Logic Layer:** the models and the rules of the app
- **Persistence Layer:** stores and retrieves data from the database

The layers communicate through a **facade**, a single entry point into the business logic.

## Project Parts

| Part | Description |
|---|---|
| [Part 1](./part1) | Technical documentation: UML diagrams of the architecture and design |
| Part 2 | Implementation of the business logic and the API |
| Part 3 | Authentication and database integration |
| Part 4 | Web client (front end) |

## Author

- Jean Carlos Jimenez Nevarez