# airbnb-clone-project
## Project Overview
The Airbnb Clone Project is a real-world web application designed to simulate a booking platform like Airbnb.  
It focuses on backend development, database design, API development, and security.  

### Project Goals
- Build and structure a scalable backend system.
- Practice collaborative workflows using GitHub.
- Implement security, CI/CD pipelines, and database design.
- Gain experience integrating technologies like Django, MySQL, and GraphQL.

### Tech Stack
- **Backend Framework**: Django
- **Database**: MySQL
- **API**: GraphQL / REST
- **Deployment & CI/CD**: Docker, GitHub Actions

## Team Roles

- **Backend Developer**: Responsible for implementing the core application logic, designing APIs, and integrating services.
- **Database Administrator (DBA)**: Manages database design, optimization, backups, and ensures data integrity.
- **DevOps Engineer**: Handles CI/CD pipelines, server deployment, monitoring, and scalability.
- **Frontend Developer**: Works on the user-facing part of the app, ensuring seamless integration with backend APIs.
- **Project Manager**: Coordinates tasks, ensures deadlines are met, and manages collaboration between all team members.
- **QA Engineer (Tester)**: Tests features, finds bugs, and ensures application quality and reliability.

## Technology Stack

The Airbnb Clone project is built using the following technologies:

- **Django**: A high-level Python web framework used to build the backend and RESTful APIs.
- **Django REST Framework (DRF)**: Provides tools for creating and managing RESTful APIs with authentication and permissions.
- **PostgreSQL**: A powerful relational database used to store structured data such as users, properties, bookings, and reviews.
- **GraphQL**: Enables flexible and efficient querying of the backend, allowing clients to fetch exactly the data they need.
- **Celery**: Handles background tasks like sending notifications and processing payments asynchronously.
- **Redis**: Used for caching, session management, and as a Celery broker.
- **Docker**: Provides a consistent development and deployment environment through containerization.
- **CI/CD Pipelines (GitHub Actions)**: Automates testing and deployment to ensure code reliability and faster delivery.

## Database Design

The database will use a relational structure with the following key entities:

- **Users**
  - `id` (Primary Key)
  - `username`
  - `email`
  - `password`
  - `role` (guest, host, admin)

- **Properties**
  - `id` (Primary Key)
  - `title`
  - `description`
  - `location`
  - `price_per_night`
  - `host_id` (Foreign Key → Users)

- **Bookings**
  - `id` (Primary Key)
  - `user_id` (Foreign Key → Users)
  - `property_id` (Foreign Key → Properties)
  - `start_date`
  - `end_date`
  - `status` (pending, confirmed, cancelled)

- **Reviews**
  - `id` (Primary Key)
  - `user_id` (Foreign Key → Users)
  - `property_id` (Foreign Key → Properties)
  - `rating`
  - `comment`

- **Payments**
  - `id` (Primary Key)
  - `booking_id` (Foreign Key → Bookings)
  - `amount`
  - `payment_method` (e.g., Credit Card, PayPal, M-Pesa)
  - `status` (pending, successful, failed)

### Relationships
- A **User** can be both a guest (booking properties) or a host (listing properties).
- A **Property** belongs to one host (User), but can have many bookings and reviews.
- A **Booking** is linked to one User and one Property.
- A **Review** is linked to one User and one Property.
- A **Payment** is always linked to one Booking.

## Feature Breakdown

The Airbnb Clone will include the following main features:

- **User Management**
  - Users can sign up, log in, and manage their profiles.
  - Authentication and authorization ensure secure access.
  - Supports roles like guest, host, and admin.

- **Property Management**
  - Hosts can list new properties with details (title, description, location, price).
  - Properties can include multiple images and amenities.
  - Hosts can edit or remove their listings.

- **Booking System**
  - Guests can view available properties and make bookings.
  - Bookings include start/end dates, price, and booking status.
  - Users can cancel or modify bookings within certain rules.

- **Payment Integration**
  - Guests can securely pay for bookings.
  - Payment records are stored with booking details.
  - Multiple payment methods supported:
    - Credit/Debit Cards
    - PayPal
    - M-Pesa (mobile money integration for local users)

- **Review System**
  - Guests can leave reviews and ratings for properties.
  - Reviews are tied to both the property and the user.
  - Hosts can view feedback to improve services.

- **Search and Filtering**
  - Guests can search properties by location, date, and price.
  - Advanced filters (e.g., amenities, property type) enhance the user experience.

- **Admin Dashboard**
  - Admins can oversee users, properties, and bookings.
  - Tools for monitoring system activity and handling disputes.

## API Security

To ensure the safety and reliability of the Airbnb Clone application, the backend APIs will include several security measures:

- **Authentication**
  - Users must log in before accessing protected resources.
  - Implemented using secure methods such as JWT (JSON Web Tokens) or session-based authentication.
  - Prevents unauthorized access to user accounts.

- **Authorization**
  - Controls what actions users can perform based on their role (guest, host, admin).
  - Ensures that only the right people can modify or view specific resources.
  - Example: only a host can edit their own property, and only an admin can remove accounts.

- **Input Validation & Sanitization**
  - Protects against SQL Injection and XSS attacks by validating user input.
  - Ensures only properly formatted data is processed by the system.

- **Rate Limiting**
  - Limits the number of requests a user can make in a given timeframe.
  - Prevents abuse such as brute-force login attempts or denial-of-service attacks.

- **Data Encryption**
  - Sensitive data such as passwords are hashed (e.g., using bcrypt).
  - All network communication will use HTTPS to prevent data interception.

- **Payment Security**
  - Payment details will not be stored directly in the system.
  - Instead, trusted third-party providers (e.g., Stripe, PayPal, **M-Pesa APIs**) will handle transactions.
  - This ensures compliance with industry standards like PCI-DSS.

## CI/CD Pipeline

A **CI/CD (Continuous Integration and Continuous Deployment) pipeline** ensures that our Airbnb Clone project is developed, tested, and deployed efficiently with minimal human error.

- **Continuous Integration (CI)**
  - Every time code is pushed to GitHub, automated tests will run.
  - This helps catch bugs early and ensures new code does not break existing functionality.
  - Tools: **GitHub Actions** for running automated workflows.

- **Continuous Deployment (CD)**
  - Once code passes all tests, it can be automatically deployed to a staging or production environment.
  - This guarantees faster release cycles and more reliable updates.
  - Tools: **Docker** for containerization, **Heroku/AWS** for hosting.

- **Benefits**
  - Increases team efficiency by automating repetitive tasks.
  - Ensures consistent deployments across environments.
  - Reduces risk of bugs reaching production.

**Example Workflow:**
1. Developer pushes code to GitHub.
2. GitHub Actions run tests and linting checks.
3. If tests pass, Docker builds a container image of the app.
4. The container is deployed to the server (Heroku, AWS, or similar).
5. Application is live with minimal downtime.

