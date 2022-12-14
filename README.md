# Final-project
import easyocr
import matplotlib.pyplot as plt
import cv2
import numpy as np

reader = easyocr.Reader(['en'], gpu=True)
vid = cv2.VideoCapture('object2.jpg')

skip_frame = True
while True:
    ret, img = vid.read()

    gray = cv2.cvtColor(img, cv2.COLOR_RGB2GRAY)
    result = reader.readtext(gray)

    text = ''    for res in result:
        text += res[1]

    cv2.putText(img, text, (50, 70), cv2.FONT_HERSHEY_SIMPLEX, 1, (0, 0, 255), 2)

    plt.imshow(img)
    plt.show()

    print(text)
