
```python
import cv2
```

# read and display images

```python
img = cv2.imread("Resources/image.png")  
cv2.imshow("output", img)  
cv2.waitKey(0)
```

---

# read and display videos

```python
capture = cv2.VideoCapture("Resources/video.mp4")  
while True:  
    success, img = capture.read()  
    cv2.imshow("video",img)  
    if cv2.waitKey(1) & 0xFF ==ord('q'):  
        break
```


---

# read and display webcam

```python
capture = cv2.VideoCapture(1)  
capture.set(3, 640)  # id=3 -> width property  
capture.set(4, 480)  # id=3 -> height property  
capture.set(10, 100)  # id=10 -> brightness  
  
while True:  
    success, img = capture.read()  
    cv2.imshow("video", img)  
    if cv2.waitKey(1) & 0xFF == ord('q'):  
        break
```


---

# convert to gray scale
*convention in opencv is not RGB but BGR*

```python
imgGray = cv2.cvtColor(img, cv2.COLOR_GBR2GRAY)
```

---

# blur image

```python
imgBlur = cv2.GaussianBlur(imgGray, (7,7), 0)
```

---

# Edge Detection

## Canny Edge Detector

```python
threshold1 = 100
threshold2 = 100
imgCanny = cv2.Canny(img, threshold1, threshold2)
```

## creating a kernel
*this requires the numpy library which handles mathematical functions in python*

```python
kernel = np.ones((5, 5), np.uint8)
```

## dilation and eroding
*increase or decrease the thickness of our edges so they connect and form straight lines*

```python
kernel = np.ones((5, 5), np.uint8)
imgDilation = cv2.dilate(imgCanny, kernel, iterations=1)
imgErode = cv2.erode(imgCanny, kernel, iterations=1)
```


---

# image size

```python
print(img.shape)
```

## resize images

```python

```