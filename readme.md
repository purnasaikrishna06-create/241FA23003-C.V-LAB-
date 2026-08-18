

CODE:

import cv2<br>
import numpy as np
from matplotlib import pyplot as plt

#to show image
def show_comparison(original,blur3,blur5,blur7):
  plt.figure(figsize=(12,10))

  #original image
  plt.subplot(2,2,1)
  plt.imshow(original,cmap='gray')
  plt.title('Original')
  plt.axis('off')

  #3x3 kernal
  plt.subplot(2,2,2)
  plt.imshow(blur3,cmap='gray')
  plt.title('avg filter (3x3)(Blur3)')
  plt.axis('off')

  #5x5 kernal
  plt.subplot(2,2,3)
  plt.imshow(blur5,cmap='gray')
  plt.title('avg filter (5x5)(Blur5)')
  plt.axis('off')

  #7x7 kernal
  plt.subplot(2,2,4)
  plt.imshow(blur7,cmap='gray')
  plt.title('avg filter (7x7)(Blur7)')
  plt.axis('off')

  plt.tight_layout()
  plt.show()

img = cv2.imread('/content/IMG20241031162048.jpg', 0)
if img is None:
    print("Error: Image not found.")
else:
    karnal_30x30=np.ones((30,30),np.float32)/900
    karnal_50x50=np.ones((50,50),np.float32)/2500
    karnal_100x100=np.ones((100,100),np.float32)/10000
    blur_3=cv2.filter2D(img,-1,karnal_30x30)
    blur_5=cv2.filter2D(img,-1,karnal_50x50)
    blur_7=cv2.filter2D(img,-1,karnal_100x100)
    show_comparison(img,blur_3,blur_5,blur_7)

OUTPUT:

<img width="1189" height="959" alt="image" src="https://github.com/user-attachments/assets/8e0c32d5-a632-4757-afb8-044a23e54c0c" />

