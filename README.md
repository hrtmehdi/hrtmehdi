- 👋 Hi, I’m @hrt
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
hrtmehdi/hrtmehdi is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
python
def vigenere_decrypt(ciphertext, key):
    plaintext = ""
    key_index = 0
    for char in ciphertext:
        if char.isalpha():
            key_char = key[key_index % len(key)]
            if char.isupper():
                base = ord('A')
            else:
                base = ord('a')
            decrypted_char = chr((ord(char) - ord(key_char) + 26) % 26 + base)
            plaintext += decrypted_char
            key_index += 1
        else:
            plaintext += char
    return plaintext

def caesar_decrypt(ciphertext, shift):
    plaintext = ""
    for char in ciphertext:
        if char.isalpha():
            if char.isupper():
                base = ord('A')
            else:
                base = ord('a')
            decrypted_char = chr((ord(char) - shift - base + 26) % 26 + base)
            plaintext += decrypted_char
        else:
            plaintext += char
    return plaintext

ciphertext = input("Enter the encrypted text: ")
algorithm_choice = input("Choose the algorithm (Vigenère or Caesar): ")

if algorithm_choice.lower() == "vigenère":
    key = input("Enter the Vigenère key: ")
    decrypted_text = vigenere_decrypt(ciphertext, key)
elif algorithm_choice.lower() == "caesar":
    shift = int(input("Enter the Caesar shift: "))
    decrypted_text = caesar_decrypt(ciphertext, shift)
else:
    print("Invalid algorithm choice!")

print("Decrypted text:", decrypted_text)
