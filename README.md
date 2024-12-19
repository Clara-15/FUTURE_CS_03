# FUTURE_CS_03
# Password Manager

This is a simple Python-based Password Manager that allows users to create accounts and log in securely. It uses hashed passwords to ensure security and prevents the storage of plain-text passwords.

## Features

- **Create Account:** Users can create accounts by providing a username and password. Passwords are hashed using SHA-256 for security.
- **Login:** Users can log in by providing their credentials. The system verifies the entered password by comparing its hash.
- **Secure Storage:** Passwords are never stored in plain text. Instead, they are hashed using the SHA-256 algorithm.

## How It Works

1. **Account Creation:**
   - The user is prompted to enter a username and password.
   - The password is hashed using the SHA-256 algorithm before being stored.
   - The username and hashed password are saved in a dictionary (`password_manager`).

2. **Login:**
   - The user enters their username and password.
   - The password is hashed, and the system checks if the hashed value matches the stored hash for the given username.
   - If the credentials match, the login is successful; otherwise, an error message is displayed.

3. **Program Loop:**
   - The program runs in a loop, offering options to create an account, log in, or exit.

## Usage

1. Run the script.
2. Select an option from the menu:
   - `1`: Create a new account.
   - `2`: Log in to an existing account.
   - `0`: Exit the program.

## Code Structure

```python
import hashlib
import getpass

password_manager = {}

def create_account():
    username = input("Enter your desired username:")
    password = getpass.getpass("Enter your desired password:")
    hashed_password = hashlib.sha256(password.encode()).hexdigest()
    password_manager[username] = hashed_password
    print("Account created successfully!")

def login():
    username = input("Enter your username:")
    password = getpass.getpass("Enter your password:")
    hashed_password = hashlib.sha256(password.encode()).hexdigest()
    if username in password_manager.keys() and password_manager[username] == hashed_password:
        print("Login Successfully!")
    else:
        print("Invalid username or password.")

def main():
    while True:
        choice = input("Enter 1 to create an account, 2 to login, or 0 to exit:")
        if choice == "1":
            create_account()
        elif choice == "2":
            login()
        elif choice == "0":
            break
        else:
            print("Invalid choice")

if __name__ == "__main__":
    main()
```

## Requirements

- Python 3.x
- `getpass` module (built-in)
- `hashlib` module (built-in)

## Security Considerations

- **Hashing:** Passwords are hashed using SHA-256 to ensure secure storage.
- **Dictionary Storage:** This implementation uses an in-memory dictionary for storage, which is not persistent. In a production system, you should use a secure database for storing user data.

## Future Enhancements

- Implement persistent storage (e.g., database or file storage).
- Add password strength validation during account creation.
- Introduce multi-factor authentication for enhanced security.
- Implement account recovery options.

## License

This project is open-source and available under the [MIT License](LICENSE).
