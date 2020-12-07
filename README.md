	
## Overview	
	
This is an embedded system with temperature recording, internet of things (IoT) sensors and face recognition to enable organisations to move towards a ‘Contact-free’ entrance checking and workplace access easily.It mainly helps in avoiding contamination due to the finger-based biometric scanners.With the relaxation in the COVID-19 lockdown norms, this non-contact temperature assessment device will play a vital role on initial checking at entry points to identify people who may have elevated temperatures.It will detect the faces of employees along with their body temperature. If the face is not recognized properly, the employees can use the KELVIN Mobile App as an alternative.This app will have an unique QR code in it for all the employees.They can scan this QR in the camera and after scanning, the body temperature of the employee is measured with the help of sensors.It restricts the entry of the employees with high temperature with visual alerts as “Access Denied”. In this  way we can protect the organization and its employees from this pandemic.
The details of the employee such as user id,photo,temperature,check in time, check out time and shift along with their personal details are stored in the server.These details can be viewed in the Admin Portal(Web Application).In case if an employee tests positive for the virus,contact tracing can be done with the help of this admin portal.Those close contact people would then be asked to self-isolate, monitor themselves for symptoms and get tested if needed through an email.

## Database Design
The schema design for the entire system is given as a class diagram below. The Employee table contains all the personal details of the employees.User Id is the primary key in this table.The Reset Password table is designed for keeping track of the forgot password option in the mobile app.TokenId and UserId are the primary key and foreign key respectively.When an employee clicks the forgot password button,he/she will be prompted to enter their email address. A reset password link will be sent to  their email and a token will be generated to them.This will be valid for 15 minutes.After 15 minutes the reset password link becomes invalid as the token generated for the employee will be deleted after 15 minutes.The temperature table holds details like checkin,checkout,working hours,temperature,distance and shift.Working hours is calculated by differencing the check in and check out time.Distance column stores the distance between the temperature sensor and the employee.It is stored for error debugging.The database has a separate temperature table for each month.


![td](https://user-images.githubusercontent.com/59678585/101355608-d0061a00-38bc-11eb-941a-1ae9e364e604.png)

## Hardware Requirements:
 
 1)INFRARED TEMPERATURE SENSOR GY-906 MLX90614 SENSOR
 
 2)IR SENSOR
 
 3)LCD
 
 4)Camera
 
 5)RASPBERRY PI 
 
 6)ARDUINO

## Python Packages Required:

 1)Pyzbar
 
 2)Mysql Connector
 
 3)PyMLX90614
 
 4)OpenCV
 
 5)Rpi.GPIO
 
 6)RPLCD

### GY-906 MLX90614
After doing the comparative study,GY-906 MLX90614 sensor(FOV 80 degree)was chosen for this project.This sensor uses IR energy to detect the temperature of the object.It is manufactured by Melexis Microelectronics Integrated system.It has two devices embedded in it, one is the infrared thermopile detector (sensing unit) and the other is a signal conditioning DSP device (computational unit).
 The sensing unit in the sensor measures how much IR energy is emitted by a targeted object and the computational unit converts it into temperature value and outputs the data through I2C communication protocol. The sensor measures both the object temperature and ambient temperature to calibrate the object temperature value.

### IR SENSOR:
This sensor is used to calculate the presence of employee infront of the temperature sensor.If no object/person is detected the system will not record temperature.


![hardware](https://user-images.githubusercontent.com/59678585/101358114-6720a100-38c0-11eb-91de-986e77fd756e.JPG)

## Face Recognition

This system could recognise faces from the trained list of people. face_recognition library  which is built on top of dlib is used here.We use a  loop to create a list of all known face encodings.Here, we are using the compare_face() function to compare each known face to our unknown face. The result is a list of True/False values in the same order as the known faces we passed in. A True means the faces matched and a False means it wasn’t a match. The tolerance value lets us control how strict the matching is. To draw a rectangle around the recognized face in OpenCV, we need the top left and bottom right coordinates, and we use cv2.rectangle to draw it.

We have implemented face recognition using OpenCV and Python. We have used the following libraries

1) OpenCV: OpenCV is an image and video processing library and is used for image and video analysis, like facial detection, license plate reading, photo editing, advanced robotic vision, optical character recognition, and a whole lot more.

2) dlib: The dlib library contains our implementation of “deep metric learning” which is used to construct our face embeddings used for the actual recognition process. 

3) Face_recognition: The face_recognition  library wraps around dlib’s facial recognition functionality, and this library is super easy to work with and we will be using this in our code. 

## Working:
We use a  loop to create a list of all known face encodings. Then we have to open the camera to capture the person’s face. To identify the person, grab a single frame of video and convert the image from BGR color to RGB color which face_recognition uses. Then, find all the faces and face encodings in the frame of video, loop through each face in this frame of video and see if the face is a match for the known face(s). If a match was found in known_face_encodings, just use the first one and return the name. Or instead, use the known face with the smallest distance to the new face. If a match isn't found then return unknown.

## Mobile Application:

An mobile application is also developed for this system.This can be used as an alternative to face recognition.The application has an unique QR Code for each employee.They need to scan this QR in the camera and then record their temperature.

## Admin Portal

The Admin can monitor the overall screening process using this web portal. This person will have access to all the employee details and will also have the access to add a new employee to the database. If there is any change in the personal details like address or phone number or even in shift details  of the employee, the admin can update it with the help of this web application. The home page has recent screening entries. The navigation has different tabs like Home, Employee Details, History, Advanced Search and Add Employee. The add employee option allows admin to add a new employee details. The admin is able to filter the employees based on their email, shift,date, month, employee id and department. 









