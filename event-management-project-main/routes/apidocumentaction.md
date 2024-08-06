API Documentation
1. Authentication Routes
Register User
Method: POST
URL: /auth/register
Description: Register a new user.
Parameters:
Body: JSON object containing name, email, password
Example Request:
bash
Copiar código
curl -X POST "https://api.example.com/auth/register" -H "Content-Type: application/json" -d '{"name": "John Doe", "email": "john.doe@example.com", "password": "password123"}'
Response:
json
Copiar código
{
  "message": "User registered successfully"
}
Login User
Method: POST
URL: /auth/login
Description: Authenticate a user and return a token.
Parameters:
Body: JSON object containing email, password
Example Request:
bash
Copiar código
curl -X POST "https://api.example.com/auth/login" -H "Content-Type: application/json" -d '{"email": "john.doe@example.com", "password": "password123"}'
Response:
json
Copiar código
{
  "token": "your-jwt-token"
}
2. Event Routes
Create Event
Method: POST
URL: /events
Description: Create a new event (requires authentication).
Parameters:
Body: JSON object containing event details.
Example Request:
bash
Copiar código
curl -X POST "https://api.example.com/events" -H "Authorization: Bearer YOUR_ACCESS_TOKEN" -H "Content-Type: application/json" -d '{"title": "Event Title", "date": "2024-12-31", "location": "Event Location"}'
Response:
json
Copiar código
{
  "message": "Event created successfully"
}
Get All Events
Method: GET
URL: /events
Description: Retrieve all events (requires authentication).
Example Request:
bash
Copiar código
curl -X GET "https://api.example.com/events" -H "Authorization: Bearer YOUR_ACCESS_TOKEN"
Response:
json
Copiar código
[
  {
    "id": "1",
    "title": "Event Title",
    "date": "2024-12-31",
    "location": "Event Location"
  }
]
Get Event by ID
Method: GET
URL: /events/:id
Description: Retrieve an event by its ID (requires authentication).
Parameters:
Path: id - Event ID
Example Request:
bash
Copiar código
curl -X GET "https://api.example.com/events/1" -H "Authorization: Bearer YOUR_ACCESS_TOKEN"
Response:
json
Copiar código
{
  "id": "1",
  "title": "Event Title",
  "date": "2024-12-31",
  "location": "Event Location"
}
Update Event
Method: PUT
URL: /events/:id
Description: Update an event by its ID (requires authentication and authorization).
Parameters:
Path: id - Event ID
Body: JSON object containing updated event details.
Example Request:
bash
Copiar código
curl -X PUT "https://api.example.com/events/1" -H "Authorization: Bearer YOUR_ACCESS_TOKEN" -H "Content-Type: application/json" -d '{"title": "Updated Title"}'
Response:
json
Copiar código
{
  "message": "Event updated successfully"
}
Delete Event
Method: DELETE
URL: /events/:id
Description: Delete an event by its ID (requires authentication and authorization).
Parameters:
Path: id - Event ID
Example Request:
bash
Copiar código
curl -X DELETE "https://api.example.com/events/1" -H "Authorization: Bearer YOUR_ACCESS_TOKEN"
Response:
json
Copiar código
{
  "message": "Event deleted successfully"
}
3. Notification Routes
Send Registration Confirmation
Method: POST
URL: /notifications/confirmation/:eventId
Description: Send a registration confirmation for an event (requires authentication).
Parameters:
Path: eventId - Event ID
Example Request:
bash
Copiar código
curl -X POST "https://api.example.com/notifications/confirmation/1" -H "Authorization: Bearer YOUR_ACCESS_TOKEN"
Response:
json
Copiar código
{
  "message": "Registration confirmation sent"
}
Send Event Reminder
Method: POST
URL: /notifications/reminder/:eventId
Description: Send an event reminder (requires authentication).
Parameters:
Path: eventId - Event ID
Example Request:
bash
Copiar código
curl -X POST "https://api.example.com/notifications/reminder/1" -H "Authorization: Bearer YOUR_ACCESS_TOKEN"
Response:
json
Copiar código
{
  "message": "Event reminder sent"
}
Send Event Update
Method: POST
URL: /notifications/update/:eventId
Description: Send an event update (requires authentication).
Parameters:
Path: eventId - Event ID
Example Request:
bash
Copiar código
curl -X POST "https://api.example.com/notifications/update/1" -H "Authorization: Bearer YOUR_ACCESS_TOKEN"
Response:
json
Copiar código
{
  "message": "Event update sent"
}
Get User Notifications
Method: GET
URL: /notifications/user
Description: Retrieve notifications for the authenticated user.
Example Request:
bash
Copiar código
curl -X GET "https://api.example.com/notifications/user" -H "Authorization: Bearer YOUR_ACCESS_TOKEN"
Response:
json
Copiar código
[
  {
    "id": "1",
    "type": "reminder",
    "message": "Don't forget about the event!",
    "date": "2024-12-01"
  }
]
Create Custom Notification
Method: POST
URL: /notifications/custom
Description: Create a custom notification (requires authentication).
Parameters:
Body: JSON object containing notification details.
Example Request:
bash
Copiar código
curl -X POST "https://api.example.com/notifications/custom" -H "Authorization: Bearer YOUR_ACCESS_TOKEN" -H "Content-Type: application/json" -d '{"message": "Custom notification message"}'
Response:
json
Copiar código
{
  "message": "Custom notification created"
}
4. User Management Routes
Get User Profile
Method: GET
URL: /users/profile
Description: Retrieve the profile of the authenticated user.
Parameters: None
Example Request:
bash
Copiar código
curl -X GET "https://api.example.com/users/profile" -H "Authorization: Bearer YOUR_ACCESS_TOKEN"
Response:
json
Copiar código
{
  "id": "1",
  "name": "John Doe",
  "email": "john.doe@example.com"
}
Update User Profile
Method: PUT
URL: /users/profile
Description: Update the profile of the authenticated user.
Parameters:
Body: JSON object containing updated user details.
Example Request:
bash
Copiar código
curl -X PUT "https://api.example.com/users/profile" -H "Authorization: Bearer YOUR_ACCESS_TOKEN" -H "Content-Type: application/json" -d '{"name": "Jane Doe"}'
Response:
json
Copiar código
{
  "message": "Profile updated successfully"
}
Get All Users
Method: GET
URL: /users
Description: Retrieve all users (requires admin authorization).
Parameters: None
Example Request:
bash
Copiar código
curl -X GET "https://api.example.com/users" -H "Authorization: Bearer YOUR_ACCESS_TOKEN"
Response:
json
Copiar código
[
  {
    "id": "1",
    "name": "John Doe",
    "email": "john.doe@example.com"
  }
]
Delete User
Method: DELETE
URL: /users/:id
Description: Delete a user by ID (requires admin authorization).
Parameters:
Path: id - User ID
Example Request:
bash
Copiar código
curl -X DELETE "https://api.example.com/users/1" -H "Authorization: Bearer YOUR_ACCESS_TOKEN"
Response:
json
Copiar código
{
  "message": "User deleted successfully"
}
5. Registration Routes
Register User for Event
Method: POST
URL: /registrations/:eventId/register
Description: Register a user for an event (requires authentication).
Parameters:
Path: eventId - Event ID
Example Request:
bash
Copiar código
curl -X POST "https://api.example.com/registrations/1/register" -H "Authorization: Bearer YOUR_ACCESS_TOKEN"
Response:
json
Copiar código
{
  "message": "User registered for event"
}
Cancel Registration
Method: DELETE
URL: /registrations/:eventId/cancel
Description: Cancel a user's registration for an event (requires authentication).
Parameters:
Path: eventId - Event ID
Example Request:
bash
Copiar código
curl -X DELETE "https://api.example.com/registrations/1/cancel" -H "Authorization: Bearer YOUR_ACCESS_TOKEN"
Response:
json
Copiar código
{
  "message": "Registration canceled"
}
Get User Registrations
Method: GET
URL: /registrations/user
Description: Get a list of events a user is registered for.
Parameters: None
Example Request:
bash
Copiar código
curl -X GET "https://api.example.com/registrations/user" -H "Authorization: Bearer YOUR_ACCESS_TOKEN"
Response:
json
Copiar código
[
  {
    "eventId": "1",
    "eventTitle": "Event Title",
    "date": "2024-12-31"
  }
]
Get Event Registrations
Method: GET
URL: /registrations/:eventId/registrations
Description: Get a list of users registered for a specific event (requires authentication).
Parameters:
Path: eventId - Event ID
Example Request:
bash
Copiar código
curl -X GET "https://api.example.com/registrations/1/registrations" -H "Authorization: Bearer YOUR_ACCESS_TOKEN"
Response:
json
Copiar código
[
  {
    "userId": "1",
    "userName": "John Doe"
  }
]
