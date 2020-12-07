	
## Overview	
	
This is an embedded system with temperature recording, internet of things (IoT) sensors and face recognition to enable organisations to move towards a ‘Contact-free’ entrance checking and workplace access easily.It mainly helps in avoiding contamination due to the finger-based biometric scanners.With the relaxation in the COVID-19 lockdown norms, this non-contact temperature assessment device will play a vital role on initial checking at entry points to identify people who may have elevated temperatures.It will detect the faces of employees along with their body temperature. If the face is not recognized properly, the employees can use the KELVIN Mobile App as an alternative.This app will have an unique QR code in it for all the employees.They can scan this QR in the camera and after scanning, the body temperature of the employee is measured with the help of sensors.It restricts the entry of the employees with high temperature with visual alerts as “Access Denied”. In this  way we can protect the organization and its employees from this pandemic.
The details of the employee such as user id,photo,temperature,check in time, check out time and shift along with their personal details are stored in the server.These details can be viewed in the Admin Portal(Web Application).In case if an employee tests positive for the virus,contact tracing can be done with the help of this admin portal.Those close contact people would then be asked to self-isolate, monitor themselves for symptoms and get tested if needed through an email.

## Database Design
The schema design for the entire system is given as a class diagram below. The Employee table contains all the personal details of the employees.User Id is the primary key in this table.The Reset Password table is designed for keeping track of the forgot password option in the mobile app.TokenId and UserId are the primary key and foreign key respectively.When an employee clicks the forgot password button,he/she will be prompted to enter their email address. A reset password link will be sent to  their email and a token will be generated to them.This will be valid for 15 minutes.After 15 minutes the reset password link becomes invalid as the token generated for the employee will be deleted after 15 minutes.The temperature table holds details like checkin,checkout,working hours,temperature,distance and shift.Working hours is calculated by differencing the check in and check out time.Distance column stores the distance between the temperature sensor and the employee.It is stored for error debugging.The database has a separate temperature table for each month.


![td](https://user-images.githubusercontent.com/59678585/101355608-d0061a00-38bc-11eb-941a-1ae9e364e604.png)

## Hardware

Sensors and other hardwares:
1)INFRARED TEMPERATURE SENSOR GY-906 MLX90614 SENSOR
2)IR SENSOR
3)LCD
4)Camera

Microcontroller:
1)RASPBERRY PI
2)ARDUINO

Python Packages:
1)Pyzbar
2)Mysql Connector
3)PyMLX90614
4)OpenCV
5)Rpi.GPIO
6)RPLCD

## GY-906 MLX90614
After doing the comparative study,GY-906 MLX90614 sensor(FOV 80 degree)was chosen for this project.This sensor uses IR energy to detect the temperature of the object.It is manufactured by Melexis Microelectronics Integrated system.It has two devices embedded in it, one is the infrared thermopile detector (sensing unit) and the other is a signal conditioning DSP device (computational unit).
 The sensing unit in the sensor measures how much IR energy is emitted by a targeted object and the computational unit converts it into temperature value and outputs the data through I2C communication protocol. The sensor measures both the object temperature and ambient temperature to calibrate the object temperature value.

## IR SENSOR:
This sensor is used to calculate the presence of employee infront of the temperature sensor.If no object/person is detected the system will not record temperature.




