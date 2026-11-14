# Reflection Questions – JWT Authentication

### 1. What is the difference between authentication and authorization? Give a real-world example of each.

Authentication is the process of verifying someone's identity. For example, when a user logs in using their email and password, the system checks if their credentials are correct.

Authorization determines what an authenticated user is allowed to access or do. For example, an admin can manage all users, while a regular user can only view or update their own information.

### 2. Why is JWT considered "stateless" and how does that benefit scalability?

JWT is considered stateless because the server does not need to store session information for every logged-in user. The token contains the necessary user information and can be verified using a secret key.

This benefits scalability because multiple servers can verify tokens without sharing session storage. It makes the application easier to expand and manage.

### 3. What are the three parts of a JWT token and what does each part do?

A JWT has three parts:

- **Header** – Contains information about the token type and signing algorithm.
- **Payload** – Contains the claims or information about the user, such as user ID and email.
- **Signature** – Verifies that the token has not been modified and was signed using the correct secret key.

These three parts are separated by dots.

### 4. Why should you never put sensitive data (like passwords) in the JWT payload?

JWT payloads are encoded, not encrypted. This means anyone who gets the token can decode and read its payload. Putting passwords or other sensitive information inside it can expose private user data.

Only necessary information should be included in the payload.

### 5. How does bcrypt protect user passwords? What is the purpose of the "salt" and "rounds"?

Bcrypt protects passwords by converting them into secure password hashes before saving them in the database.

A salt is a random value added during hashing to make password hashes unique, even when users have the same password.

Rounds determine how much computational work is needed to create the hash. More rounds make password guessing attacks slower and more difficult.

### 6. What happens if someone steals a JWT token? How can you mitigate this risk?

If someone steals a JWT token, they may be able to use it to access protected routes as the legitimate user until the token expires or is otherwise rejected.

We can reduce this risk by using HTTPS, setting short token expiration times, storing tokens securely, and avoiding sharing tokens with other people. We can also implement token revocation or refresh-token rotation.

### 7. Why is it important to use HTTPS when transmitting JWT tokens?

HTTPS encrypts communication between the client and server. It helps prevent attackers from intercepting and stealing JWT tokens while they are being transmitted.

Without HTTPS, tokens may be exposed through network attacks.

### 8. What is the difference between a short-lived access token and a long-lived refresh token? When would you use each?

An access token is a short-lived token used to access protected API endpoints. It expires quickly to reduce the risk if it gets stolen.

A refresh token lasts longer and is used to request a new access token without requiring the user to log in again.

Access tokens are used for normal API requests, while refresh tokens are used when the access token expires. Our current implementation uses a JWT access token with a 24-hour expiration and does not yet implement refresh tokens.

### 9. How does the auth middleware know which user is making the request?

The auth middleware gets the JWT from the Authorization header using the Bearer token format. It then verifies the token using the JWT secret through the AuthService.

After successful verification, it gets the user ID and email from the token payload and attaches them to `req.user`. This allows protected routes to identify the user making the request.

### 10. If you had to implement role-based authorization (e.g., admin vs. regular user), how would you modify your current setup?

I would add a role field to the User entity and database, with values such as `admin` and `user`.

I would include the user's role in the JWT payload and create an authorization middleware that checks the user's role before allowing access to certain routes.

For example, only users with the admin role could access routes for managing all user accounts, while regular users would have limited access.