# Sequence Diagrams for API Calls

## 1. User Registration

```mermaid
sequenceDiagram
    participant User
    participant API
    participant BusinessLogic
    participant Database

    User->>API: Register (first_name, last_name, email, password)
    API->>BusinessLogic: Validate and create user
    BusinessLogic->>Database: Check if email exists
    Database-->>BusinessLogic: Result
    alt Email already used
        BusinessLogic-->>API: Error
        API-->>User: 400 Email already registered
    else New email
        BusinessLogic->>Database: Save user
        Database-->>BusinessLogic: Confirm save
        BusinessLogic-->>API: Return new user
        API-->>User: 201 User created
    end
```

## 2. Place Creation

```mermaid
sequenceDiagram
    participant User
    participant API
    participant BusinessLogic
    participant Database

    User->>API: Create place (title, description, price, latitude, longitude)
    API->>BusinessLogic: Validate and create place
    alt Invalid data (e.g. negative price)
        BusinessLogic-->>API: Error
        API-->>User: 400 Invalid data
    else Valid data
        BusinessLogic->>Database: Save place
        Database-->>BusinessLogic: Confirm save
        BusinessLogic-->>API: Return new place
        API-->>User: 201 Place created
    end
```

## 3. Review Submission

```mermaid
sequenceDiagram
    participant User
    participant API
    participant BusinessLogic
    participant Database

    User->>API: Submit review (place_id, rating, comment)
    API->>BusinessLogic: Validate and create review
    BusinessLogic->>Database: Check that the place exists
    Database-->>BusinessLogic: Result
    alt Place not found
        BusinessLogic-->>API: Error
        API-->>User: 404 Place not found
    else Place found
        BusinessLogic->>Database: Save review
        Database-->>BusinessLogic: Confirm save
        BusinessLogic-->>API: Return new review
        API-->>User: 201 Review created
    end
```

## 4. Fetching a List of Places

```mermaid
sequenceDiagram
    participant User
    participant API
    participant BusinessLogic
    participant Database

    User->>API: Get places (criteria, e.g. max price)
    API->>BusinessLogic: Process request with criteria
    BusinessLogic->>Database: Get places matching criteria
    Database-->>BusinessLogic: List of places
    BusinessLogic-->>API: Return list of places
    API-->>User: 200 List of places
```

## How Each Layer Contributes

- **API (Presentation):** receives the request and sends back the response with a status code.
- **BusinessLogic:** applies the rules (unique email, valid price, existing place) and decides whether the request succeeds.
- **Database (Persistence):** saves and reads the data.