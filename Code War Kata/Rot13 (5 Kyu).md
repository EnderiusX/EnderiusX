#Taken from Code Wars Kata [(5 Kyu)](https://www.codewars.com/kata/530e15517bc88ac656000716/train/python):
ROT13 is a simple letter substitution cipher that replaces a letter with the letter 13 letters after it in the alphabet. ROT13 is an example of the Caesar cipher.

Create a function that takes a string and returns the string ciphered with Rot13. If there are numbers or special characters included in the string, they should be returned as they are. Only letters from the latin/english alphabet should be shifted, like in the original Rot13 "implementation".

Please note that using encode is considered cheating.

Ciphers, Fundamentals
```
import string


def rot13(message):
#     print(dir(string))
    abcd = string.ascii_lowercase # Obtains a string of lowercase letters from a-z.
    abcd_dict = dict([(ltr, idx) for idx, ltr in enumerate(abcd)]) # Creates a dictionary that is indexed from 0 - 25 for all 26 lowercase letters in the alphabet and sets the key:value pair as letter:index i.e. "b":1.
#     print(abcd_dict)
    encrypted_lst = [] # Empty list to store individually encrypted string.
    upper = False # Stores a variable to check if the letter is an uppercase letter.
    for letter in message:
        if letter not in abcd: # Checks if the letter is anything but a lowercase letter
            if letter.lower() not in abcd:
                encrypted_lst.append(letter)
                continue
            upper = True
            letter = letter.lower()
        rot13_idx = abcd_dict[letter] + 13
        if rot13_idx > 25: # Checks if the index is greater than 25 and subtracts from the value to ensure it remains in range.
            rot13_idx -= 26
        rot13_ltr = abcd[rot13_idx]
        if upper == True: # Checks if the "upper" variable is true and sets the encrypted letter as such.
            rot13_ltr = rot13_ltr.upper()
            upper = False
        encrypted_lst.append(rot13_ltr)
    return "".join(encrypted_lst)
```
