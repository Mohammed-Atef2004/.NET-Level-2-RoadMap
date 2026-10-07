# 🏃 Sprint 2 — State Management & Media
**Weeks 3–4 · Project 1: E-Commerce MVC**

## 🎯 Goal
Build features that every real-world e-commerce application needs while learning state management, file handling, caching, and better user experience.

---

## 📚 Concepts
- File Upload & Validation
- Session vs Cookies
- Shopping Cart
- Memory Cache
- Pagination
- Searching
- Sorting
- Partial Views

---

## 📝 Features

### 📦 Product Image Management
Implement complete image lifecycle management.
- Upload product images
- Validate file extension and size
- Rename images using GUID
- Replace old image when editing
- Delete image when product is deleted
- Display placeholder image when none exists

---

### 🛒 Shopping Cart
Implement a complete shopping cart using Session.
- Add products to cart
- Increase / decrease quantity
- Remove items
- Clear cart
- Calculate totals automatically
- Display cart summary

---

### 🔍 Product Browsing
Improve product discovery.
- Search by product name
- Search by description
- Filter by category
- Sort by:
  - Name
  - Price
  - Newest
- Add server-side pagination

---

### ⚡ Performance Optimization
Improve application performance.
- Cache categories using IMemoryCache
- Invalidate cache after CRUD operations
- Minimize unnecessary database queries

---

## ✅ Deliverable
A complete shopping experience with image management, session cart, searching, sorting, pagination, and caching.

---

## 🔗 Resource Hub

### 🇬🇧 English Creators
- **Nick Chapsas — "The Only Cache You Should Be Using in .NET"** (IMemoryCache): https://www.youtube.com/watch?v=SNoJtwiY4c4
- **Milan Jovanović — "Adding Filtering, Sorting And Pagination To a REST API (.NET 7)"**: https://www.youtube.com/watch?v=X8zRvXbirMU
- **Code Maze — "Pagination in ASP.NET Core Web API with Onion Architecture"**: https://www.youtube.com/watch?v=MdK9PeXksg4

### 📄 Official Docs
- File Upload: https://learn.microsoft.com/en-us/aspnet/core/mvc/models/file-uploads
- Session & State Management: https://learn.microsoft.com/en-us/aspnet/core/fundamentals/app-state
- In-Memory Cache: https://learn.microsoft.com/en-us/aspnet/core/performance/caching/memory
