# Date of Birth Field Requirements

## 1. Purpose

Replace the `is_adult` field with a required `dateOfBirth` field during user registration.

The system must collect the user's exact date of birth instead of a boolean value indicating whether the user is an adult.

## 2. Field Description

| Attribute | Requirement |
|---|---|
| Field name | `dateOfBirth` |
| Data type | String |
| Format | YYYY-MM-DD |
| Required | Yes |
| Example | `1999-03-15` |

## 3. Validation Rules

1. The `dateOfBirth` field is mandatory.
2. The date must follow the `YYYY-MM-DD` format.
3. The date must be a valid calendar date.
4. The date must not be in the future.
5. No minimum age restriction is specified until confirmed by the business.

## 4. Error Messages

| Validation scenario | Error message |
|---|---|
| Missing date of birth | Date of birth is required. |
| Invalid date format | Invalid date format. Use YYYY-MM-DD. |
| Invalid calendar date | Invalid date of birth. Please enter a valid calendar date. |
| Future date | Date of birth cannot be in the future. |

## 5. Expected API Behavior

- The registration request must include the `dateOfBirth` field.
- If validation is successful, the API returns `201 Created`.
- If validation fails, the API returns `400 Bad Request`.
- The API must reject requests containing an invalid or missing date of birth.

## 6. Open Questions

- Should the system enforce a minimum age of 18?
- Should the user's date of birth be included in the registration response?

These business rules require confirmation.
