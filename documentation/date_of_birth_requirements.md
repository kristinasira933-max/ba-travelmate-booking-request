# Date of Birth Field Requirements

## 1. Purpose

The goal is to replace the `is_adult` field with a new required field `dateOfBirth` in the user registration process.

Instead of asking users to confirm whether they are adults, the system will collect their exact date of birth.

## 2. Field Description

| Attribute | Requirement |
|---|---|
| Field name | `dateOfBirth` |
| Data type | String |
| Format | YYYY-MM-DD |
| Required | Yes |
| Example | `1999-03-15` |

## 3. Registration Request

**Method:** POST

**Endpoint:** `/auth/register`

**Content-Type:** `application/json`

Example of the updated request body:

```json
{
  "email": "newuser@example.com",
  "password": "SecurePass123!",
  "firstName": "New",
  "lastName": "User",
  "phone": "+1-555-000-0000",
  "dateOfBirth": "1999-03-15"
}
```

## 4. Validation Rules

The system must check the following conditions:

1. The `dateOfBirth` field is required and cannot be empty.
2. The date must be entered in the `YYYY-MM-DD` format.
3. The entered date must be a valid calendar date.
4. The date of birth cannot be in the future.
5. No minimum age restriction is defined at this stage. This rule requires confirmation from the business.

## 5. Error Messages

The following error messages should be displayed when validation fails:

| Validation scenario | Error message |
|---|---|
| Missing date of birth | Date of birth is required. |
| Invalid date format | Invalid date format. Use YYYY-MM-DD. |
| Invalid calendar date | Invalid date of birth. Please enter a valid calendar date. |
| Future date | Date of birth cannot be in the future. |

## 6. Expected API Behavior

- The registration request must include the `dateOfBirth` field.
- The API must validate the date before creating a new user.
- If all validation checks pass, the API returns `201 Created`.
- If the date is missing or invalid, the API returns `400 Bad Request`.
- The system must not create a user if the date of birth does not pass validation.

## 7. Open Questions

The following points require confirmation from the business:

- Should users be at least 18 years old to register?
- Should the date of birth be included in the registration response?
