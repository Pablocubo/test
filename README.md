Student Management API Documentation
Overview
This Student Management API allows for the handling of student data, including retrieval, creation, deletion, and updating of student records and grades. It is built using Express.js with body-parser for parsing request bodies and uuid for generating unique identifiers for new student entries.

Base URL
The base URL for the API is:

http://<hostname>:8080
Where <hostname> should be replaced with the domain or IP address of the server where the API is hosted.

Endpoints
GET /students
Description: Retrieve a list of all students.
Response: JSON array of student objects.
GET /students/:name
Description: Retrieve the data for a single student by name.
Parameters:
name: Name of the student (string).
Response: JSON object of the student's data.
POST /students
Description: Add a new student record.
Body: JSON object containing at least the name key.
Response:
Success: JSON object of the created student, including the new id.
Error: Plain text error message with a 400 status code if the name key is missing.
DELETE /students/:id
Description: Delete a student record by ID.
Parameters:
id: Unique identifier of the student (UUID string).
Response:
Success: Plain text confirmation message with a 201 status code.
Error: No explicit error handling for non-existent IDs.
PUT /students/:name/:class/:grade
Description: Update the grade for a specific class of a student.
Parameters:
name: Name of the student (string).
class: Name of the class (string).
grade: New grade to be assigned (integer in string format).
Response:
Success: Plain text confirmation message with a 201 status code.
Error: Plain text error message with a 404 status code if the student is not found.
GET /students/:name/gpa
Description: Calculate and retrieve the GPA for a student.
Parameters:
name: Name of the student (string).
Response:
Success: Plain text representation of the GPA with a 201 status code.
Error: Plain text error message with a 404 status code if the student is not found.
Running the API
Ensure Node.js is installed on your system.
Include the required modules using npm install express body-parser uuid.
Launch the application using the command node app.js (assuming your file is named app.js).
The API will be accessible via http://localhost:8080 if run locally, or the configured host's address and port.
Error Handling
The API currently sends a 400 status code when creating a student without a name and a 404 status code when a student cannot be found for retrieval or update actions. Other error checks, such as for non-existent classes or invalid grade values, have not been implemented.
