# HAR
Human Activity Recognition through CNN-LSTM network with a C/S architecture

This is my undergraduate graduation design, which is a system which uses the sensors's data from user's android phone to predict what kind of activity the user is taking. In this project there are six kinds of activities: walking, standing, walking upstairs, walking downstairs, sitting and lying down.

# File Organization
The Android folder includes a .apk file for android installation and the Android Studio project of the Client part of this system, while the Python file contains the server part of this system and some ohter files

The har.sql file is the mysql file for the system history, which is composed of the history of activity recognitions of this system.

# CNN-LSTM network
To be continue...

# System Design
To transform data between client and server, a tcp connection will be established between them once there is a request from the client. Th CNN-LSTM network has been trained offline. 
## Client
This is an Android application, whose functions are as followings:
1. Adding new data(data with label)
2. Predicting the activity of a period of data
3. Continuously predicting
4. Recognition result feedback
### Adding new data
This part is designed for adding more trainning data for the network. After recording a period of data, user needs to choose the activity he/she was taking, then the data will be submitted and transmit to the server. This part of function is mainly used during the starting period of this project to collect enough data for network trainning. 
### Predicting the activity of a period of data
Collect a period of data and use the pre-trained model to predict it, and then result will be returned to the client
### Continuously predicting
Continuously collecting sensors' data and get a result every 2.7s(...). 
### Recognition result feedback
Choose a wrongly-predicted record from "history" and submit the correct activity type. The server will use the right data to update the model.
## Server
Maintain a tcp connection and the CNN-LSTM network
