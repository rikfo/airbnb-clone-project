# airbnb-clone-project

# Backend

# Project Goals
## 1. User Management:
Implement a secure system for user registration, authentication, and profile management.
## 2. Property Management:
Develop features for property listing creation, updates, and retrieval.
## 3. Booking System:
Create a booking mechanism for users to reserve properties and manage booking details.
## 4. Payment Processing:
Integrate a payment system to handle transactions and record payment details.
## 5. Review System:
Allow users to leave reviews and ratings for properties.
## 6. Data Optimization:
Ensure efficient data retrieval and storage through database  

**Tech Stack**
React will be used in the frontend while django will be used in the backend.  

# Team Roles
**Backend Developer**: is the developer responsible for the service side logic, including API endpoints implementing, database schemes, and implementing algorithms and business logic.  

**Database Administrator**: is responsible for optimizing, managing, and designing the database logic.  

**DevOps Engineer**: is the linking point between backend and frontend developers, and is also responsible for deployment, testing, and scaling backend services.

**QA Engineer**: is responsible for making sure and application runs according to the requirements, and spots functional and non-functional defects.

# Technology Stack
- **Django**: A high-level Python web framework used for building the RESTful API.
- **Django REST Framework**: Provides tools for creating and managing RESTful APIs.
- **PostgreSQL**: A powerful relational database used for data storage.
- **GraphQL**: Allows for flexible and efficient querying of data.
- **Celery**: For handling asynchronous tasks such as sending notifications or processing payments.
- **Redis**: Used for caching and session management.
- **Docker**: Containerization tool for consistent development and deployment environments.
- **CI/CD Pipelines**: Automated pipelines for testing and deploying code changes.

# Database Design
## **1. User**
Represents the people using the platform, either as guests or hosts (or both).  
**Key Fields:**
  - **id**: Unique identifier
  - **name**: Full name of the user
  - **email**: Unique email address
  - **password_hash**: Encrypted password
  - **role**: Host or Guest (or both)

**Relationships:**  
A user can own multiple properties (if they’re a host)  
A user can make multiple bookings (if they’re a guest)  
A user can write multiple reviews  

## **2. Property**  
Represents the places listed for rent.  
**Key Fields:**
  - **id**: Unique identifier
  - **title**: Name of the property
  - **description**: Detailed description
  - **location**: Address or coordinates
  - **price_per_night**: Rental price

**Relationships:**  
A property belongs to one user (the host)  
A property can have multiple bookings  
A property can have multiple reviews  

## **3. Booking**  
Represents a reservation made by a guest.  
**Key Fields:**
  - **id**: Unique identifier
  - **user_id**: Who booked it (guest)
  - **property_id**: Which property was booked
  - **start_date**: Check-in date
  - **end_date**: Check-out date

**Relationships:**  
A booking belongs to one user (guest)  
A booking belongs to one property  
A booking may have one payment  

## **4. Review**  
Represents feedback left by a guest after a stay.  
**Key Fields:**
  - **id**: Unique identifier
  - **user_id**: Who left the review
  - **property_id**: Which property was reviewed
  - **rating**: Score (e.g., 1–5 stars)
  - **comment**: Text review

**Relationships:**  
A review belongs to one user (guest)  
A review belongs to one property  

## **5. Payment**  
Represents a financial transaction for a booking.  
**Key Fields:**
  - **id**: Unique identifier
  - **booking_id**: Linked booking
  - **amount**: Total amount paid
  - **payment_method**: Card, PayPal, etc.
  - **status**: Paid, Pending, Failed

**Relationships:**  
A payment belongs to one booking  
A booking has one payment  

# Feature Breakdown
## Features Overview
### 1. API Documentation
OpenAPI Standard: The backend APIs are documented using the OpenAPI standard to ensure clarity and ease of integration.
Django REST Framework: Provides a comprehensive RESTful API for handling CRUD operations on user and property data.
GraphQL: Offers a flexible and efficient query mechanism for interacting with the backend.
### 2. User Authentication
Endpoints: /users/, /users/{user_id}/
Features: Register new users, authenticate, and manage user profiles.
### 3. Property Management
Endpoints: /properties/, /properties/{property_id}/
Features: Create, update, retrieve, and delete property listings.
### 4. Booking System
Endpoints: /bookings/, /bookings/{booking_id}/
Features: Make, update, and manage bookings, including check-in and check-out details.
### 5. Payment Processing
Endpoints: /payments/
Features: Handle payment transactions related to bookings.
### 6. Review System
Endpoints: /reviews/, /reviews/{review_id}/
Features: Post and manage reviews for properties.
### 7. Database Optimizations
Indexing: Implement indexes for fast retrieval of frequently accessed data.
Caching: Use caching strategies to reduce database load and improve performance.

