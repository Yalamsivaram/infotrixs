users = {}

class User:
    def __init__(self, username, password):
        self.username = username
        self.password = password
        self.profile = {}

def register():
    username = input("Enter a username: ")
    
    if username in users:
        print("Username already exists. Please choose a different username.")
        return
    
    password = input("Enter a password: ")
    user = User(username, password)
    users[username] = user
    print("Registration successful!")

def login():
    username = input("Enter your username: ")
    password = input("Enter your password: ")
    
    if username in users and users[username].password == password:
        print("Login successful!")
        manage_profile(users[username])
    else:
        print("Invalid username or password.")

def manage_profile(user):
    while True:
        print("\nProfile Management")
        print("1. View Profile")
        print("2. Update Profile")
        print("3. Logout")
        
        choice = input("Enter your choice (1-3): ")
        
        if choice == "1":
            view_profile(user)
        elif choice == "2":
            update_profile(user)
        elif choice == "3":
            print("Logged out successfully.")
            break
        else:
            print("Invalid choice. Please try again.")

def view_profile(user):
    print("\nProfile Information")
    if user.profile:
        for key, value in user.profile.items():
            print(f"{key}: {value}")
    else:
        print("Profile is empty.")

def update_profile(user):
    print("\nUpdate Profile")
    key = input("Enter profile key: ")
    value = input("Enter profile value: ")
    user.profile[key] = value
    print("Profile updated successfully!")

def main():
    while True:
        print("\nUser Registration System")
        print("1. Register")
        print("2. Login")
        print("3. Exit")
        
        choice = input("Enter your choice (1-3): ")
        
        if choice == "1":
            register()
        elif choice == "2":
            login()
        elif choice == "3":
            break
        else:
            print("Invalid choice. Please try again.")

if __name__ == "__main__":
    main()
