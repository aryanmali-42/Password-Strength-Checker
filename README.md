# Password-Strength-Checker
import re

def check_password_strength(password):
    strength = 0
    suggestions = []

    if len(password) >= 8:
        strength += 1
    else:
        suggestions.append("Make it at least 8 characters long.")

    if re.search(r"[A-Z]", password):
        strength += 1
    else:
        suggestions.append("Add at least one uppercase letter.")

    if re.search(r"[a-z]", password):
        strength += 1
    else:
        suggestions.append("Add at least one lowercase letter.")

    if re.search(r"[0-9]", password):
        strength += 1
    else:
        suggestions.append("Add at least one digit.")

    if re.search(r"[!@#$%^&*(),.?\":{}|<>]", password):
        strength += 1
    else:
        suggestions.append("Add a special character.")

    print(f"\nPassword: {password}")
    if strength == 5:
        print("Strength: Strong 💪")
    elif strength >= 3:
        print("Strength: Moderate ⚠️")
    else:
        print("Strength: Weak ❌")

    if suggestions:
        print("Suggestions:")
        for s in suggestions:
            print(" -", s)

# Example usage
password = input("Enter your password to check: ")
check_password_strength(password)
