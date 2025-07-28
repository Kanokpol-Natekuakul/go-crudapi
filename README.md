# Go CRUD API

A simple RESTful API for managing books built with Go and Gorilla Mux router.

## Features

- Create, Read, Update, Delete (CRUD) operations for books
- RESTful API endpoints
- JSON response format
- In-memory data storage
- Book and Author data models

## Prerequisites

- Go 1.24.1 or higher
- Git (for cloning the repository)

## Installation

1. Clone the repository:
```bash
git clone https://github.com/Kanokpol-Natekuakul/go-crudapi.git
cd go-crudapi
```

2. Download dependencies:
```bash
go mod tidy
```

3. Run the application:
```bash
go run main.go
```

The server will start on port 8000.

## API Endpoints

### Base URL
```
http://localhost:8000
```

### Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/books` | Get all books |
| GET | `/api/books/{id}` | Get a specific book by ID |
| POST | `/api/books` | Create a new book |
| PUT | `/api/books/{id}` | Update an existing book |
| DELETE | `/api/books/{id}` | Delete a book |

## Data Models

### Book
```json
{
  "id": 1,
  "isbn": "12345",
  "title": "Go Programming",
  "author": {
    "firstname": "John",
    "lastname": "Doe"
  }
}
```

### Author
```json
{
  "firstname": "John",
  "lastname": "Doe"
}
```

## API Usage Examples

### Get all books
```bash
curl -X GET http://localhost:8000/api/books
```

### Get a specific book
```bash
curl -X GET http://localhost:8000/api/books/1
```

### Create a new book
```bash
curl -X POST http://localhost:8000/api/books \
  -H "Content-Type: application/json" \
  -d '{
    "id": 3,
    "isbn": "11111",
    "title": "Learning Go",
    "author": {
      "firstname": "Alice",
      "lastname": "Johnson"
    }
  }'
```

### Update a book
```bash
curl -X PUT http://localhost:8000/api/books/1 \
  -H "Content-Type: application/json" \
  -d '{
    "id": 1,
    "isbn": "54321",
    "title": "Updated Go Programming",
    "author": {
      "firstname": "John",
      "lastname": "Updated"
    }
  }'
```

### Delete a book
```bash
curl -X DELETE http://localhost:8000/api/books/1
```

## Sample Data

The application comes with two pre-loaded books:

1. **Go Programming** by John Doe (ID: 1, ISBN: 12345)
2. **Advanced Go** by Jane Smith (ID: 2, ISBN: 67890)

## Dependencies

- [Gorilla Mux](https://github.com/gorilla/mux) v1.8.1 - HTTP router and URL matcher

## Project Structure

```
go-crudapi/
├── main.go      # Main application file
├── go.mod       # Go module file
├── go.sum       # Go module checksum file
└── README.md    # This file
```

## Development

### Running the application
```bash
go run main.go
```

### Building the application
```bash
go build -o go-crudapi main.go
./go-crudapi
```

## Notes

- This API uses in-memory storage, so data will be lost when the server restarts
- For production use, consider implementing persistent storage (database)
- The API currently doesn't include input validation or error handling for edge cases
- CORS headers are not configured

