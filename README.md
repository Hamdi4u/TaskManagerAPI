Task Management API (.NET 8)


A simple RESTful API for managing users and tasks, with role-based access using ASP.NET Core 8, EF Core (InMemory), JWT authentication, and Swagger documentation.
________________________________________
 How to Run the Project
 Requirements
•	.NET 8 SDK
•	Visual Studio 2022+ or Visual Studio Code
•	Git
________________________________________
Setup Instructions
1.	Build the Project
dotnet build

•	Make sure you ran migrations: SQL local database to save data and in memory refresh and lost data so I converted it to local TaskDb 
Type code in package manager console to be sure data is updated
dotnet ef migrations add InitialCreate
dotnet ef database update

2.	Run the Project
dotnet run
The API will launch and open Swagger UI for testing.
________________________________________
How to Test the API (via Swagger)
Swagger UI provides a visual interface to test all endpoints:
1. Authenticate to Get a Token
•	Go to POST /api/auth/login
•	Click Try it out
•	Input credentials:
{
  "username": "admin",
  "password": "admin123"
}

 


•	Click Execute, then copy the token from the response
•	Click Authorize (top right) and enter:

 
Bearer your-jwt-token-here
________________________________________
2. User Endpoints
Method	Endpoint	Description	Access
POST	/api/users	Create a new user	Public
GET	/api/users	List all users	Admin
GET	/api/users/{id}	Get a user by ID	Admin
PUT	/api/users/{id}	Update user details	Admin
DELETE	/api/users/{id}	Delete a user	Admin
________________________________________
3. Task Endpoints
Method	Endpoint	Description	Access
POST	/api/tasks	Create a task	Admin
GET	/api/tasks	List all tasks	Admin
GET	/api/tasks/{id}	Get a task (assigned to you)	Admin/User
PUT	/api/tasks/{id}	Update task	Admin / (User → status only)
DELETE	/api/tasks/{id}	Delete a task	Admin
________________________________________


Seeded Users
These test users are auto-loaded into the in-memory database when the app starts:
Username	Password	Role
admin	admin123	Admin
user	user123	User
________________________________________
Running Unit Tests
To run the unit tests:
dotnet test
At least one service and one controller action have been unit tested as part of the assignment.
________________________________________
API Documentation
The full Swagger/OpenAPI documentation is available at:
https://localhost:5001/swagger

