# Express.js Route Handler Missing Error Handling

This repository demonstrates a common error in Express.js route handlers: missing error handling for invalid input.  The provided `bug.js` file shows a vulnerable route that crashes when passed a non-numeric ID or an ID that doesn't exist. The corrected version (`bugSolution.js`) provides robust error handling to prevent unexpected crashes.

## Bug

The `bug.js` file includes a route that retrieves a user by ID. However, it lacks error handling. If the `userId` is not a number, `parseInt(userId)` will return `NaN`, causing the `.find()` method to fail silently.  If no user matches the ID, it also doesn't handle the case appropriately.

## Solution

The `bugSolution.js` file addresses these issues by:

1. **Validating the input:**  The code checks if `userId` can be parsed as an integer using `isNaN()`. If it's not a valid integer, it returns a 400 Bad Request response.
2. **Handling missing users:** If no user matches the ID, it returns a 404 Not Found response.

This approach ensures that the application handles invalid input gracefully and prevents crashes due to unexpected data.