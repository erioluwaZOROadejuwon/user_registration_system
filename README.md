# user_registration_system
# User Registration System

A Python exercise that validates user signup details (username, email, password) using helper functions, then registers the user by returning their details as a dictionary.

## Features
- Modular validation — each field (username, email, password) is checked by its own dedicated helper function
- `validate_user()` coordinates all three checks and raises a `ValueError` with a specific message when something is invalid
- `register_user()` catches that error internally, returning `False` on failure or a user dictionary on success
- Docstrings on every function explaining its purpose

## How it works

**Validation rules used in this version:**
- Username must be at least 8 characters, with no spaces
- Email must contain `@` and a `.` in the domain part
- Password must be at least 8 characters, and contain both a digit and a symbol

## How to run
```
python validator.py
```

## Example usage
```python
result = register_user("erioluwa", "eri@example.com", "pass123!")
print(result)
```

## What I learned
- Breaking one big validation task into small, single-purpose helper functions
- Using `raise` to trigger a specific error the moment invalid input is detected, instead of letting the program continue with bad data
- Using `try`/`except` inside `register_user()` to catch an error raised deeper in the call stack (`validate_user()`) and turn it into a simple `False` return value instead of letting it crash the program
- `any()` combined with a generator expression (`any(char in string.digits for char in password)`) as a compact way to check "does at least one character meet this condition?"
- Dictionary keys are just strings I choose myself — Python doesn't enforce any particular casing, but if a test or another piece of code expects a specific key name, matching it exactly (including case) matters

## Known issue (caught during review)
This version's `validate_username()` required a minimum of 8 characters, and `validate_password()` required both a digit and a symbol. A test case (`validate_user('John', 'john@example.com', 'securePassword123')`) revealed these rules were stricter than what the exercise actually expected — the correct rules turned out to be a shorter minimum username length and no mandatory symbol in the password. This is a good example of validating assumptions against actual test cases rather than just what "feels right."

## Tech
Python 3, standard library only (`string`)

