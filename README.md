# E-Commerce Database Management System

A relational, SQL-based database system designed to power a scalable e-commerce platform.  
This project demonstrates how to design, normalize, and implement an efficient backend to handle users, products, orders, and payments with full data integrity.

---

## 📘 Project Overview

**Title:** Database Design and Implementation of a Scalable E-Commerce System Using SQL  
**Course:** Database Management System (DBMS)  
**Institution:** Dhaka International University (DIU)

This system is designed for large-scale online stores that require secure transactions, multi-user management, product listings, cart systems, and payment tracking.

---

## 🎯 Objectives

- Design a **normalized relational database** for e-commerce operations.
- Ensure **data integrity, accuracy, and consistency**.
- Handle **users, vendors, products, carts, and orders** efficiently.
- Implement **secure and traceable** SQL-based transactions.
- Support **future scalability** for technologies like AI, AR, Blockchain, and microservices.

---

## 🧱 Entities & Relationships

### **1. Users**
| Attribute | Description |
|------------|-------------|
| user_id (PK) | Unique user identifier |
| user_name | Customer name |
| email | Unique email |
| address | Customer address |

### **2. Products**
| Attribute | Description |
|------------|-------------|
| product_code (PK) | Unique product identifier |
| product_name | Product name |
| category_name | Product category |
| price | Product price |

### **3. Cart**
| Attribute | Description |
|------------|-------------|
| cart_id (PK) | Unique cart ID |
| user_id (FK) | Linked user |
| product_code (FK) | Linked product |
| product_quantity | Quantity added |

### **4. Orders_Payments**
| Attribute | Description |
|------------|-------------|
| order_id (PK) | Unique order identifier |
| user_id (FK) | Linked customer |
| product_code (FK) | Linked product |
| total_items | Number of items |
| total_amount | Total purchase amount |

---

## 🗄️ SQL Schema (MySQL)

```sql
DROP DATABASE IF EXISTS D_87_Ecommerce;
CREATE DATABASE D_87_Ecommerce;
USE D_87_Ecommerce;

CREATE TABLE Users (
  user_id INT AUTO_INCREMENT PRIMARY KEY,
  user_name VARCHAR(50),
  address VARCHAR(150),
  email VARCHAR(50)
);

CREATE TABLE Products (
  product_code INT AUTO_INCREMENT PRIMARY KEY,
  product_name VARCHAR(100),
  category_name VARCHAR(100),
  price INT
);

CREATE TABLE Cart (
  cart_id INT AUTO_INCREMENT PRIMARY KEY,
  product_quantity INT,
  user_id INT,
  product_code INT,
  FOREIGN KEY (user_id) REFERENCES Users(user_id) ON DELETE CASCADE,
  FOREIGN KEY (product_code) REFERENCES Products(product_code) ON DELETE CASCADE
);

CREATE TABLE Orders_Payments (
  order_id INT AUTO_INCREMENT PRIMARY KEY,
  user_id INT,
  product_code INT,
  total_items INT,
  total_amount INT,
  FOREIGN KEY (user_id) REFERENCES Users(user_id) ON DELETE CASCADE,
  FOREIGN KEY (product_code) REFERENCES Products(product_code) ON DELETE CASCADE
);
🧮 Example Queries
Show all customers

sql
SELECT * FROM Users;
Display all products with categories

sql
SELECT product_name, category_name FROM Products;
Show all orders with customer names

sql
SELECT u.user_name, o.order_id, o.total_amount
FROM Orders_Payments o
JOIN Users u ON o.user_id = u.user_id;
Calculate total revenue

sql
SELECT SUM(total_amount) AS total_revenue FROM Orders_Payments;
🔮 Future Improvements
Partitioning large tables for faster query performance

Stored procedures for returns, cancellations, and reporting

Database auditing & logging for user actions

Dynamic reporting dashboards for business insights

Integration-ready schema for APIs and payment gateways

👨‍💻 Contributors
1.Abdullah Ibrahim - **https://github.com/Abdullah3d**
2.Md Nure Lokman
3.Tasnuba Tajvi
4.Shihab Sumik
