# Attendance_Management_System

## Problem:
During COVID, companies tried to find ways to reduce how much people have to touch things. To keep track of when employees come to the office, they either got a special ID card that they could tap to enter, or they wrote their names and signed a paper. Even though the ID cards worked well and lessened physical contact, they weren't very cost-effective for lots of employees working in warehouses all over the country.

## Proposed Solution:

We can generate a QR code on the user's phone with a 34-digit value, which can be scanned by the scanner to confirm that the user is physically present. This approach also resolves the issue of inaccurate geolocations. The format of the 34-digit value will include 6 digits of the employee code, 6 digits of latitude, 6 digits of longitude, and 16 digits of timestamp (e.g., '303146' + '26.8705' + '75.5510' + 'yyyy-MM-dd-HH:mm:ss.SS').

![alt text](https://github.com/supragyabajpai/Attendance_Management_System/blob/main/Pictures/QR_Scanner.jpg)

Stepwise Procedure:

Step 1 - Code a QR code generator with the above format into the app.
Step 2 - Place a QR scanner at the gate of the premises.
Step 3 - The employee will use the app to generate a QR code, which will remain active for the next two seconds.
Step 4 - The scanner will read the code containing all the real-time data of the employee and transfer it to its database. After cross-checking the data, we can signal the employee to proceed.

PROS:

We don’t need to generate new QR codes daily.
Relying on timestamps eliminates concerns about the employee's geolocation accuracy; we can work with slightly inaccurate coordinates.
QR codes can be provided through MMS for users without smartphones.
Cost-efficient compared to other technologies, such as geofencing.
A two-second time limit helps prevent forgery.
User-generated QR codes ensure attendance is marked only from the user's location.

CONS:

Requires regular maintenance.
Dependence on a real-time server for responding to actions may increase setup charges.
If someone other than the employee with the employee's phone scans the QR code, the employee will still be marked as present.


Future modifications:

Option 1:

We will generate a QR code on the user's phone with a timestamp. Upon scanning, if the timestamp value falls within the last few seconds, we will accept it, store all the employee details, and mark their attendance. After processing the details, we can signal them to enter.

Option 2:

Alternatively, we can instruct the user to take a daily picture of themselves and upload it to the app before scanning their QR code. We will generate a hash number for that image, upload it to the server, and then add the hash number to the QR code during generation. By comparing the hash number in the generated QR code with the one on the server, we can signal the user to enter when the values match. Additionally, we can use the uploaded image for facial recognition to verify the user's identity.
