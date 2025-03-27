# calculator as api
A Node.js-based project designed to demonstrate practical implementation of server-side programming concepts. This project includes multiple endpoints to showcase various functionalities.
## Prerequisites
- Node.js installed on your system.
## Tools Required
- Git: [Download Git](https://github.com)
- Visual Studio Code: [Download VS Code](https://code.visualstudio.com/)
- Node.js: [Download Node.js](https://nodejs.org/en/download/)
## Project Overview
This project is a simple calculator microservice built using Node.js and Express. It provides basic arithmetic operations (addition, subtraction, multiplication, division) through RESTful API endpoints. The microservice also includes error handling and logging for better development and debugging.
## Steps to Build the Project
1. **Set Up the Environment**:
     - Install Node.js from the [official website](https://nodejs.org/en/download/).
     - Install Git and clone the repository using `git clone <repository-url>`.
3. **Install Dependencies**:
     - Navigate to the project directory.
     - Run `npm install` to install the required dependencies, including `express` and `winston`.
5. **Create the Server**:
     - Use Express to set up a server listening on port 3000.
     - Define routes for arithmetic operations (`/add`, `/subtract`, `/multiply`, `/divide`).
6. **Implement Logging**:
     - Use the Winston library for logging.
     - Configure Winston to log errors and combined logs into separate files in the `logs` directory.
7. **Add Error Handling**:
     - Validate input parameters for each endpoint.
     - Handle division by zero and other invalid inputs gracefully.
     - Implement a global error handler to catch unexpected errors.
  8. **Run the Application**:
     - Start the server using `node index.js`.
     - Access the endpoints via `http://localhost:3000`.
## Features
- Four API endpoints for arithmetic operations: addition, subtraction, multiplication, and division.
- Error handling to validate input parameters and provide meaningful error messages.
- Logging using Winston to track requests and responses for troubleshooting and monitoring.
## API Endpoints
### GET /add
- **Description**: Adds two numbers.
- **Query Parameters**: `num1` and `num2` (both required).
- **Response**: Returns the sum of the two numbers.
- **Example**:
  
```
  curl "http://localhost:3000/add?num1=5&num2=3"
```
  **Response**:
```
  {
     "result": 8
  }
```
### GET /subtract
- **Description**: Subtracts the second number from the first.
- **Query Parameters**: `num1` and `num2` (both required).
- **Response**: Returns the result of the subtraction.
- **Example**:
```bash
  curl "http://localhost:3000/subtract?num1=10&num2=4"
```
  **Response**:

```json
  {
     "result": 6
  }
```
### GET /multiply
- **Description**: Multiplies two numbers.
- **Query Parameters**: `num1` and `num2` (both required).
- **Response**: Returns the product of the two numbers.
- **Example**:
```bash
  curl "http://localhost:3000/multiply?num1=7&num2=6"
```
  **Response**:
```json
  {
     "result": 42
  }
```
### GET /divide
- **Description**: Divides the first number by the second.
- **Query Parameters**: `num1` and `num2` (both required).
- **Response**: Returns the result of the division or an error if division by zero is attempted.
- **Example**:
```bash
  curl "http://localhost:3000/divide?num1=20&num2=4"
 ```
  **Response**:
```json
  {
     "result": 5
  }
```
## Logging
This project uses the Winston library for logging. Logs include details about each request, such as the IP address, request method, URL, headers, and response status. Logs are stored in the `logs` directory with separate files for errors and combined logs.
### Example Log Configuration

```javascript
const winston = require('winston');
const logger = winston.createLogger({
     level: 'info',
     format: winston.format.json(),
     defaultMeta: { service: 'calculator-microservice' },
     transports: [
          new winston.transports.Console({
                format: winston.format.simple(),
          }),
          new winston.transports.File({ filename: 'logs/error.log', level: 'error' }),
          new winston.transports.File({ filename: 'logs/combined.log' }),
     ],
});
```
### Example Log Output

- **Info Log**:
```
  info: Addition requested: 5 + 3 = 8
```
- **Error Log**:
```
  error: Invalid input for division
```
- **Division by Zero Log**:
```
  error: Division by zero attempt
```
## Running the Application
1. Start the server:
```bash
    node index.js
```
2. Access the endpoints using a browser, Postman, or `curl`.
3. Monitor logs in the `logs` directory for debugging and analysis.
