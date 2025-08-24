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
  - `payment_method`
  - `status` (pending, successful, failed)

### Relationships
- A **User** can be both a guest (booking properties) or a host (listing properties).
- A **Property** belongs to one host (User), but can have many bookings and reviews.
- A **Booking** is linked to one User and one Property.
- A **Review** is linked to one User and one Property.
- A **Payment** is always linked to one Booking.


