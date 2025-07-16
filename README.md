# 🍽️ Restaurant Management Database System

An end-to-end **SQL-based database management system** designed for a modern restaurant environment. This project models the operational and analytical workflows of a restaurant, combining customer ordering, employee assignment, inventory tracking, invoicing, and delivery logistics into one robust MySQL solution.

---

## 📘 Project Overview

This project was developed for **Farmer’s Restaurant**, a hypothetical business seeking to digitize operations and move away from manual tracking. The database is built using **MySQL** and designed to support:

- Live menu availability
- Customer order management (online + in-person)
- Invoice and payment tracking
- Ingredient and vendor inventory
- Area code-based delivery logic

---

## 🧠 Key Features

- 11 fully normalized entities with defined relationships
- Support for **multi-channel customer orders** (dine-in & online)
- Efficient **area code-based employee assignment** for delivery
- Normalized ingredient tracking with vendor-to-chef mapping
- Sample **SQL test queries** to analyze sales, customers, orders, and delivery behavior

---

## 🗂️ Schema Design

- `Customer`, `Cus_order`, `Invoice`, `Payment_transaction`
- `Meals`, `Drinks`, `Ingredients`, `Vendor`, `Executive_Chef`
- `Employee`, `Areacode`

📄 See full schema and relationships in [`Technical Report`](./Technical%20Report_%20Restaurant%20Management%20Database.pdf)  
🧾 Business logic is detailed in [`Business Rules`](./Business%20Rules%20.pdf)

---

## 🛠 Technologies Used

- **MySQL** for schema creation and querying
- **ER modeling** (Conceptual, Logical, and Physical)
- **SQL JOINs** and **aggregation** queries for business analysis

---

## ✅ Sample Use Cases

- View all online customers in a specific city
- List customers with assigned delivery employees by area code
- Show invoice and payment data by payment method
- Track ingredient usage by vendor
- Identify in-demand meals and drinks based on availability and orders

---

## 📄 Example Queries

```sql
-- 1. List all available meals
SELECT Meal_ID, Meal_Item FROM Meals WHERE Meal_availability > 0;

-- 2. Online customers assigned to delivery employees by area code
SELECT Customer.Cus_name, Employee.Emp_name
FROM Customer
JOIN Employee ON Customer.area_code = Employee.area_code
WHERE Cus_online = 1;

-- 3. Ingredients supplied by vendors
SELECT Vendor.Vendor_name, Ingredient_name, Ingredient_quantity
FROM Vendor
JOIN Ingredients ON Vendor.Vendor_ID = Ingredients.Vendor_ID;
```
