# face_recognition
# 1.	INTRODUCTION
                      #       1.1. Introduction
Attendance is mandatory for any institution or organisation based on the attendance the organisation or institution give upraise for employees or for students in colleges it is mandatory of their presence to give promote with minimal attendance for the next academic year.
There are traditional ways of taking the attendance like
1.	Teacher/Supervisor physical takes the presence of students/employee and mark present or absent.

2.	Signature for every hour or morning and evening sessions by student /employee

3.	Finger print or Biometric recording the attendance

All the above may have chance of not getting the accurate result.  In this project developing the automatic attendance using the face detection using python.
1.2. Proposed method
Using the face recognition module we develop the project using python programming language. The following libraries are used in the project development
Face recognition , pandas , Opencv ,PIL, pygames ,datetime, sys ,os.
Developing of the face recognition can be done in many ways like training the machine of various images and using the deep learning concept we can do.
Here we have done in face recognition library which pretrained module here no need give have any trained images, but it is easy to implement but it takes time to detect the image bit slow in normal CPU. It is fast in the GPU.

                             # 1.3. Objectives

To overcome the above problems
1.	Teacher/Supervisor may miss the attendance due to miscommunication
2.	Signature for every hour or every session it is difficult
3.	Fingerprint or Biometric sometimes gives us error finger prints may erase or wiped off.
        are not getting the accurate because 
Due to these reasons we updated to face recognition attendance.


                            # 1.4. Literature Survey
 There are the other methods where like deep learning concepts where we need to train the dataset which requires the much amount space. There are the other methods using open-cv and tensor-flow , harrcasecade but they required the dataset and we need to train the data set.
                  Table 1.1 Different methods for face detection 
Methods	Acurracy	Dataset training	Fasteness
Face_recognition	97.2	No	>60 sec
OpenCv	96.2	Yes	7 sec
Harrcasecade	98.6	Yes	5 sec
TensorFlow	98.4	Yes	5 sec
              




                              # 2. IMPLEMENTATION


2.1 Methodology
Design
1. Reference Data load Module 
2. Face Capture and Store temporarily 
3. Face Recognition 
4. Attendance Record Module 
5. Display Attendance Module 
6. Announce Attendance Module





