# Food Delivery System (Like Zomato)

## Overview

This project implements a simplified food delivery system similar to Zomato, addressing the common challenges of traditional phone-based food ordering. It provides a platform to browse restaurants, place orders, track deliveries, and manage reviews, all within a centralized system.

## Problem Statement

Traditional food ordering methods often suffer from:

* **Limited Options:** Customers struggle to find diverse restaurant choices on a single platform.
* **Manual Errors:** Phone-based orders are prone to miscommunication and errors.
* **Lack of Tracking:** Customers lack real-time delivery tracking and estimated time information.
* **Payment Inefficiency:** Inefficient payment systems with no online tracking.
* **Decentralized Reviews:** Absence of a centralized review system for restaurants and dishes.

## Features

* **Restaurant Browsing:** Browse a variety of restaurants with cuisine and rating details.
* **Menu Display:** View restaurant menus with dish descriptions and prices.
* **Order Placement:** Place orders with multiple dishes.
* **Order Tracking:** Track order status and delivery progress.
* **User Reviews:** Provide ratings and comments for restaurants and dishes.
* **Admin Panel:** Manage restaurants, dishes, users, and orders.
* **Online Payment:** Payment system with transaction tracking.
* **Delivery Management:** Delivery personnel management and delivery tracking.

## Database Schema (MySQL)

The system utilizes a MySQL database with the following tables:

* **Restaurants:** Restaurant details (name, address, cuisine, rating, etc.).
* **Users:** User information (username, password, email, address, etc.).
* **Dishes:** Menu items (name, description, price, restaurant ID).
* **Orders:** Order details (user ID, restaurant ID, order time, total amount, status, payment ID, delivery ID).
* **Order\_Items:** Items within an order (order ID, dish ID, quantity).
* **Reviews:** Restaurant and dish reviews (user ID, restaurant ID, dish ID, rating, comment).
* **Payment:** Payment details (user ID, amount, payment method, transaction ID).
* **Delivery\_Personnel:** Delivery personnel information (name, phone, vehicle type).
* **Delivery:** Delivery details (order ID, delivery person ID, delivery address, delivery time, status).
* **Admins:** Admin user information (username, password, email, phone).

## Setup Instructions

1.  **Install MySQL:** Ensure you have MySQL installed and running.
2.  **Create Database:** Create a new database for the project.
3.  **Import Schema:** Execute the SQL schema script provided to create the tables.
4.  **Insert Sample Data:** Execute the insert scripts to populate the database with sample data.
5.  **Application Setup:** (If a web application is created) Setup your application with the database connection parameters.
6.  **Run the Application:** Start the application to begin using the food delivery system.

## Example Queries (MySQL)

* **View Restaurant Menu:**
    ```sql
    SELECT Dishes.name, Dishes.description, Dishes.price
    FROM Dishes
    WHERE Dishes.restaurant_id = 1;
    ```
* **View User Orders:**
    ```sql
    SELECT Orders.order_id, Restaurants.name, Orders.total_amount, Orders.status
    FROM Orders
    JOIN Restaurants ON Orders.restaurant_id = Restaurants.restaurant_id
    WHERE Orders.user_id = 1;
    ```
* **View Restaurant Reviews:**
    ```sql
    SELECT Users.username, Reviews.rating, Reviews.comment
    FROM Reviews
    JOIN Users ON Reviews.user_id = Users.user_id
    WHERE Reviews.restaurant_id = 1;
    ```
* **Top Rated Restaurants:**
    ```sql
    SELECT r.name, r.cuisine, AVG(rev.rating) AS average_rating
    FROM Restaurants r
    JOIN Reviews rev ON r.restaurant_id = rev.restaurant_id
    GROUP BY r.restaurant_id, r.name, r.cuisine
    ORDER BY average_rating DESC;
    ```

## Contributing

Contributions are welcome! Feel free to submit pull requests or open issues for bug fixes, feature requests, or improvements.

## License

This project is licensed under the [Your License] License. (Replace [Your License] with the appropriate license, e.g., MIT, Apache 2.0).
