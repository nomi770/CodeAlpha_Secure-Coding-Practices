import secrets
import bcrypt

# Simulate a database connection (replace with actual database implementation)
users = {}

def register(username, password):
    # Validate username
    if not username.isalnum():
        raise ValueError("Username must contain only alphanumeric characters")

    # Sanitize and hash password
    hashed_password = bcrypt.hashpw(password.encode(), bcrypt.gensalt())

    # Store user in "database" (replace with secure storage)
    users[username] = hashed_password

def login(username, password):
    try:
        hashed_password = users[username]
    except KeyError:
        # Don't reveal username existence for security reasons
        raise ValueError("Invalid login credentials")

    if bcrypt.checkpw(password.encode(), hashed_password):
        # Generate a random, secure session ID
        session_id = secrets.token_urlsafe(32)
        # ... (associate session_id with user for further requests)
        return session_id
    else:
        raise ValueError("Invalid login credentials")

# Usage example
username = input("Enter username: ")
password = input("Enter password: ")

try:
    register(username, password)
    print("Registration successful!")
except ValueError as e:
    print("Registration failed:", e)

try:
    session_id = login(username, password)
    print("Login successful, session ID:", session_id)
except ValueError as e:
    print("Login failed:", e)