Flow Chart
![Screenshot (216)](https://user-images.githubusercontent.com/73389805/178927022-75e55c2e-dd99-4896-a3e9-c55a71553ec9.png)
              Fig 2.1. Working model of attendance management




![Screenshot (233)](https://user-images.githubusercontent.com/73389805/178927029-c00a2be2-0a8a-4064-942f-168334da9b2c.png)

                      Table 2.1 Importing various Libraries
                      
Sl No	Library / Module Name	Usage
1	import face_recognition	The key module for face recognition
2	import cv2	Computer Vision library cv2 is used to capture the image in the camera
3	from PIL import Image, ImageDraw, ImageFont	PIL Module is for drawing the name of the person on the image captured. This is required to display after recognizing the image
4	import sys	In using the encodings function, we use try-else clause. In the else calyse, we want to exist system. Sys library is used here
5	import pandas as pd	In loading the datafile and converting into Python list, we use
6	import datetime	For recording the attendance, we use the date stamp.
7	import pygame	This module is used to play audio and announce the attendance
              

1. Reference Data Load Module
Here top10rich.csv file created and columns we have
Employee Identification Number 
Employee's First Name
The employee's photo is stored at this URL. Every employee has a photo, and the location of the photo file is saved in this field as a string.
The audio file announcing the name is preserved at this URL. We want to announce the employee's name when attendance is taken.
The audio of the employee's name being announced is saved.


Code 
![Web capture_1-1-2022_191753_localhost](https://user-images.githubusercontent.com/73389805/178927053-1d98638e-a909-4b84-a862-1fa0fd618643.jpeg)
 
                    Fig 2.2 Loading the data from excel and encoding

2. Face Capture Module 
When the employee stands in front of the camera, the image of his or her face is captured. We'd want to collect the image frames continuously for 5 frames and then choose the middle one (3rd frame) because the image capture happens in real time.
They saved as employee [i], for i=1,2 …..9 .png
Load employee3.png as grp_photo
And proceed for the face recognition

Code

![Web capture_1-1-2022_191725_localhost](https://user-images.githubusercontent.com/73389805/178927050-a3c60e70-8bb1-4a41-9efb-471252daa69f.jpeg)
 
                           Fig 2.3 Capturing the photos
3. Face Recognition Module 
Face encodings of all the images emp_code [] and camera captured image encodings we are compare it and if the comparing where match we get the desired output. 
Whole thing we placed in the try and catch block.
The compare will return the Boolean value that is True or False and found value is True the found value will be True 
Code

  ![Web capture_1-1-2022_191654_localhost](https://user-images.githubusercontent.com/73389805/178927048-357aa142-c5f0-4298-84ce-1e5a1c473a77.jpeg)
 
		           Fig 2.4. Comparing the photos with registered images

4.Attendance Record (in a Data file) Module:
If the index is equal to -1, it means we have not recognized the face. So, in this case attendance is not recorded in the data file. If it is not -1 the string with employee no and employee name and date and time will be printed in the data text file.
Code
![Web capture_1-1-2022_191630_localhost](https://user-images.githubusercontent.com/73389805/178927044-e5a1f390-9e61-47a9-b35d-4f67034d016c.jpeg)

 
                        Fig 2.5 Noting the attendance

5. Display Attendance Module:
Converting the capture image to array and find the face location and drawing the bounding box and displaying the text over the text on the image and displaying the image if emp_index = -1 it draw the text Face Not Recognition and if not it display the Employee name on the image

Code
![Web capture_1-1-2022_19169_localhost](https://user-images.githubusercontent.com/73389805/178927038-8be2f5f0-95e2-41d5-a0fe-fc469845c688.jpeg)

 
                        Fig 2.6 Drawing bounding boxes
6: Announcing (Audio) the Attendance
Using the pygame library we can play the audio . Firstly , the audio of failure face recognition and success recorded and it is played using the pygame .If emp_index value is -1 load and play the failure audio from the location. If emp_index is not -1 that means it some value and it load and play the success audio.
Code

![Web capture_1-1-2022_191529_localhost](https://user-images.githubusercontent.com/73389805/178927042-0f9f0bdf-be22-45d9-b02c-b45e960aa6b6.jpeg)
 
			                Fig 2.7 announcing the attendance


Result and Analysis:
 ![Screenshot (234)](https://user-images.githubusercontent.com/73389805/178927033-26c9e399-01dd-43c6-bb16-fd7cdc167d79.png)
 
                           Fig 2.8 The student attendance recorded 

It is gives the accurate result. It compare the csv file and captured image if the image is in that it display the name an image. If it is not in the csv file it show the face has not recognized.

 The output here observe that the recognized face is matching with the csv file image and displayed the employee name and there captured date and time.
 
 ![Web capture_1-1-2022_195240_localhost](https://user-images.githubusercontent.com/73389805/178927056-198861d0-e3ce-4e83-88ab-9be5abae89a6.jpeg)
 
                   Fig 2.9 Showing location of image matches with registered data

The text file attendance will store the data that is camera captured of the employee with data and time.


                                # CONCLUSIONS
 Conclusion
By this project we have developed the Automatic attendance using face recognition and learned the different python libraries which are used to develop this project mainly we learnt
PIL image Drawing on the image and bounding box on the image from the face recognition library. Using face location ,face encoding ,face compare method and their parameter used.
Pygame is used to paly the audio and pandas we used to extract the data from the csv file and later we converted into the list. Cv2 is used to capture the image from the camera.
Finally we have developed the project putting together.
                          # Future Scope of Work
We can further develop this module for the multiple faces and to record in the excel file and implement them. The entire project can be run on the GPU will give the better result and fast execution We have ran this project on the CPU. So, It is bit time consuming. There are the other methods where like deep learning concepts where we need to train the dataset which requires the much amount space. There are the other methods using open-cv and tensor-flow , harrcasecade but they required the dataset and we need to train the data set. They are efficient and accurate.


# Reference:
>	Facial Recognition and Attendance System using dlib and face_recognition libraries
>	https://pypi.org/project/face-recognition/
>	face_recognition: Face recognition library [Electronic Resource] – Access mode: https://face-recognition.readthedocs.io/en/latest/readme.htm

