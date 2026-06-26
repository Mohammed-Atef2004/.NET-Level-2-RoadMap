# Sprint 3 — Data Management & Integrations

> Duration: Weeks 5–6

## 🎯 Sprint Goal

Learn advanced Entity Framework Core features and integrate external services commonly used in production applications.

By the end of this sprint, the application should support soft deletion, transactional emails, and a complete order workflow.

---

# Task 1 — Advanced Entity Framework Core

## Objective

Improve the application's data layer using production-ready EF Core techniques.

---

## Requirements

### Soft Delete

Implement soft delete for:

- Products
- Categories

Instead of deleting records permanently:

- Set `IsDeleted = true`
- Set `DeletedAt = DateTime.UtcNow`

---

### Global Query Filters

Configure EF Core Global Query Filters.

Requirements:

- Hide deleted Products
- Hide deleted Categories

Deleted records should not appear in normal queries.

---

### Archived Products

Create an Admin page that displays archived products.

Requirements:

- Ignore Global Query Filters
- Restore deleted products
- Hide the page from customers

---

### Audit Information

Add audit fields to entities.

Fields:

- CreatedAt
- UpdatedAt

Automatically populate them inside `SaveChanges()`.

---

### Fluent API

Move entity configuration from Data Annotations to Fluent API.

Configure:

- Required properties
- Maximum lengths
- Relationships
- Indexes

---

## Concepts

- Global Query Filters
- Soft Delete
- Fluent API
- Entity Configuration
- Audit Fields

---

## Deliverable

A production-ready data layer with Soft Delete, audit fields, and Fluent API configuration.

---

# Task 2 — Email Integration

## Objective

Send professional HTML emails from the application.

---

## Requirements

### MailKit

Configure MailKit using SMTP.

Store SMTP settings inside:

- appsettings.json

Bind configuration using the Options Pattern.

---

### Email Service

Create:

- IEmailService
- MailKitEmailService

Method:

- SendAsync()

---

### Email Templates

Create HTML templates for:

- Welcome Email
- Order Confirmation Email

Templates should contain:

- Customer Name
- Order Summary
- Total Price
- Delivery Information

---

### Registration Email

Send a Welcome Email after a successful registration.

---

### Order Confirmation

After placing an order:

- Generate email
- Send confirmation automatically

---

## Concepts

- SMTP
- MailKit
- HTML Templates
- Options Pattern

---

## Deliverable

A reusable email service capable of sending professional HTML emails.

---

# Task 3 — Orders & Checkout

## Objective

Build a complete ordering workflow.

---

## Requirements

### Order Entities

Create:

- Order
- OrderItem

Each order should belong to:

- One Customer

Each order contains:

- Multiple Order Items

---

### Checkout

Create a Checkout page.

Display:

- Cart Items
- Total Price

Collect:

- Customer Name
- Phone Number
- Address

---

### Fake Payment

Implement a simulated payment process.

When payment succeeds:

- Create Order
- Create Order Items
- Clear Shopping Cart
- Send Confirmation Email

---

### My Orders

Create a page where customers can:

- View all orders
- View order details
- View order status

---

### Order Status

Support:

- Pending
- Paid
- Cancelled

---

## Concepts

- Aggregate Root
- Parent-Child Relationship
- Transactions
- Order Workflow

---

## Deliverable

A complete checkout experience with persistent orders and email confirmation.

---

# Sprint Deliverables

Students should have completed:

- ✅ Soft Delete
- ✅ Global Query Filters
- ✅ Fluent API Configuration
- ✅ Audit Fields
- ✅ MailKit Integration
- ✅ HTML Email Templates
- ✅ Order Management
- ✅ Checkout Workflow
- ✅ Customer Order History

Project 1 is now complete and represents a production-style MVC E-Commerce application.