# Dockerized E-commerce Platform
This project is an e-commerce web application that has been containerized using Docker for easy deployment and scalability. It consists of two main components: a client-side application and a backend server. The application allows users to browse and purchase retail products, and it also provides functionality for administrators to add new products to the platform.

![Alt text](<explanation-images/yolo-demo.png>)

## Table of Contents

- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
- [Project Structure](#project-structure)
- [Docker Containers](#docker-containers)
- [Usage](#usage)
- [Customization](#customization)
- [Contributing](#contributing)
- [License](#license)

## Prerequisites

Before you can run this application, ensure that you have the following software and services installed:

- Node.js and npm: Make sure you have Node.js and npm (Node Package Manager) installed. You can download them from the official website: [Node.js](https://nodejs.org/).
- MongoDB: This application uses MongoDB as the database backend. You can either install MongoDB locally or use a cloud-based MongoDB service like MongoDB Atlas. Start the MongoDB service before running the application.
## Getting Started

Follow these steps to get the application up and running:

1. Clone the Repository:

Clone this repository to your local machine:

```bash

git clone https://github.com/The-Algorist/yolo.git

```

2. Navigate to the Client Folder:

```bash

cd client

```

3. Install Dependencies for the Client:

Install the required dependencies for the client-side application:

```bash

npm install

```

4. Start the Client Application:

Start the client-side application:

```bash

npm start

```

5. Open a New Terminal:

Open a new terminal window and navigate to the backend folder:

```bash

cd ../backend

```

6. Install Dependencies for the Backend:

Install the required dependencies for the backend server:

```bash

npm install

```

7. Start the Backend Server:

Start the backend server:

```bash

npm start

```

The application should now be up and running locally. You can access it in your web browser.

## Project Structure

The project is structured as follows:

- client: Contains the client-side React application.

- backend: Contains the backend server built with Node.js and Express.js.

- docker-compose.yml: Defines the Docker Compose configuration for running the application as Docker containers.

- Dockerfile (client): Specifies the Dockerfile for building the client-side container.

- Dockerfile (backend): Specifies the Dockerfile for building the backend server container.

## Docker Containers

The application has been containerized using Docker for easy deployment and management. There are two Docker containers: one for the client and one for the backend server. Docker Compose is used to orchestrate these containers.

### Client Container

- Base Image: Node.js Alpine

- Dockerfile: `Dockerfile.client`

- Exposed Port: 3000

### Backend Server Container

- Base Image: Node.js Alpine

- Dockerfile: `Dockerfile.backend`

- Exposed Port: 5000

## Usage

### Running with Docker Compose

To run the application using Docker Compose, follow these steps:

1. Make sure you have Docker and Docker Compose installed on your machine.

2. Navigate to the project root directory.

3. Run the following command to start the containers in detached mode:

```bash

docker-compose up -d

```

4. Access the application in your web browser at `http://localhost:3000`.

### Accessing the Containers

You can also access the running containers to inspect or debug them using the following commands:

- Client Container:

```bash

docker exec -it client-container-name sh

```

- Backend Server Container:

```bash

docker exec -it backend-container-name sh

```

Replace `client-container-name` and `backend-container-name` with the actual container names.

## Customization

You can customize the application by modifying the source code in the respective `client` and `backend` folders. Additionally, you can update the Dockerfiles and Docker Compose configuration to meet your specific requirements.

## Contributing

Contributions to this project are welcome. Feel free to open issues or pull requests if you have any suggestions, bug reports, or enhancements.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Open a new terminal and run the same commands in the backend folder
 `cd ../backend`

 `npm install`

 `npm start`

 ### Go ahead and add a product (note that the price field only takes a numeric input)
 ### Refresh to see the newly added product

 ### Here is a demo:<video src="explanation-images/yolo-demo.mp4" controls title="Title"></video>