# Data Validation in Web Apps

- Data Validation - The process of ensuring a web application operates on clean, correct and useful data. For example:
	- Ensure a user provides a vlide email address, phone number, etc.
	- Ensure that inputs (505) 255-1234, 505-255-1234 and 5052551234 are all treated the same.
	- Ensure that "business rules" are not being violated.
	- e.g. a comment cannot be stored without a post ID.

- Data input also provides an attack vector
- Failure to validata client-side input - a commont web application security weakness
- Lack of validation enables:
	- SQL injection attacks
	- Cross-site scripting attacks
	- Buffer overflow attacks.

### Ways of Validations:
- Client-side validations (JavaScript, HTML5)
- Server-side validations
