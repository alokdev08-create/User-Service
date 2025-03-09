1. Requirements
Functional Requirements
User Registration and Authentication:

Allow users to register using their email, username, and password.

Secure authentication using OAuth2/JWT.

Support role-based login for customer, service_provider, and admin.

User Profile Management:

Users can update their personal details (e.g., name, contact number, profile picture).

Service providers can add professional details (e.g., services offered, certifications).

Login History Tracking:

Record login history with timestamps, IP addresses, and device details.

Role and Permission Management:

Allow assigning roles (customer, service_provider, admin) dynamically.

Define permissions for each role and provide fine-grained access control.

Notifications:

Send notifications (via email/SMS) for critical events like password changes, booking confirmations, or updates.

Account Recovery:

Provide secure methods for password recovery, like sending reset links to email.

Non-Functional Requirements
Security:

Encrypt sensitive information (e.g., passwords using BCrypt).

Ensure secure communication using HTTPS and token-based authentication.

Scalability:

Allow for increased user activity without degrading performance.

Extensibility:

Easily add support for new roles, permissions, or services.

Auditability:

Maintain audit logs for tracking user activities (login, profile updates).

2. Implementation
Tech Stack
Backend Framework: Spring Boot (Java)

Database: MySQL/PostgreSQL

Authentication: OAuth2/JWT

Messaging: Kafka or RabbitMQ for real-time updates

APIs: RESTful APIs for user service

API Endpoints
Below is an example of the critical API endpoints for the User Service:

HTTP Method	Endpoint	Description
POST	/api/v1/users/register	User registration
POST	/api/v1/users/login	User login and JWT token generation
GET	/api/v1/users/profile/{id}	Fetch user profile by ID
PUT	/api/v1/users/profile/update	Update user profile
GET	/api/v1/users/login-history	Retrieve user login history
GET	/api/v1/users/notifications	Fetch user-specific notifications
POST	/api/v1/users/reset-password	Trigger password reset process
Database Tables
Here’s how the database tables interact to implement the User Service:

Users Table: Manages core user details (username, email, password hash).

Roles Table: Stores roles like customer, service_provider, and admin.

UserRoles Table: Links users to their respective roles.

LoginHistory Table: Tracks each login attempt.

Notifications Table: Stores notifications sent to users.

Workflow for Critical Activities
User Registration:

User submits registration details via the frontend.

Backend validates inputs and encrypts the password.

User details are saved, and a confirmation email is sent.

User Authentication:

User submits login credentials.

Backend validates the credentials and generates a JWT token if valid.

Token is sent to the frontend for subsequent requests.

Role Assignment:

Admin assigns roles using a dedicated endpoint.

Roles are stored in the UserRoles table and permissions fetched dynamically.

3. Activities Performed by the User Service
User Management:

Handles user registration, profile updates, and password management.

Authentication:

Validates credentials and issues JWT tokens for secure access.

Authorization:

Ensures users access only the features permitted by their role/permissions.

Login Auditing:

Tracks login attempts for monitoring and security.

Notification Management:

Sends email/SMS notifications about key events.

Role and Permission Handling:

Assigns roles to users and manages role-based access control.

Data Integrity and Security:

Safeguards user data via encryption and secure APIs.

Scalable Interactions:

Handles user interactions with services, community queries, and feedback submission.
