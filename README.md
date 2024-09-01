# E-Commerce Back End

## Description

This is the back end for an e-commerce site that allows you to manage products, categories, and tags. The app is built using Express.js, Sequelize, and PostgreSQL. It supports basic CRUD operations through a RESTful API, making it easy to manage the product catalog.

## Table of Contents

- [Installation](#installation)
- [Usage](#usage)
- [Database Models](#database-models)
- [Routes](#routes)
- [Walkthrough Video](#walkthrough-video)
- [License](#license)

## Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/AhmedGarcia/E-Commerce-app.git
   ```

2. Navigate to the project directory:

   ```bash
   cd e-commerce-app
   ```

3. Install the necessary dependencies:

   ```bash
   npm install
   ```

4. Create a new `.env` file in the root directory and add your PostgreSQL database credentials:

   ```plaintext
   DB_NAME='ecommerce_db'
   DB_USER='your_postgres_username'
   DB_PASSWORD='your_postgres_password'
   ```

5. Create the database schema using PostgreSQL:

   ```bash
   psql -U postgres
   \i db/schema.sql
   \q
   ```

6. Seed the database:

   ```bash
   npm run seed
   ```

7. Start the server:

   ```bash
   npm start
   ```

## Usage

Once the server is running, you can use a tool like `Insomnia` to interact with the API. The server will be running on `http://localhost:3001.`

## Example Requests

* Get all categories:
  
  ```http
  GET http://localhost:3001/api/categories
  ```

* Create a new product:

  ```http
  POST http://localhost:3001/api/products
  Body: {
   "product_name": "New Product",
   "price": 25.99,
   "stock": 100,
   "category_id": 1,
   "tagIds": [1, 2]
   }
  ```

* Update Tag:

  ```http
  PUT http://localhost:3001/api/tags/1
  Body: {
   "tag_name": "Updated Tag"
  }
  ```

* Delete category

  ```http
  DELETE http://localhost:3001/api/categories/1
  ```

## Database Models

### Category

* `id`: Integer, primary key, auto-increment, not null.

* `category_name`: String, not null.

### Product

* `id`: Integer, primary key, auto-increment, not null.

* `product_name`: String, not null.

* `price`: Decimal, not null.

* `stock`: Integer, default value 10, not null.

* `category_id`: Integer, references `Category` model's `id`.

### Tag

 * `id`: Integer, primary key, auto-increment, not null.

* `tag_name`: String.

### PoductTag

* `id`: Integer, primary key, auto-increment, not null.

* `product_id`: Integer, references
`Product` model's `id`.

* `tag_id`: Integer, references `Tag` model's `id`.

## Routes

### Category Routes

* `GET /api/categories`: Get all categories.

* `GET /api/categories/:id`: Get a single category by ID.

* `POST /api/categories`: Create a new category.

* `PUT /api/categories/:id`: Update a category by ID.

* `DELETE /api/categories/:id`: Delete a category by ID.

### Product Routes

* `GET /api/products`: Get all products.

* `GET /api/products/:id`: Get a single product by ID.

* `POST /api/products`: Create a new product.

* `PUT /api/products/:id`: Update a product by ID.

* `DELETE /api/products/:id`: Delete a product by ID.

### Tag Routes

* `GET /api/tags`: Get all tags.

* `GET /api/tags/:id`: Get a single tag by ID.

* `POST /api/tags`: Create a new tag.

* `PUT /api/tags/:id`: Update a tag by ID.

* `DELETE /api/tags/:id`: Delete a tag by ID.

## Walkthrough Video

A walkthrough video demonstrating the functionality of the application, including the creation of the schema, seeding the database, and testing the routes in Insomnia, can be found [here](#).

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.