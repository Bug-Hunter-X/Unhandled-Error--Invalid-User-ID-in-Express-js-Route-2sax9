# Unhandled Error: Invalid User ID in Express.js Route

This repository demonstrates a common error in Express.js route handlers:  lack of error handling for invalid input.

The `bug.js` file shows a vulnerable route that attempts to parse a user ID from the request parameters. If the ID is not a number, it will cause an error. The `bugSolution.js` file shows how to implement proper error handling to prevent this.

## Bug

The bug lies in the `/users/:id` route.  It attempts to convert the `userId` to an integer using `parseInt()` without verifying the input is valid.  If a non-numeric string is passed as `userId`, `parseInt()` will return `NaN`, and the subsequent `users.find()` will not work as expected, causing unexpected behavior, or, in some cases a server crash.

## Solution

The solution involves adding input validation and handling the case where a user is not found.