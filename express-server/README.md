# Express Server Project

This project is a simple Express server that listens on port 8001. It is set up to use Nodemon for automatic code reloading during development.

## Project Structure

```
express-server
├── src
│   └── app.js
├── package.json
├── Dockerfile
└── README.md
```

## Getting Started

To get started with this project, follow the instructions below.

### Prerequisites

Make sure you have the following installed:

- Node.js
- Yarn
- Docker (if you want to run the server in a container)

### Installation

1. Clone the repository:

   ```
   git clone https://github.com/Wilcolab/Anythink-Market-lx35v56x.git
   cd Anythink-Market-lx35v56x/express-server
   ```

2. Install the dependencies:

   ```
   yarn install
   ```

### Running the Server

To run the server in development mode with automatic reloading, use:

```
yarn start
```

The server will be available at `http://localhost:8001`.

### Building the Docker Image

To build the Docker image, run:

```
docker build -t express-server .
```

### Running the Docker Container

To run the Docker container, use:

```
docker run -p 8001:8001 express-server
```

The server will be accessible at `http://localhost:8001` from your host machine.