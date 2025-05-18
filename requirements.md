# 📄 Backend Feature Requirements – Airbnb Clone

## 🛡️ 1. User Authentication

### Functional Requirements:
- Users must be able to register, log in, and log out securely.
- Passwords must be stored securely using hashing (e.g., bcrypt).
- JWT (JSON Web Token) should be used for session management.

### API Endpoints:
| Method | Endpoint        | Description             |
|--------|-----------------|-------------------------|
| POST   | /api/register   | Register new user       |
| POST   | /api/login      | Authenticate user       |
| POST   | /api/logout     | Invalidate session token|

### Input Specifications:
- **/register**: `{ "username": "string", "email": "email", "password": "string" }`
- **/login**: `{ "email": "email", "password": "string" }`

### Output Specifications:
- **Success**: 200 OK `{ "token": "jwt_token", "user": { id, username, email } }`
- **Failure**: 400/401 with error messages.

### Validation Rules:
- Email must be valid and unique.
- Password must be at least 8 characters with one number.
- Username must be unique.

### Performance Criteria:
- Login and registration response time ≤ 300ms.
- Handle up to 100 concurrent login requests.

---

## 🏠 2. Property Management

### Functional Requirements:
- Hosts can create, update, or delete their property listings.
- Listings include title, description, images, price, location, and availability.

### API Endpoints:
| Method | Endpoint            | Description                |
|--------|---------------------|----------------------------|
| POST   | /api/properties     | Create a new listing       |
| PUT    | /api/properties/:id | Update listing             |
| DELETE | /api/properties/:id | Delete a listing           |
| GET    | /api/properties     | Retrieve all listings      |
| GET    | /api/properties/:id | Retrieve single listing    |

### Input Specifications:
- POST/PUT:  
```json
{
  "title": "string",
  "description": "string",
  "price": "number",
  "location": "string",
  "images": ["url1", "url2"],
  "available_dates": ["2025-05-25", "2025-05-26"]
}
