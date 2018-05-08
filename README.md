# Location Based Quiz

The project corresponds to a Location Based Quiz that is divided in two apps, a mobile app that shows questions to the user related with his/her location (called Quiz app) and a web application where these questions are defined (called Question setting app) and saved into a database. Additionally, both parts are served by an HTTP node.js server.

Both apps use a three tiers architecture where the client-side code is separated from the server-side code which connects to a PostGreSQL database.

Both are PhoneGap apps and their front–ends were designed based on the Google’s Material Design Lite, specifically on the [dashboard template](https://getmdl.io/templates/index.html). The web map used is obtained from the Leaflet API and using MapBox as basemap tiles. 

All the code to develop these two parts and the server are available on three separated repositories on this GitHub account:
* [Quiz App](https://github.com/ucesova/Quiz_App)
* [Question setting app](https://github.com/ucesova/question_setting_app)
* [Server](https://github.com/ucesova/Server) 

## 1.	Mobile quiz app: 
The quiz app is designed to track the movement of the user, shows it on a map and compares its location with the location of different points of interest (POI) obtained from a postGres database, which have a question related to each of them. When the user is near to a POI, the app shows an alert asking him to answer the related question. This question is displayed below the map and shows multiple choices. After the user answers the question, his answer is saved into the database and the correct answer is showed to him. For this project, and as a possible deployment example, the quiz app was called “ArchiQuiz” which asks about the architectural style of different buildings around London.

To do this, the app uses the HTML 5 in-built location services that allow the app to find the position of the device and tracks its movements. 

The distance between the device location and the POIs is calculated using the Haversine formula and [Rob Gravelle’s code](https://www.htmlgoodies.com/beyond/javascript/calculate-the-distance-between-two-points-in-your-web-apps.html)

The app was successfully tested in different locations around London on a Moto G (3rd generation) phone with Android version 6.0.1 and system version 24.221.17.osprey_retgb.retgb.en.GB retgb.

### Technical Requirements

* Android 5 or newer.
* To use the quiz app, the device needs to be connected to the UCL network so a UCL user and password is needed. To access it remotely from a mobile device you may use CISCO VPN App. 

### How to install it in your phone: 
* Make sure that you have a file manager app and a QR code scanner on your mobile phone.
* Go to the following [link](https://chart.googleapis.com/chart?chs=116x116&cht=qr&chl=https://build.phonegap.com/apps/3151570/install/hWaZttdRGhwUJYRmNMRC&chld=L|1&choe=UTF-8) and scan the QR code that it contains.
* Once downloaded on your phone, open the file and the press “install”.

### User guide
The user guide is accessible from the app clicking on the menu on “user guide”.

### APIs used
* Leaflet v.1.1.0 for the web map. 
This was used in the [index.html](https://github.com/ucesova/Quiz_App/blob/master/ucesova/www/index.html) file.
* Mapbox v.4 for the basemap tiles.
This was used in the [index.html](https://github.com/ucesova/Quiz_App/blob/master/ucesova/www/index.html) file.
* Material Design Lite v. 1.3.0, specifically its dashboard template
This was used in the [index.html](https://github.com/ucesova/Quiz_App/blob/master/ucesova/www/index.html) and in the [quizuserguide.html](https://github.com/ucesova/Quiz_App/blob/master/ucesova/www/quizuserguide.html) files.


## 2.	Question setting app: 

The question setting app is designed to allow the administrator of a Quiz App instance to define the location of the POIs and the questions related to them, their choices and correct choice, and save all these information into the database.

All these aspects should be defined by the administrator filling a simple form. Through the Leaflet API, the application offers the user a function to identify the coordinates of the point where the user clicks on the map that can then be used by him to fill the coordinate’s part of the form. 

Before using the question setting app, is necessary to run the PhoneGap server and the node.js server called httpServer.js.

The application was tested in Google Chrome (version 52.0.2743.116), Mozilla Firefox (version 45.2.0), Internet Explorer (version 11.0.9600.18920) and Microsoft Edge (version 41.16299.371.0), having the expected outputs in all of them.

### Technical Requirements

* To acces the question setting app, the device needs to be connected to the UCL network so a UCL user and password is needed. To access it remotely from a mobile device you may use CISCO VPN App. 

### User guide
The user guide is accessible from the app clicking on the menu on “user guide”.

### APIs used
* Leaflet v.1.1.0 for the web map. 
Used in the [index.html](https://github.com/ucesova/Quiz_App/blob/master/ucesova/www/index.html) file.
* Mapbox v.4 for the basemap tiles. 
Used in the [index.html](https://github.com/ucesova/Quiz_App/blob/master/ucesova/www/index.html) file.
* Material Design Lite v. 1.3.0, specifically its dashboard template. 
Used in the [index.html](https://github.com/ucesova/Quiz_App/blob/master/ucesova/www/index.html) and in the [quizuserguide.html](https://github.com/ucesova/Quiz_App/blob/master/ucesova/www/quizuserguide.html) files.


## 3.	Server: 

The server-side code of both, the Quiz app and the Question setting app is developed on the [Node.js](https://nodejs.org/en/) environment using the express API. For both apps, the server-side code was stored in the same Node.js file, called [httpServer.js](https://github.com/ucesova/Server/blob/master/httpServer.js) which, true to its name, is an HTTP server to ensure it works in all browsers and with PhoneGap.

This server allows the question setting app to connect to the database over the internet to store the POIs’ questions, and the Quiz app to get the questions from the database, store the users’ answers and show him the correct one. 

Note that the server should be initialized before running any of the apps.
This server allows cross-origin request (i.e. making data requests from this server via another server, in this case the PhoneGap server)

### How to run it: 
* typing node httpServer.js at the therminal, in the location where this file is saved


### APIs used
* Express API (node.js)


## Built With

* [PhoneGap](https://phonegap.com/) version 7.1.1 - Mobile apps developer
* [Bitvise SSH Client](https://www.bitvise.com/ssh-client) version 6.31 - SSH file transfer, terminal and tunneling

## Acknowledgments

* The majority of the code is based on the lectures and practicals from the UCL module "Web and Mobile GIS" 2018, by Claire Ellul
* This README was based on [PurpleBooth's template](https://gist.github.com/PurpleBooth/109311bb0361f32d87a2#getting-started)
