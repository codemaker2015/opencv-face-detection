# Face Detection 
Face detection demo using opencv and haarcascade

[demo](demo.mp4)

### Installation

```
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

### Run

```
python face_detection.py
```

### Source code

```py
import cv2
import numpy as np
cap = cv2.VideoCapture(0)
face_cascade = cv2.CascadeClassifier('haarcascade_frontalface_default.xml')
while True:
    _, img = cap.read()
    img=cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
    faces = face_cascade.detectMultiScale(img, 1.1, 4)
    for (x, y, w, h) in faces:
        cv2.rectangle(img, (x, y), (x+w, y+h), (0, 0, 0), 2)
    cv2.imshow('img', img)
    k = cv2.waitKey(30) & 0xff
    if k==27:
        break
cap.release()
```