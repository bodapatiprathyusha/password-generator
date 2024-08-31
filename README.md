# password-generator
import random
import string

def generate_password(length, complexity):
    characters = ""
    
    if complexity >= 1:
        characters += string.ascii_lowercase
    if complexity >= 2:
        characters += string.ascii_uppercase
    if complexity >= 3:
        characters += string.digits
    if complexity >= 4:
        characters += string.punctuation
    
    if not characters:
        print("Invalid complexity level. Please try again.")
        return
    
    password = ''.join(random.choice(characters) for _ in range(length))
    return password

def password_generator():
    print("Password Generator")
    
    try:
        length = int(input("Enter the desired length of the password: "))
        if length <= 0:
            print("Length should be a positive integer. Please try again.")
            return
    except ValueError:
        print("Invalid input. Please enter a numeric value.")
        return
    
    print("Choose the complexity level:")
    print("1. Lowercase letters")
    print("2. Lowercase and Uppercase letters")
    print("3. Lowercase, Uppercase letters, and Digits")
    print("4. Lowercase, Uppercase letters, Digits, and Punctuation")
    
    try:
        complexity = int(input("Enter complexity level (1/2/3/4): "))
        if complexity not in [1, 2, 3, 4]:
            print("Invalid complexity level. Please try again.")
            return
    except ValueError:
        print("Invalid input. Please enter a numeric value.")
        return
    
    password = generate_password(length, complexity)
    if password:
        print(f"Generated password: {password}")

# Run the password generator
password_generator()
