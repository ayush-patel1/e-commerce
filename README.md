# Go E-Commerce Backend

**A RESTful E-Commerce Backend built with Golang and MongoDB**

Developed by **Ayush Patel**

A backend project built using Go (Golang) and MongoDB that provides core e-commerce functionality, including user authentication, product management, product search, shopping carts, address management, and order placement.

## Tech Stack

- **Language:** Go (Golang)
- **Database:** MongoDB
- **Containerization:** Docker & Docker Compose
- **API Testing:** Postman or any HTTP client
- **Authentication:** JWT-based authentication

## Features

- User registration and login
- Password hashing
- Token-based authentication
- Product creation and product listing
- Product search using regular expressions
- Add and remove products from the shopping cart
- View cart items and calculate the total price
- Add, edit, and delete delivery addresses
- Checkout and order placement
- Buy products instantly

## Getting Started

### Prerequisites

Ensure you have the following installed:

- [Go](https://go.dev/dl/)
- [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- [Git](https://git-scm.com/)

### Installation

Clone the repository:

```bash
git clone https://github.com/ayush-patel1/e-commerce.git
cd e-commerce
```

Start the required Docker services:

```bash
docker-compose up -d
```

Run the application:

```bash
go run main.go
```

The API server runs at:

`http://localhost:8000`

## API Documentation

All endpoints below use the local development server at `http://localhost:8000`.

### 1. User Authentication

#### Sign Up

**POST** `/users/signup`

Register a new user.

Request body:

```json
{
  "first_name": "Ayush",
  "last_name": "Patel",
  "email": "ayush@example.com",
  "password": "your_password",
  "phone": "+910000000000"
}
```

Expected response:

```text
Successfully Signed Up!!
```

#### Login

**POST** `/users/login`

Authenticate an existing user.

Request body:

```json
{
  "email": "ayush@example.com",
  "password": "your_password"
}
```

The response includes user information and authentication tokens. Exact response fields depend on the implementation.

### 2. Product Management

#### Add Product (Admin)

**POST** `/admin/addproduct`

Add a product to the database.

Request body:

```json
{
  "product_name": "Laptop",
  "price": 2500,
  "rating": 10,
  "image": "laptop.jpg"
}
```

Expected response:

```text
Successfully added our Product Admin!!
```

#### View All Products

**GET** `/users/productview`

Retrieve the available products from the database.

Example response:

```json
[
  {
    "Product_ID": "product_id",
    "product_name": "Laptop",
    "price": 2500,
    "rating": 10,
    "image": "laptop.jpg"
  }
]
```

#### Search Products

**GET** `/users/search?name=lap`

Search for products by name using the implemented regular-expression query.

### 3. Shopping Cart

#### Add Product to Cart

**GET** `/addtocart?id=PRODUCT_ID&userID=USER_ID`

Add a product to a user's shopping cart.

#### Remove Product from Cart

**GET** `/removeitem?id=PRODUCT_ID&userID=USER_ID`

Use the actual registered route in the source code; verify whether the implementation uses `/addtocart` for removal as well.

#### View Cart and Total Price

**GET** `/listcart?id=USER_ID`

Retrieve the cart items and their total price.

### 4. Address Management

#### Add Address

**POST** `/addadress?id=USER_ID`

Request body:

```json
{
  "house_name": "Example House",
  "street_name": "Example Street",
  "city_name": "Raipur",
  "pin_code": "492001"
}
```

The documented implementation supports up to two addresses per user: home and work.

#### Edit Home Address

**PUT** `/edithomeaddress?id=USER_ID`

Update the user's home address.

#### Edit Work Address

**PUT** `/editworkaddress?id=USER_ID`

Update the user's work address.

#### Delete Addresses

**GET** `/deleteaddresses?id=USER_ID`

Delete the user's saved addresses.

### 5. Checkout and Orders

#### Checkout and Place Order

**GET** `/?id=USER_ID`

Place an order using the user's cart. The documented behavior clears the cart after checkout.

#### Buy a Product Instantly

**GET** `/?userid=USER_ID&pid=PRODUCT_ID`

Purchase a specific product directly.

> **Note:** Confirm the exact checkout and instant-purchase routes in the source code before using these endpoints. The original API documentation does not specify distinct paths for these operations.

## Project Structure

The exact directory structure depends on the repository. A typical Go backend may contain:

```text
e-commerce/
├── main.go
├── docker-compose.yml
├── go.mod
├── go.sum
├── controllers/
├── models/
├── routes/
└── database/
```

## Running with Docker

Start the configured services:

```bash
docker-compose up -d
```

Stop them when finished:

```bash
docker-compose down
```

Ensure MongoDB is configured correctly and accessible to the Go application before starting the server.

## Future Improvements

- Add comprehensive request validation
- Introduce role-based authorization for admin routes
- Use HTTP methods appropriate to each operation
- Add pagination and filtering for product listings
- Implement automated unit and integration tests
- Add structured logging and centralized error handling
- Add API documentation using Swagger/OpenAPI

## Author

**Ayush Patel**

- GitHub: [@ayush-patel1](https://github.com/ayush-patel1)
- Portfolio: [ayush-patel-dev.vercel.app](https://ayush-patel-dev.vercel.app/)

---

*Built with Go and MongoDB to explore backend development and core e-commerce workflows.*
