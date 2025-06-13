Sum O Primes

Challenge:
We have so much faith in RSA we give you not just the product of the primes, but their sum as well. 
They gave us 2 files, gen.py and output.txt

I first read up abt RSA. In a typical RSA we get only n, but here they game us p*q and p+q. They also gave public exponent e which is 65537 (in most of the cases including this one).
x = p + q
n = p * q

Procedure:
First i converted hex to integers
Then since they gave sum and products i used quadratic formula, and found p and q.(wrote python code for this)
Next I computed Euler’s totient, and decryption exponent..they gave us the encryption exponent (65537). I now have the private key.
After this I decrypted the ciphertext using python
Now i converted the decrypted message to a flag using:
from Crypto.Util.number import long_to_bytes
flag = long_to_bytes(m).decode()

Ans
picoCTF{pl33z_n0_g1v3_c0ngru3nc3_0f_5qu4r35_92fe3557}

Vault door 1
Java program checks individual characters of the password.pretty easy
 I reconstructed the password character-by-character using the logic from the charAt() comparisons.
Flag: picoCTF{d35cr4mbl3_tH3_cH4r4cT3r5_f6daf4}


Vault Door 3
Password is scrambled through index-based reordering.
Just reversed the index manipulation from the loop logic to recover the original order of the characters.
Flag: picoCTF{jU5t_a_s1mpl3_an4gr4m_4_u_79958f}


Vault Door 4
For this question my approach was to convert each byte to its ASCII equivalent to form the password.
Flag: picoCTF{jU5t_4_bUnCh_0f_bYt3s_8f4a6cbf3b}


Vault Door 5
URL-encoded and then base64 encoded.
Base64 decoded the target string, then URL-decoded the result to retrieve the password.
Flag: picoCTF{c0nv3rt1ng_fr0m_ba5e_64_0b957c4f}


Vault Door 6
In the question, the password is XORed with 0x55 and matched against a byte array.
Reversed the XOR operation to recover the original password bytes.
Flag: picoCTF{n0t_mUcH_h4rD3r_tH4n_x0r_948b888}


Vault Door 7
Each group of 4 characters is packed into a 32-bit integer, converted each 32-bit integer back into 4 ASCII characters.
Flag: picoCTF{A_b1t_0f_b1t_sh1fTiNg_07990cd3b6}


Forensics Challenge
File named Flag.pdf that wouldn’t open as a normal PDF.
Ran file Flag.pdf, output revealed it’s a shell archive script.
Opened in a text editor…i then identified it was a shar archive with uuencoded content.
Extracted using sh Flag.pdf, which gave a file named flag.
Used uudecode or inspected the decoded content directly to retrieve the flag.


Flag: picoCTF{f1l3_5p3c1m3n_4n4ly51s_f75aebcf}
Mini RSA
Question: RSA challenge with small exponent e = 3 and slightly padded message M.
By solving this i learnt about RSA, Regex, 


My approach:
Understood that M^3 slightly exceeded N.
Used integer cube root estimation to recover M.
Converted integer M to bytes.
Searched decoded bytes for flag format using regex.
Used Python and sympy.integer_nthroot() for cube root logic.
Converted final ans (which was in integers) to its byte representation.
Flag: picoCTF{smal1_expo_attack_successful} (example)




