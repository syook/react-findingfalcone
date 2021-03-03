# react-findingfalcone

## Problem Statement

Our problem is set in the planet of Lengaburu, in the distant galaxy of Tara B. After the recent war with neighbouring planet Falicornia, King Shan has exiled the Queen of Falicornia for 15 years. Queen Al Falcone is now in hiding. But if King Shan can find her before the years are up, she will be exiled for another 15 years.

King Shan has received intelligence that Al Falcone is in hiding in one of these 6 planets - Donlon, Enchai, Jebing, Sapir, Lerbin & Pingasor. However he has limited resources at his disposal & can send his army to only 4 of these planets. Your coding problem is to help King Shan find Al Falcone.

You need to build a react app through which King Shan can 
- select 4 planets to search (out of the total 6)
- select which space vehicles to send to each of these planets
- see how much time it will take for the vehicles to reach their targets
- show final result of success or failure for finding Al Falcone

## Planets (Potential Hideouts)
There are 6 potential hideouts and all are at varying distances from Lengaburu. 

The details of the planets can be fetched using the following API

```
URL: https://findfalcone.herokuapp.com/planets
Method: GET
Response: [{"name":"Donlon","distance":100},{"name":"Enchai","distance":200},{"name":"Jebing","distance":300},{"name":"Sapir","distance":400},{"name":"Lerbin","distance":500},{"name":"Pingasor","distance":600}]
```

## Space Vehicles (Available Vehicles)
There are 4 types of vehicles. The number of available vehicles for each vehicle type vary (eg:- there are 2 space pods but only 1 space rocket). All have different ranges (maximum distance it can travel). If the range for a vehicle is lesser than the distance to the planet, it cannot be chosen for going to that planet. All have different speed. Based on the distance to the planet and the speed of the vehicle, time taken for the search can be calculated.

The details of the vehicles can be fetched using the following API

```
URL: https://findfalcone.herokuapp.com/vehicles
Method: GET
Response: [{"name":"Space pod","total_no":2,"max_distance":200,"speed":2},{"name":"Space rocket","total_no":1,"max_distance":300,"speed":4},{"name":"Space shuttle","total_no":1,"max_distance":400,"speed":5},{"name":"Space ship","total_no":2,"max_distance":600,"speed":10}]
```

## Finding Falcone
Once the user has made his selection of 4 planets and the appropriate vehicles to be used to go to these planets, the details of the user's selection need to passed on to the following API to determine success or failure of finding Al Falcone

```
Step 1: Fetch authenticaton token
URL: https://findfalcone.herokuapp.com/token
Method: POST
Body: empty
Headers:
Accept: application/json
Response: { "token": "PAPngVMMuFHwvnNcXyDUsQSfmdZytOwC" }

Step 2: Find Falcone using the authentication token fetched in step 1 along with the user's selection details
URL: https://findfalcone.herokuapp.com/find 
Method: POST
Body: The request body is a json object which consists of a token, planet_names and vehicle_names. Value of the token is obtained from the previous API call (/token). planet_names is a JSON Array which consists of the planet names you selected from the UI. vehicle _names is also a JSON Array which consists of the vehicle names you have selected from the UI in the same sequence as the planets they need to travel to
{
     "token": "PAPngVMMuFHwvnNcXyDUsQSfmdZytOwC",
     "planet_names": ["Donlon","Enchai","Jebing","Sapir"],
     "vehicle_names":["Space pod","Space rocket","Space shuttle","Space ship"]
}
Headers:
Accept: application/json
Content-type: application/json
Response: { "planet_name": "Donlon", "status": "success" }
```

## How will the assignment be graded?
- Functionality: Is the web-app functional?
- Code Quality: Code Readability and structuring.
- Exception Handling: No crashes.
- Git Commit practices: Manage your code in github and make frequent commits.

## Submission
Share the github repository and hosted webapp link. If you have any other doubts, get in touch with us
