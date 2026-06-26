# Sprint 2 — State Management & Media

> Duration: Weeks 3–4

## 🎯 Sprint Goal

Learn how real applications manage files, application state, caching, and scalable product browsing.

By the end of this sprint, the application should provide a complete shopping cart experience with optimized product browsing and proper file management.

---

# Task 1 — Product Image Management

## Objective

Implement a professional image management system for products.

---

## Requirements

### Create File Service

- Create `IFileService`
- Implement `LocalFileService`

The service should:

- Save images inside `wwwroot/uploads/products`
- Generate unique file names using `Guid`
- Return the saved image path

---

### Validate Uploaded Images

Only allow:

- jpg
- jpeg
- png
- webp

Maximum size:

- 2 MB

Reject invalid files with meaningful validation messages.

---

### Product Create

When creating a product:

- Upload image
- Save image path inside database
- Display uploaded image correctly

---

### Product Edit

When updating a product:

- Upload new image
- Delete previous image
- Save new image path

---

### Product Delete

When deleting a product:

- Delete image from disk
- Delete product from database

---

### UI

Display:

- Product image
- Placeholder image when no image exists

---

## Concepts

- IFormFile
- File Validation
- File Streams
- Physical Storage
- GUID File Naming

---

## Deliverable

A complete image management system with automatic cleanup.

---

# Task 2 — Session Shopping Cart

## Objective

Build a shopping cart that stores products inside the user's Session.

---

## Requirements

### Cart Model

Create:

- CartItem

Fields:

- ProductId
- ProductName
- Price
- Quantity
- ImageUrl

---

### Cart Service

Create:

- ICartService

Operations:

- Get Cart
- Add Item
- Remove Item
- Increase Quantity
- Decrease Quantity
- Clear Cart

---

### Session

Configure:

- IHttpContextAccessor
- Session
- DistributedMemoryCache

Store cart as JSON inside Session.

---

### Cart Controller

Implement:

- Add To Cart
- Remove Item
- Increase Quantity
- Decrease Quantity
- Clear Cart

---

### Cart UI

Display:

- Product Image
- Product Name
- Quantity
- Unit Price
- Total Price

Display:

- Order Total

---

## Concepts

- Session
- Serialization
- JSON
- IHttpContextAccessor

---

## Deliverable

A fully functional Session-based Shopping Cart.

---

# Task 3 — Product Browsing Optimization

## Objective

Improve product browsing performance and usability.

---

## Requirements

### Pagination

Implement server-side pagination.

Features:

- Page Number
- Page Size
- Previous
- Next
- Page Numbers

---

### Search

Allow searching by:

- Product Name
- Product Description

Search should work together with pagination.

---

### Sorting

Support sorting by:

- Name ASC
- Name DESC
- Price ASC
- Price DESC

Sorting should work together with pagination.

---

### Category Caching

Cache categories using MemoryCache.

Requirements:

- Cache categories for 30 minutes
- Remove cache after Create
- Remove cache after Update
- Remove cache after Delete

---

### UI

Show:

- Search Box
- Sort Dropdown
- Pagination Component

---

## Concepts

- Skip
- Take
- IQueryable
- IMemoryCache
- Cache Invalidation

---

## Deliverable

A scalable product listing with:

- Pagination
- Searching
- Sorting
- Category Caching

---

# Sprint Deliverables

Students should have completed:

- ✅ Product Image Management
- ✅ Session Shopping Cart
- ✅ Product Pagination
- ✅ Product Search
- ✅ Product Sorting
- ✅ Memory Cache

The application should now resemble a real-world online store.