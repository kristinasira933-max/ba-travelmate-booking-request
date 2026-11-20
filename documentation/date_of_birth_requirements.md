Date of Birth Field Requirements
1. Task

A new Date_of_Birth  field will replace the `is_adult` field, as specified in the task. The `is_adult` field is currently absent from the "Register User" request in Postman.


2. Field Description


Attribute
Requirement
Field name 
dateOfBirth 
Data type 
String 
Format 
YYYY-MM-DD 
Required 
Yes 
Purpose 
Store the user's exact date of birth 
Replaces 
Adult-status indicator mentioned in the business requirement 



3. Registration Request
Method: POST
Endpoint: /auth/register
Content-Type: application/json
Example of the updated request body:


{
  "email": "newuser@example.com",
  "password": "SecurePass123!",
  "firstName": "New",
  "lastName": "User",
  "phone": "+1-555-000-0000",
  "dateOfBirth": "1999-03-15"
}




4. Validation Rules


Validation scenario
Expected API Behavior 
Missing field 
Reject request, return 400 
Empty value 
Reject request, return 400 
Invalid format 
Reject request, return 400 
Invalid calendar date 
Reject request, return 400 
Future date 
Reject request, return 400 
Under 18 
Clarifications are required from the business side












5. Error Messages



Validation Scenario
Error Message
Missing date of birth
Date of birth is required.
Empty date of birth
Date of birth cannot be empty.
Invalid date format
Invalid date format. Please use YYYY-MM-DD.
Invalid calendar date
Invalid date of birth. Please enter a correct date of birth.
Future date
Date of birth cannot be in the future.


6. Expected API Behavior
The registration request must include the required dateOfBirth field in YYYY-MM-DD format.
The API must check that the date of birth is provided, is not empty, follows the YYYY-MM-DD format, is a valid calendar date, and is not in the future.
If all required fields are valid, the API must create a new user and return 201 Created.
If dateOfBirth is missing, empty, incorrectly formatted, invalid, or in the future, the API must reject the request and return 400 Bad Request.
The API must return the corresponding error message described in Section 5.
The system must not create a user account if the date of birth fails validation.

7. Open Questions
The following point requires confirmation from the business:

- Should users be at least 18 years old to register?


