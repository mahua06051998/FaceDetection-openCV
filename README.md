import cv2
video = cv2.VideoCapture(0)
face_cascade = cv2.CascadeClassifier("haarcascade_frontalface_default.xml")
while True:
    check,frames =video.read()
    gray = cv2.cvtColor(frames,cv2.COLOR_BGR2GRAY)
    faces = face_cascade.detectMultiScale(gray,1.3,5)
    for x,y,w,h in faces:
        frames  = cv2.rectangle(frames,(x,y),(x+w,y+h),(0,255,0),3)
        cv2.resize(frames,(500,1000))
        cv2.imshow("faceDetection",frames)
        k = cv2.waitKey(1)
        if k == ord('q'):
            break
        
video.release()
cv2.destroyAllWindows()
