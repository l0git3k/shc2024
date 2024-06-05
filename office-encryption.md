# [office-encryption](http://ctf.m0unt41n.ch/challenges/office-encryption) (`crypto`, `baby`)

# TL;DR

A trivial substitution encryption.

# Code

```python
from random import shuffle
from collections import Counter

# Function to generate a substitution cipher
def generate_substitution_cipher(text):
    alphabet = "abcdefghijklmnopqrstuvwxyz"  # Define the alphabet
    shuffled_alphabet = list(alphabet)  # Create a list of the alphabet
    shuffle(shuffled_alphabet)  # Shuffle the list to create a substitution cipher
    
    # Create a mapping of original to substituted characters
    cipher_map = {
        original: substituted
        for original, substituted in zip(alphabet, shuffled_alphabet)
    }

    encrypted_text = ""  # Initialize the encrypted text
    for char in text:
        if char.lower() in cipher_map:  # Check if the character is in the cipher map
            encrypted_char = cipher_map[char.lower()]  # Get the substituted character
            if char.isupper():
                encrypted_char = encrypted_char.upper()  # Maintain the case of the original character
            encrypted_text += encrypted_char  # Add the substituted character to the encrypted text
        else:
            encrypted_text += char  # If not in the cipher map, add the original character

    return encrypted_text, cipher_map  # Return the encrypted text and the cipher map

# Example text to be encrypted
text = "shc2024{fake_flag}"

# Generate the encrypted text and cipher map
encrypted_text, cipher_map = generate_substitution_cipher(text)

# Print the encrypted text and cipher map
print(encrypted_text, cipher_map)
```

# Decryption

```python
# Copied from the cipher_map.txt
cipher_map = {'a': 'k', 'b': 'n', 'c': 'o', 'd': 'r', 'e': 'v', 'f': 'q', 'g': 'i', 'h': 'w', 'i': 'x', 'j': 'd', 'k': 'h', 'l': 'm', 'm': 'l', 'n': 'y', 'o': 'u', 'p': 'b', 'q': 'f', 'r': 'p', 's': 's', 't': 'z', 'u': 't', 'v': 'a', 'w': 'c', 'x': 'j', 'y': 'g', 'z': 'e'}

# Encrypted flag to be decrypted
encrypted_flag = 'swo2024{jytmm_ruvs_opgbzu_mum}'

# Decrypt the encrypted flag using the cipher map
for c in encrypted_flag:
  found = False
  for m in cipher_map:
    if cipher_map[m] == c:
      print(m, end="")  # Print the original character if found in the cipher map
      found = True
  if not found:
    print(c, end="")  # Print the character as is if not found in the cipher map
print("")
```

# The flag

```
shc2024{xnull_does_crypto_lol}
```

