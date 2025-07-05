import random
import string

def generate_password(length):
    if length < 4:
        return "Password length should be at least 4 characters."

    # Characters to include
    letters = string.ascii_letters  # a-zA-Z
    digits = string.digits          # 0-9
    symbols = string.punctuation    # !@#$%^&*()_+-=[]...

    # Combine all characters
    all_chars = letters + digits + symbols

    # Ensure at least one from each category
    password = [
        random.choice(letters),
        random.choice(digits),
        random.choice(symbols)
    ]

    # Fill the rest randomly
    password += random.choices(all_chars, k=length - 3)

    # Shuffle and join to make the final password
    random.shuffle(password)
    return ''.join(password)

def main():
    print("🔐 Password Generator")
    print("=======================")
    try:
        length = int(input("Enter desired password length: "))
        password = generate_password(length)
        print(f"\n✅ Your Generated Password: {password}")
    except ValueError:
        print("❌ Invalid input! Please enter a number.")

if __name__ == "__main__":
    main()
