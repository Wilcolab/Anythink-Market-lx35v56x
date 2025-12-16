# Anythink-Market

This project provides a task management API implemented in both Python (FastAPI) and Node.js (Express) for comparison and migration purposes. Both servers offer identical functionality with in-memory task storage.

## Project Structure

The project has the following files and directories:

- `python-server/`: Python implementation using FastAPI.
  - `src/main.py`: FastAPI application with task management routes.
  - `src/__init__.py`: Marks the `src` directory as a Python package.
  - `requirements.txt`: Python dependencies (FastAPI, Pydantic, Uvicorn).
  - `Dockerfile`: Docker image for the Python server.

- `express-server/`: Node.js implementation using Express.
  - `src/app.js`: Express application with task management routes.
  - `package.json`: Node.js dependencies (Express, Nodemon).
  - `Dockerfile`: Docker image for the Node.js server.

- `docker-compose.yml`: Defines and orchestrates both services using Docker Compose.

## Getting Started

### Using Docker Compose (Recommended)

To run both servers simultaneously:

```shell
docker compose up
```

- Python server: http://localhost:8000
- Node.js server: http://localhost:8001

### Running Individually

#### Python Server

**Prerequisites**: Python 3.8 or higher.

**Installation**:
```shell
cd python-server
pip install -r requirements.txt
```

**Server Startup**:
```shell
uvicorn src.main:app --reload --port 8000
```

#### Node.js Server

**Prerequisites**: Node.js 14 or higher, Yarn package manager.

**Installation Instructions**:
```shell
cd express-server
yarn install
```

**Server Startup Commands**:
For development with auto-reload:
```shell
yarn start
```

For production:
```shell
node src/app.js
```

## API Routes

Both servers provide identical API endpoints:

- `GET /`: Returns "Hello World"
- `POST /tasks`: Adds a new task. Request body: `{"text": "task description"}`. Response: `{"message": "Task added successfully"}`
- `GET /tasks`: Retrieves all tasks. Response: `{"tasks": ["task1", "task2", ...]}`

## Migration Notes

If transitioning from the Python server to the Node.js server:

- **Environment Setup**: Install Node.js (v14+) and Yarn instead of Python. No specific version lock yet, but ensure compatibility with Express 4.x.
- **Dependencies**: Replace `pip install -r requirements.txt` with `yarn install`. Dependencies are minimal (Express for routing, Nodemon for development).
- **Server Startup**: Use `yarn start` (which runs `nodemon src/app.js` for auto-reload) or `node src/app.js` directly, instead of `uvicorn src.main:app --reload`.
- **Code Differences**: 
  - Request parsing: Express requires `app.use(express.json())` middleware; FastAPI handles JSON automatically with Pydantic models.
  - Routing: Express uses `app.get/post()`; FastAPI uses decorators like `@app.get()`.
  - No changes needed for in-memory data (global `tasks` array).
- **Configuration**: Update any scripts or tools to point to port 8001 instead of 8000. No database or external services to migrate.
- **Testing**: Endpoints behave identically; use the same curl/Postman requests for validation.
