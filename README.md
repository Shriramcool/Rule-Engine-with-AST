# Rule Engine Application

## Project Overview

Introducing the **Rule Engine Application** sophisticated solution built on a dynamic 3-tier architecture that empowers users to create, combine, modify, and evaluate eligibility rules. This application intelligently handles attributes such as age, department, income, salary, and experience to deliver personalized assessments.

At its core, the Rule Engine utilizes an **Abstract Syntax Tree (AST)** to efficiently parse and evaluate intricate, nested rules, ensuring quick and accurate processing. The **frontend** is crafted with React for a responsive user experience, while the **backend** is powered by Node.js and Express.js for seamless performance. Data management is handled through MongoDB, providing a reliable and scalable **database** solution.

This full-stack application not only streamlines rule management but also enhances decision-making capabilities through its intuitive interface and robust architecture.
## Features

### Core Features

- **Rule Creation**: Users can easily define individual rules using logical expressions, such as `age > 30 AND department = 'Sales'`.
- **Rule Combination**: Multiple individual rules can be seamlessly combined into a single logical Abstract Syntax Tree (AST) for more complex evaluations.
- **Rule Evaluation**: Created or combined rules can be evaluated against user data to assess eligibility accurately.
- **RESTful API**: The backend provides a comprehensive set of APIs for creating, modifying, deleting, and evaluating rules, ensuring efficient data interaction.

### Bonus Features Implemented

- **Robust Error Handling**: The application effectively manages invalid rule strings, missing data, and other potential errors, ensuring a smooth user experience.
- **Soft Deletion**: Rules can be marked as deleted without permanently removing them from the database, allowing for easy restoration if needed.
- **Attribute Validation**: The system verifies that only valid attributes are used in rule definitions, maintaining data integrity and accuracy.

## Technologies and Dependencies

- **Frontend**: React, Axios
- **Backend**: Node.js, Express.js, Mongoose
- **Database**: MongoDB Atlas
- **Others**: Docker (optional, for containerization)

### Dependencies

- **Node.js** (v14+)
- **MongoDB Atlas** account (or local MongoDB installation)
- **npm** for managing packages
- **Docker** (optional, for containerization)

## Installation and Setup

### Prerequisites

Ensure you have the following installed:

- **Node.js** and **npm**
- **MongoDB** (or access to MongoDB Atlas)
- **Git**
- (Optional) **Docker** for containerization

### Steps to Run the Project

1. **Clone the Repository**:

   ```bash
   git clone https://github.com/yourusername/rule-engine-with-ast.git
   cd rule-engine-with-ast
   ```

2. **Backend Setup**:

   ```bash
   cd backend
   npm install
   ```

   Create a `.env` file in the `backend` directory and add the MongoDB connection string:

   ```
   MONGO_URI=mongodb+srv://<username>:<password>@cluster0.mongodb.net/rule-engine?retryWrites=true&w=majority
   ```

   Start the server:

   ```bash
   node server.js
   ```

3. **Frontend Setup**:
   Open a new terminal and run the following commands:

   ```bash
   cd frontend
   npm install
   npm run dev
   ```

   The frontend should now be running on `http://localhost:5173`.

4. **(Optional) Docker Setup**:
   - To run the backend in a Docker container, use the provided `Dockerfile`.
   ```bash
   docker build -t rule-engine-backend .
   docker run -p 5000:5000 rule-engine-backend
   ```

## API Overview

- **POST /api/rules/create**: Create a new rule.
- **POST /api/rules/combine**: Combine multiple rules.
- **POST /api/rules/evaluate**: Evaluate a rule with given user data.
- **GET /api/rules**: Get all rules (excluding soft-deleted ones).
- **PUT /api/rules/:id**: Update an existing rule.
- **DELETE /api/rules/soft-delete/:id**: Soft delete a rule.
- **PATCH /api/rules/restore/:id**: Restore a soft-deleted rule.

## Usage Guide

### Creating a Rule

- Open the app in your browser (`http://localhost:5173`).
- Navigate to the **Create Rule** section.
- Enter a rule name and a logical expression (e.g., `age > 30 AND department = 'Sales'`).
- Click **Create Rule**.

### Viewing Rules

- Scroll down to see all existing rules listed under **Rules List**.

### Evaluating a Rule

- Go to the **Evaluate Rule** section.
- Select a rule from the dropdown.
- Provide the relevant user data (e.g., `age`, `department`, etc.).
- Click **Evaluate Rule** to get the result (`True` or `False`).

## Design Decisions

- **Abstract Syntax Tree (AST)**: The AST was chosen for flexibility in representing rules and evaluating complex logic.
- **MongoDB**: A NoSQL database like MongoDB is ideal for the flexibility of storing nested rule structures.
- **React and Node.js**: A modern stack that allows for quick development of full-stack web applications.

## Testing Instructions

### Manual Testing

- **Create Rules**: Test the rule creation with various attributes and conditions.
- **Combine Rules**: Combine different rules to verify the AST is correctly structured.
- **Evaluate Rules**: Provide sample user data to evaluate whether the rule conditions are met.
- **Error Handling**: Test with invalid rules or missing fields to ensure proper error responses.

### Testing with Postman

- You can use Postman to directly call the APIs.
- Import the following example JSON body to test rule creation:
  ```json
  {
    "name": "Sales Department Age Rule",
    "ruleString": "age > 30 AND department = 'Sales'"
  }
  ```

## Troubleshooting

- **CORS Errors**: If you encounter CORS issues, verify that the backend is configured to allow requests from the frontend origin (`http://localhost:5173`).
- **MongoDB Connection Problems**: Ensure that the `.env` file contains the correct MongoDB URI to establish a successful connection.
- **Frontend-Backend Connection**: Confirm that the backend server (`http://localhost:5000`) is running before starting the frontend application to ensure proper connectivity.

