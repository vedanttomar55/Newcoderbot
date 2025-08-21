import random

alphabet = "abcdefghijklmnopqrstuvwxyz"
uppercase = alphabet.upper()
digits = "0123456789"
special_characters = "!@#$%^&*()-_=+[]{}|;:',.<>?/"

def get_user_input():
    while True:
        try:
            length = int(input("\nEnter the desired password length (minimum 8 characters): "))
            letters = int(input("Enter the minimum number of letters: "))
            digits_count = int(input("Enter the minimum number of digits: "))
            special_count = int(input("Enter the minimum number of special characters: "))

            if length < 8:
                print("Password length must be at least 8.")
            elif letters < 0 or digits_count < 0 or special_count < 0:
                print("All values must be non-negative.")
            elif letters + digits_count + special_count > length:
                print("The sum of letters, digits, and special characters exceeds the total length.")
            else:
                return length, letters, digits_count, special_count

        except ValueError:
            print("Invalid input. Please enter valid integers.")

def generate_password(length, letters, digits_count, special_count):
    password = []

    for _ in range(letters):
        password.append(random.choice(alphabet + uppercase))
    for _ in range(digits_count):
        password.append(random.choice(digits))
    for _ in range(special_count):
        password.append(random.choice(special_characters))

    while len(password) < length:
        all_chars = alphabet + uppercase + digits + special_characters
        password.append(random.choice(all_chars))

    random.shuffle(password)
    return ''.join(password)

def evaluate_strength(password):
    score = 0
    if len(password) >= 12:
        score += 1
    if any(c.islower() for c in password) and any(c.isupper() for c in password):
        score += 1
    if any(c.isdigit() for c in password):
        score += 1
    if any(c in special_characters for c in password):
        score += 1

    if score == 4:
        return "Strong"
    elif score == 3:
        return "Moderate"
    else:
        return "Weak"

def main():
    print("\n\t--Welcome to the Password Generator!--")

    while True:
        length, letters, digits_count, special_count = get_user_input()
        password = generate_password(length, letters, digits_count, special_count)
        strength = evaluate_strength(password)

        print(f"\nGenerated Password: {password}")
        print(f"Password Strength: {strength}")

        again = input("\nWould you like to generate another password? (yes/no): ").strip().lower()
        if again != "yes":
            print("\nThank you for using the Password Generator!\n")
            break

if __name__ == "__main__":
    main()
