# Crpytography

## pixelated

I have these 2 images, can you make a flag out of them? scrambled1.png scrambled2.png

### Script

''' picoCTF-cryptography-pixelated '''

import numpy as np
from PIL import Image

#opening images
img1=Image.open("scrambled1.png")
img2=Image.open("scrambled2.png")

np1=np.array(img1)
np2=np.array(img2)

result=np1+np2
Image.fromarray(result).save("result.png")

## Flag

> picoCTF{1b867c3e}