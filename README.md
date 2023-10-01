
                                
## Project Overview
The E-commerce API project is designed to support the operations of an online store, providing a comprehensive solution for managing users, products, addresses, and orders. This Spring-based E-commerce API allows you to manage users, products, addresses, and orders for an online store.

## Tech Stack
Before you begin, make sure you have the following tools and dependencies installed:

**Java Development Kit (JDK)**

**Languages & FrameWorks :** Java, SpringBoot

**Data Storage :** Data Base

**Tools Used :** IntelliJ, PostMan, Swagger

**Maven or Gradle (for project build management)**

## Documentation Dataflow

In this E-commerce API project, the data flows between different components as follows:


### User Management

- **Description**: Users are a fundamental part of the system, and they can be created with essential information.
- **Attributes**:
  - Name: The user's full name.
  - Email: The user's email address.
  - Password: The user's password for authentication.
  - Phone Number: The user's contact phone number.
- **Storage**: User data is securely stored in the database.

### Product Management

- **Description**: Products are the items available for purchase in the online store.
- **Attributes**:
  - Name: The name of the product.
  - Price: The price of the product.
  - Description: A brief description of the product.
  - Category: The category to which the product belongs.
  - Brand: The brand or manufacturer of the product.
- **Storage**: Product details are stored in the database and can be easily managed.

### Address Management

- **Description**: Addresses are crucial for order fulfillment and customer communication.
- **Attributes**:
  - Name: A user-defined name for the address (e.g., "Home," "Work").
  - Landmark: A notable landmark near the address.
  - Phone Number: The contact phone number associated with the address.
  - Zipcode: The postal code or ZIP code of the address.
  - State: The state or region where the address is located.
- **Association**: Addresses can be associated with specific users.
- **Storage**: Address information is stored in the database for easy retrieval.

### Order Placement

- **Description**: Users can place orders for products they wish to purchase.
- **Details**:
  - User ID: Identifies the user placing the order.
  - Product ID: Specifies the product to be ordered.
  - Address ID: Indicates the delivery address for the order.
  - Product Quantity: Specifies the quantity of the product to order.
- **Storage**: Order details are recorded in the database and linked to the respective user, product, and address.

## Data Flow Diagram



                            ┌─────────────────────────┐
                            │   E-commerce API        │
                            └───────────┬─────────────┘
                                        │
                                        ▼
                            ┌─────────────────────────┐
                            │       Controllers       │
                            └───────────┬─────────────┘
                                        │
                                        ▼
                            ┌─────────────────────────┐
                            │       Services          │
                            └───────────┬─────────────┘
                                        │
                                        ▼
                            ┌─────────────────────────┐
                            │       Repositories      │
                            └───────────┬─────────────┘
                                        │
                                        ▼
                            ┌─────────────────────────┐
                            │       Database          │
                            └─────────────────────────┘


This E-commerce API provides a comprehensive set of functionalities to facilitate the management of an online store, including user registration, product catalog management, address handling, and order processing.


## User API

### Create Users

- **Endpoint:** 
```
POST http://localhost:8080/api/users
```
- **Request:** Create one or more users.
- **Request Body:** List of user objects.
- **Validation:** Users' names, emails, passwords, and phone numbers are validated.
- **Response:** Returns a success message if users are created successfully.

## User Request Body

```
[
    {
        "id": 1,
        "name": "John Doe",
        "email": "john.doe@example.com",
        "password": "Password@123",
        "phoneNumber": "1234567890"
    },
    {
        "id": 2,
        "name": "Jane Smith",
        "email": "jane.smith@example.com",
        "password": "JaneS@321",
        "phoneNumber": "0987654321"
    }
]
```

## Product API

### Create Products

- **Endpoint:** 
```
POST http://localhost:8080/api/products
```
- **Request:** Create one or more products.
- **Request Body:** List of product objects.
- **Validation:** Product names, prices, and categories are validated.
- **Response:** Returns a success message if products are created successfully.

## Product Request Body
```
[
    {
        "id": 1,
        "name": "Smartphone",
        "price": 500,
        "description": "High-end smartphone with advanced features.",
        "category": "ELECTRONICS",
        "brand": "Samsung"
    },
    {
        "id": 2,
        "name": "T-Shirt",
        "price": 20,
        "description": "Comfortable cotton T-shirt for everyday wear.",
        "category": "CLOTHING",
        "brand": "Nike"
    }
]
```

### Get All Products

- **Endpoint:** 
```
GET http://localhost:8080/api/products
```
- **Request:** Retrieve a list of all products.
- **Response:** Returns a list of all products available.

### Get Products by Category

- **Endpoint:** 

```
GET http://localhost:8080/api/products/category
```
- **Request:** Retrieve products by specifying a category as a query parameter.
- **Query Parameter:** `category` (string)
- **Response:** Returns a list of products in the specified category.

### Delete Product

- **Endpoint:** 

```
DELETE http://localhost:8080/api/{productId}
```
- **Request:** Delete a product by its ID.
- **Path Parameter:** `productId` (integer)
- **Response:** Returns a success message if the product is deleted successfully.

## Address API

### Create Addresses

- **Endpoint:** 

```
POST http://localhost:8080/api/addresses
```
- **Request:** Create one or more addresses.
- **Request Body:** List of address objects.
- **Validation:** Addresses' names, phone numbers, zipcodes, and states are validated.
- **Response:** Returns a success message if addresses are created successfully.

## Address Request Body
```
[
    {
        "id": 1,
        "name": "John Doe",
        "landmark": "Near Park",
        "phoneNumber": "1234567890",
        "zipcode": "12345",
        "state": "California",
        "user": {
            "id": 1
        }
    },
    {
        "id": 2,
        "name": "Jane Smith",
        "landmark": "Next to Mall",
        "phoneNumber": "9876543210",
        "zipcode": "54321",
        "state": "New York",
        "user": {
            "id": 2
        }
    }
]
```


## Order API

### Place an Order

- **Endpoint:** 

```
POST http://localhost:8080/api/userId/productId/addressId/productQuantity
```
- **Request:** Place an order by specifying the user ID, product ID, address ID, and product quantity.
- **Request Body:** Order object with user ID, product ID, address ID, and product quantity.
- **Response:** Returns a success message if the order is placed successfully.

## Order request Body
```
{
  "id": 1,
  "users": [
    {
      "id": 1
    }
  ],
  "products": [
    {
      "id": 1
    },
{
      "id": 2
    }

  ],
  "addresses": [
    {
      "id": 1
    }
  ],
  "productQuantity": 2
}
```

### Get Order by Order ID

- **Endpoint:** 

```
GET http://localhost:8080/api/order/{orderId}
```
- **Request:** Retrieve an order by its ID.
- **Path Parameter:** `orderId` (integer)
- **Response:** Returns the order with the specified ID.

---

## Contributors

- **Pratik Sharma** : [thepratiksharma@gmail.com]()

We welcome contributions and feedback to improve and expand this project.

Contributions to this project are welcome! If you have suggestions, enhancements, or bug fixes, please open an issue or submit a pull request.


## Acknowledgments

Special thanks to the Spring Boot and Spring Data JPA communities for their excellent documentation and support. Please note that this README provides an overview of the API endpoints and their functionality. You can use tools like Postman or Swagger UI to interact with the API and test the endpoints in detail.
