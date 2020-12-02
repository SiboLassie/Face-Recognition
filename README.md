# Realtime-Face-Recognition
a Python Project to recognize multi faces on video or live camera and show the names using OpenCV and haar-cascade-frontal-face.

# *To identify a particular person's face, the system must be trained first

#How to Run
	** Very important!
	First go to trainer folder and extract trainer.Zip 
	
	Run face_dataset.py and let the system to train

	Make sure to modify face_id parameter, so new profile will created.

	Once the training is complete, profile pictures will be created in the dataset folder

	Then run training.py to load all profiles of different faces.

	In face_recognition.py for each profile, create an id test condition to display the real-time Id tag on the face

	Finally Run face_recognition.py .


#Sample to get video from PiCam
	import the necessary packages
	from picamera.array import PiRGBArray
	from picamera import PiCamera
	import time
	import cv2
 
# initialize the camera and grab a reference to the raw camera capture
	camera = PiCamera()
	camera.resolution = (640, 480)
	camera.framerate = 32
	rawCapture = PiRGBArray(camera, size=(640, 480))
 
# allow the camera to warmup
	time.sleep(0.1)
 
# capture frames from the camera
	for frame in camera.capture_continuous(rawCapture, format="bgr", use_video_port=True):
	# grab the raw NumPy array representing the image, then initialize the timestamp
	# and occupied/unoccupied text
	image = frame.array
 
	# show the frame
	cv2.imshow("Frame", image)
	key = cv2.waitKey(1) & 0xFF
 
	# clear the stream in preparation for the next frame
	rawCapture.truncate(0)
 
	# if the `q` key was pressed, break from the loop
	if key == ord("q"):
		break