# API Security
## 1. Authentication
Verifies user identity (e.g., login with hashed passwords, JWTs).  
Protects accounts from unauthorized access.
## 2. Authorization
Controls what each user can do (e.g., only hosts can edit their listings).  
Prevents users from accessing others’ data.
## 3. Rate Limiting
Limits number of requests per user/IP.  
Stops abuse like brute-force attacks or spam.
## 4. Input Validation
Checks and sanitizes all user input.  
Prevents SQL injection & XSS attacks.
## 5. Secure Payments
Uses trusted payment providers (e.g., Stripe).  
Ensures safe, PCI-compliant transactions.
## 6. Data Encryption
Encrypts sensitive data and uses HTTPS.  
Keeps personal and financial data safe.

# What is CI/CD?
CI/CD (Continuous Integration/Continuous Deployment) is a process that automates testing and deployment of code changes.  
CI (Continuous Integration): Automatically tests and merges code when changes are pushed.  
CD (Continuous Deployment): Automatically deploys the app after successful tests.
## Why It’s Important for the Project
Faster development: Code changes go live quickly.  
Fewer bugs: Automated tests catch errors early.  
Better collaboration: Developers can work smoothly as code is continuously merged and tested.
## Tools You Can Use
GitHub Actions – Automate testing and deployment  
Docker – Containerize the app for consistent environments  
Jest / Mocha – For running tests  
Heroku / Vercel / AWS – For deployment

# Frontend

# UI/UX Design Planning
## Design Goals
**Simplicity**: Clean and intuitive user interface.  
**Responsiveness**: Works on mobile, tablet, and desktop.  
**Performance**: Fast loading, smooth navigation.  
**Security**: Protect user data and payments.  
**Scalability**: Easy to maintain and extend features later.
## Key Features
- User registration/login (auth)  
- Property search & filter (by location, price, etc.)  
- Host property listing  
- Booking system with availability check  
- Reviews and ratings  
- Secure payment integration  
- User dashboard (bookings, listings, reviews)  
## Primary Page Descriptions
| Page | Description|
|------|------------|
| Property Listing View |	Shows a grid/list of properties with images, price, and basic details. Includes filters (e.g., price, location). |
| Listing Detailed View	| Shows full details of a selected property: photos, description, host info, availability calendar, and reviews. |
| Simple Checkout View | Lets the user confirm booking dates, view total cost, and make payment securely. |  
## Why User-Friendly Design Matters
**Easy Navigation**: Helps users find properties or make bookings quickly.  
**Reduces Friction**: Simple forms and clear flows make the experience smooth.  
**Boosts Conversions**: A better UX increases trust, which leads to more bookings.  
**Accessibility**: Inclusive design means everyone can use it regardless of device or ability.  

## Color Styles

| Name            | Hex Code   | Usage                          |
|-----------------|------------|---------------------------------|
| Primary         | #1E90FF    | Buttons, links, highlights     |
| Secondary       | #F5F5F5    | Backgrounds, cards             |
| Accent          | #FF7F50    | Icons, tags, call-to-action    |
| Text - Primary  | #222222    | Main text                      |
| Text - Secondary| #666666    | Subtext, hints                 |
| Error           | #FF4C4C    | Validation errors, warnings    |
| Success         | #28a745    | Booking success, notifications |

---

## Typography

| Style          | Value                       |
|----------------|-----------------------------|
| Font Family    | `Inter`, `sans-serif`       |
| Font Weights   | 400 (regular), 600 (semi-bold), 700 (bold) |
| Font Sizes     | 
- `12px` (caption)  
- `14px` (secondary text)  
- `16px` (body text)  
- `24px` (section headings)  
- `32px` (main titles) |

---

## Why Identifying Design Properties Matters

- **Consistency:** Ensures a cohesive look across all screens and components.
- **Efficiency:** Developers and designers stay aligned, reducing confusion and rework.
- **Scalability:** Easier to maintain or scale the project with reusable styles.
- **Accessibility:** Proper font sizes, contrast, and spacing enhance usability for all users.

---
