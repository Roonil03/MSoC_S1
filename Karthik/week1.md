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

