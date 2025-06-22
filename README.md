# airbnb-clone-project
ALX Airbnb Clone.  
This Project aims to equipe me with essential skills in full stack software engineering.  
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
**1. User**
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
**2. Property**
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
**3. Booking**
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
**4. Review**
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
**5. Payment**
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
