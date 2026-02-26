# Product Inventory API

**Live Deployment:** https://e-commerce-api-jxpl.onrender.com  
**Postman Documentation:** https://documenter.getpostman.com/view/50839260/2sBXcGFLY8

A simple Express.js REST API for managing an e-commerce product catalog with full CRUD operations.

## Overview

This project provides a backend server for managing product inventory. It allows you to create, read, update, and delete products with support for filtering by category and updating individual product attributes like stock and price.

## Features

- ✅ Get all products
- ✅ Get product by ID
- ✅ Get products by category
- ✅ Create new products
- ✅ Update entire product details
- ✅ Update product stock
- ✅ Update product price
- ✅ CORS enabled for cross-origin requests

## Prerequisites

- Node.js (v12 or higher)
- npm (Node Package Manager)

## Installation

1. Clone or navigate to the project directory
2. Install dependencies:
   ```bash
   npm install
   ```

## Running the Server

Start the server with:

```bash
npm start
```

or

```bash
node index.js
```

The server will start on **http://localhost:3000**

## API Endpoints

### 1. Welcome Endpoint
```
GET /
```
Returns a welcome message.

**Response:**
```
Express server is running on 3000 port
```

### 2. Get All Products
```
GET /products
```
Returns an array of all products.

**Response (200 OK):**
```json
[
  {
    "id": 1,
    "name": "Wireless Mouse",
    "category": "Electronics",
    "price": 799,
    "stock": 25,
    "rating": 4.3
  },
  ...
]
```

### 3. Get Product by ID
```
GET /products/:id
```
Returns a single product by its ID.

**Example:** `GET /products/1`

**Response (200 OK):**
```json
{
  "id": 1,
  "name": "Wireless Mouse",
  "category": "Electronics",
  "price": 799,
  "stock": 25,
  "rating": 4.3
}
```

**Response (404 Not Found):**
```json
{
  "message": "Product not found"
}
```

### 4. Get Products by Category
```
GET /products/category/:categoryName
```
Returns all products in a specific category (case-insensitive).

**Example:** `GET /products/category/electronics`

**Response (200 OK):**
```json
[
  {
    "id": 1,
    "name": "Wireless Mouse",
    "category": "Electronics",
    "price": 799,
    "stock": 25,
    "rating": 4.3
  },
  {
    "id": 4,
    "name": "Smart Watch",
    "category": "Electronics",
    "price": 4999,
    "stock": 12,
    "rating": 4.4
  }
]
```

### 5. Create New Product
```
POST /products
```
Creates a new product and adds it to the inventory.

**Request Body:**
```json
{
  "name": "Product Name",
  "category": "Category",
  "price": 999,
  "stock": 10,
  "rating": 4.5
}
```

**Response (201 Created):**
```json
{
  "message": "Products created",
  "products": {
    "id": 6,
    "name": "Product Name",
    "category": "Category",
    "price": 999,
    "stock": 10,
    "rating": 4.5
  }
}
```

### 6. Update Entire Product
```
PUT /products/:id
```
Replaces all details of a product.

**Example:** `PUT /products/1`

**Request Body:**
```json
{
  "name": "Updated Product",
  "category": "Electronics",
  "price": 1299,
  "stock": 20,
  "rating": 4.6
}
```

**Response (200 OK):**
```json
{
  "message": "Product replaced successfully..!!",
  "product": {
    "id": 1,
    "name": "Updated Product",
    "category": "Electronics",
    "price": 1299,
    "stock": 20,
    "rating": 4.6
  }
}
```

**Response (404 Not Found):**
```json
{
  "message": "Products not found"
}
```

### 7. Update Product Stock
```
PUT /products/:id/stock
```
Updates only the stock quantity of a product.

**Example:** `PUT /products/1/stock`

**Request Body:**
```json
{
  "stock": 35
}
```

**Response (200 OK):**
```json
{
  "id": 1,
  "name": "Wireless Mouse",
  "category": "Electronics",
  "price": 799,
  "stock": 35,
  "rating": 4.3
}
```

### 8. Update Product Price
```
PUT /products/:id/price
```
Updates only the price of a product.

**Example:** `PUT /products/1/price`

**Request Body:**
```json
{
  "price": 899
}
```

**Response (200 OK):**
```json
{
  "id": 1,
  "name": "Wireless Mouse",
  "category": "Electronics",
  "price": 899,
  "stock": 25,
  "rating": 4.3
}
```

## Sample Data

The server comes pre-loaded with 5 sample products:

| ID | Name | Category | Price | Stock | Rating |
|---|---|---|---|---|---|
| 1 | Wireless Mouse | Electronics | 799 | 25 | 4.3 |
| 2 | Running Shoes | Footwear | 2499 | 40 | 4.5 |
| 3 | Laptop Stand | Accessories | 999 | 30 | 4.2 |
| 4 | Smart Watch | Electronics | 4999 | 12 | 4.4 |
| 5 | Backpack | Fashion | 1599 | 50 | 4.1 |

## Project Structure

```
nodeAss.02/
├── index.js          # Main server file
├── package.json      # Project dependencies
└── README.md         # This file
```

## Dependencies

- **express** - Fast, unopinionated web framework for Node.js
- **cors** - Enable Cross-Origin Resource Sharing

## Technologies Used

- Node.js
- Express.js
- JavaScript (ES6+)

## Notes

- All data is stored in memory (no persistent database)
- Data will be reset when the server restarts
- Product IDs are auto-generated based on array length

## Future Improvements

- Add database integration (MongoDB, PostgreSQL)
- Implement authentication and authorization
- Add input validation and error handling
- Add pagination for product listings
- Implement delete product endpoint
- Add product search functionality
- Add unit and integration tests

## License

This project is open source and available under the MIT License.

## Author

Created as a Node.js learning exercise.
