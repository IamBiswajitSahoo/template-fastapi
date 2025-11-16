
# FastAPI Template Project

This is a scalable FastAPI template project with a modular structure, ready for production and testing.

## Project Structure

```
template-fastapi/
├── app/
│   ├── main.py              # FastAPI app entry point
│   ├── api/
│   │   └── v1/
│   │       └── user.py      # User API routes
│   ├── core/
│   │   ├── config.py        # App configuration (env, settings)
│   │   └── logging.py       # Logging setup
│   ├── db/
│   │   └── schema.py        # SQLAlchemy models and DB session
│   ├── models/
│   │   └── user.py          # Pydantic models for User
│   └── services/
│       └── user_service.py  # Business logic for User
├── tests/
│   ├── test_db.py           # Test DB setup
│   └── api/
│       └── v1/
│           └── test_user.py # User API tests
├── pyproject.toml           # Project dependencies and config
├── Dockerfile               # Docker image definition
├── docker-compose.yaml      # Multi-container orchestration
├── .gitignore               # Git ignore rules
└── README.md                # Project documentation
```

## Folder & Script Purpose

- `app/main.py`: Starts the FastAPI application and registers routes.
- `app/api/v1/user.py`: Defines REST endpoints for user operations.
- `app/core/config.py`: Loads environment variables and app settings.
- `app/core/logging.py`: Configures logging for the app.
- `app/db/schema.py`: Contains SQLAlchemy DB models and session setup.
- `app/models/user.py`: Pydantic models for request/response validation.
- `app/services/user_service.py`: Implements business logic for user CRUD.
- `tests/`: Contains all test cases and test DB setup.
- `pyproject.toml`: Lists all dependencies and project metadata.
- `Dockerfile` & `docker-compose.yaml`: For containerization and orchestration.

## Installation & Setup

1. **Clone the repository:**
     ```sh
     git clone https://github.com/IamBiswajitSahoo/template-fastapi.git
     cd template-fastapi
     ```

2. **Install dependencies:**
     - For local development:
          ```sh
          pip install -e .
          ```
          Or use Poetry:
          ```sh
          poetry install
          ```
     - For Docker usage: dependencies are installed automatically with `uv sync` during the build process. No manual step needed.

3. **Run the server:**
     ```sh
     uvicorn app.main:app --reload
     ```

4. **Run tests:**
     ```sh
     pytest
     ```

5. **Docker usage:**
     Build and run with Docker Compose:
     ```sh
     docker-compose up --build
     ```

## Example API Usage

Interact with the API (default at http://localhost:8000):

### Create a User
```sh
curl -X POST "http://localhost:8000/api/v1/users" \
       -H "Content-Type: application/json" \
       -d '{"name": "Ada Lovelace"}'
```

### Get All Users
```sh
curl -X GET "http://localhost:8000/api/v1/users"
```

### Get a User by ID
```sh
curl -X GET "http://localhost:8000/api/v1/users/1"
```

### Update a User
```sh
curl -X PUT "http://localhost:8000/api/v1/users/1" \
       -H "Content-Type: application/json" \
       -d '{"name": "Grace Hopper"}'
```

### Delete a User
```sh
curl -X DELETE "http://localhost:8000/api/v1/users/1"
```

## Notes

- Environment variables can be set in a `.env` file.
- Database uses SQLite by default (see `app/core/config.py`).
- All business logic is separated into service classes for scalability.
- Tests use an in-memory SQLite database for isolation.

---
For questions or contributions, open an issue or pull request!